# Domain: Automation and Optimization 

## Topic: Cloudformation 

### Task: Create EC2 Instance 

Create a stack using Cloudformation template. The stack should contain the following resources: 

- EC2 instance with httpd server installed 
- Security group with SSH traffic allowed only from your IP address
- Elastic IP attached to the instance 

Parameters: 
- SSH key pair (must be the name of existing keypair) 
- Instance type (with allowed values t2.micro, t2.nano, t3.micro, t2.nano) 
- AMI Id 

Output exported: 
- InstanceId 
- Elastic IP associated with the instance 
- Website URL in form of http://<elastic ip>
 
Create a change set with a new rule in security group allowing 80 port from anywhere. Apply the change set, check if webserver works. 

## Solution

### Creating an EC2 instance using Cloudformation template
1) Open EC2 web console. Select N.Virginia region (us-east-1).
2) On the left under "Network & Security" section click on "Key Pairs". Click "Create key pair".
3) Set the name, for example "LabKeyPair". Choose the necessary format (ppk is used in Windows with PuTTY, pem is usually used in *nix systems). 
4) Click "Create key pair" button and save the file.
5) Open Cloudformation console. Be sure you're in the same region as in step 1). 
6) From the left menu choose "Stacks" -> "Create stack"
7) Select "Template is ready", "Upload a template file" and Choose the file "08-01.yml" from this repo, click "Next"
8) Set stack name like "lab08-01". Choose KeyPair created above. Set your external IP (you can get it, for example, by https://www.whatsimyip.com) in format x.x.x.x/32 . Choose default VPC (it should have 172.31.0.0/16 address range). Choose any of default public subnets (it should have 172.31.x.0/24 or /20 address range). Click "Next".

**Note:** If you're using other region, then ImageId will be different. To find the appropriate AMI ID, go to EC2 console, on the left side choose Instances->Instances and then click "Launch instances" button. Find "Amazon Linux 2 AMI" and copy its Ami ID (it should have the format ami-xxxxxxxxxxxxxxxxx). Click "Cancel and Exit"

9) On "Configure stack options" page leave the settings as is and click "Next"
10) On "Review" page click "Create stack" and wait until the stack is created. The status of the stack must be "CREATE_COMPLETE"
11) Go to "Outputs" tab and click on SiteURL link. The site shouldn't work. This is because the firewall isn't configured appropriately. In the next steps we're going to fix it.

### Creating a change set with firewall fix rules
1) Go to "Change sets" tab or click on "Stack actions" -> "Create change set for current stack"
2) Select "Replace current template", "Upload template file", click on "Choose file" and choose the file "08-01-changeset.yml". Click "Next"
3) On "Specify stack details" page leave all the parameters untouched and click "Next".
4) On "Configure stack options" page leave all the parametes untouched and click "Next".
5) Click "Create change set". Set the name like "lab08-1-changeset" and click "Create change set" button.
6) Wait until status of the change set changes to CREATE_COMPLETE. The changes that are going to be applied will be shown in the bottom in "Changes" section.
7) To apply current change set, click "Execute". Wait until stack changes its state to UPDATE_COMPLETE.
8) Go to "Outputs" tab and click on SiteURL link. The site should now work.

## Tearing down
1) Open Cloudformation in AWS web console. If necessary, change the region where the VPC stack was created.
2) From the left menu choose "Stacks" -> Choose the stack you created
3) On the right side click "Delete" button, confirm deletion by pressing "Delete stack" button
4) Wait until stack's deletion process. It may take up to several minutes.
