# Domain: Provisioning services

## Topic: Advanced Cloudformation

Useful links:
- Cloudformation [template reference](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html)
- Cloudformation [changesets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-changesets.html)

### Task: Create the infrastructure stack that imitates highly available web site, with additional security items, using Cloudformation

NOTE: The task has to be implemented step by step, in order below. On the first step you'll need to create a template file from scratch with mentioned resources (see Step 1) and deploy them using Cloudformation AWS console. Starting from step 2, add new required items into the template file created on step 1, and apply it using Cloudformation Changesets using Cloudformation AWS console.

##### Step 1: Create VPC
Stack items to create:
- VPC with 10.20.0.0/16 mask
- Internet Gateway attached to the VPC
- S3 bucket

Note: after the creation manually upload a sample file into the created S3 bucket

##### Step 2: Extend VPC with subnets
Stack items to add:
- Two public subnets in different availability zones
- Two private subnets in different availability zones
- Security group with ports 80 and 22 opened for your personal extenal IP only. The SG has to be attached to your VPC

##### Step 3: Add NAT gateway and routing
Stack items to add:
- Route table for public subnets with traffic being sent to Internet gateway
- Elastic IP (EIP)
- NAT Gateway attached to any of public subnets and associated with the EIP
- Route table for private subnets with traffic being sent to NAT gateway

##### Step 4: Load balancing and autoscaling
Stack items to add:
- Application load balancer with 80 port listener and associated with 2 public subnets
- Target group attached to the Application load balancer
- EC2 instance profile with access to the S3 bucket
- Launch template with Ubuntu image (get the latest LTS from AWS Marketplace) and httpd installed
- Launch template should have EC2 instance profile attached to it
- Autoscaling group with Launch template attached. Minimum running instances - 2

*These links might be helpful:*
1) [EC2 instance profiles](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html)
2) [User data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html)
3) [Launch templates](https://docs.aws.amazon.com/autoscaling/ec2/userguide/LaunchTemplates.html)

##### Step 5: Get output from stack. Tagging resources
Stack items to add:
- Export ELB address in Output section
- Tag each possible item with: 
   1) Key: "Name", Value: "lab08-3-<your_name>"
   2) Key: "Project", Value "Cloudformation"
   3) Key: "Role", Values like ("Security", "WebApplication", "LB", etc.)

##### Step 6: Check if everything works
- Open site by the address obtained from the output section on step 5
- SSH to any instance and try to get file uploaded on step 1 from S3


### Task: Disassemble the stack
- Remove the file from S3 bucket
- Delete the Cloudformation stack. Check if any resources weren't deleted and delete them manually if needed
