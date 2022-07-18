# Domain: Automation and Optimization 

## Topic: Cloudformation 

### Task: Create VPC 

Create a stack using Cloudformation template. The stack should contain at least the following resources: 

- VPC with CIDR 10.0.0.0/16 
- Two public subnets 
- Two private subnets 
- NAT Gateway 
- Internet Gateway 
- Public route table for public subnets with traffic routing via Internet gateway 
- Private route table for private subnets with traffic routing via NAT gateway 
- Elastic IP attached to NAT gateway 

And output exported: 
- VPCId 
- Public subnets names 
- Private subnet names 

## Solution
### Creating the VPC stack
1) Open Cloudformation in AWS web console. If necessary, change the region.
2) From the left menu choose "Stacks" -> "Create stack"
3) Select "Template is ready", "Upload a template file" and Choose the file "08-02.yml" from this repo, click "Next"
4) Set stack name like "lab08-02", change VPCName if you want, click "Next"
5) On "Configure stack options" page leave the settings as is and click "Next"
6) On "Review" page click "Create stack" and wait until the stack is created. The status of the stack must be "CREATE_COMPLETE"
7) Check the output of the stack by clicking to "Outputs" tab
8) Review the resources created using VPC manamagement console

### Tearing down
1) Open Cloudformation in AWS web console. If necessary, change the region where the VPC stack was created.
2) From the left menu choose "Stacks" -> Choose the stack you created
3) On the right side click "Delete" button, confirm deletion by pressing "Delete stack" button
4) Wait until stack's deletion process. It may take up to several minutes.

