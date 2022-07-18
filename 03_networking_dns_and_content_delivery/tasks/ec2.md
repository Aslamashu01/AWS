# Running EC2 Instances

- Create Bastion Host
- Create a host in private subnet
- Configure ssh access to instances
## Go to EC2 Dashboard and Launch Instance in your VPC Region

![](images/ec2-console.jpg)

![](images/aws-ec2-create.jpg)


### Create Bastion Instance 

#### Choose AMI

Requirements:
- Amazon Linux 2 AMI (HVM), SSD Volume Type 
- Architecture: `64-bit (x86)`

![](images/aws-ec2-AMI.png)

#### Choose Instance Type

Requirements:
- Instance Type: `t2.micro`

![](images/aws-ec2-instance-type.png)

#### Configure Instance Details

Requirements:
- Number of instances: `1`
- Network: `my-vpc-01`
- Subnet: `my-dev-01-sub-pub-c`
- Auto-assign Public IP: use default settings
- Shutdown behavior: `Terminate`
- User-data (script to run on instance boot): 
    ```
    #!/bin/bash
    yum install -y tree
    ```
![](images/aws-ec2-conf-details.png)
![](images/aws-ec2-conf-details1.png)

#### Add Storage

Requirements:
- Volume Type `Root`, Size (GiB): `8GB`, General Purpose SSD (gp2), Delete on Termination: Checked
- Volume Type `EBS`, Size (GiB): `10GB`, General Purpose SSD (gp2), Delete on Termination: Checked

![](images/aws-ec2-create-disk.png)

#### Add Tags

Tags:
- Name: `bastion-01`
- Stack: `dev`
- Owner: `{Your Name}`

![](images/aws-ec2-create-tags.jpg)


#### Configure Security Groups

Requirements:
- Security group name: `bastion-01-sg`
- Description: `Bastion-01 Security Group`
- SSH, Source `My IP`, Description `{Your Name} Home IP`

![](images/aws-ec2-create-sg.jpg)

#### Review

#### Create SSH Key (One-time operation)

![](images/aws-ec2-create-ssh.jpg)

**!!! Download generated key**

#### Launch Instance

#### Review:

![](images/aws-ec2-created.jpg)


### Connect to Bastion Instance

![](images/aws-ec2-created-2.jpg)
![](images/aws-ec2-connect.jpg)

## Create an Instance in Private Subnet

Requirements:

- AMI: `Amazon Linux 2 AMI (HVM), SSD Volume Type`
- Type: `t2.micro`
- Network: `my-vpc-01`
- Subnet: `my-dev-01-priv-b`
- Shutdown behavior: `Terminate`
- Name tag: `private-host`
- SSH Key: `created in the previous step`

### Connect to the host in Private Network:

Create ssh config file on the host machine(`~/.ssh/config`):
```
Host bastion
  User ec2-user
  HostName {bastion_public_ip}
  IdentityFile {path/to/ssh_key_file}
  ForwardAgent yes

Host private
  User ec2-user
  HostName {second_instance_private_ip}
  ForwardAgent yes
  ProxyCommand ssh -W %h:%p bastion
  IdentityFile {path/to/ssh_key_file}
```
In this ~/.ssh/config file we use `ProxyCommand` to connect to private host through bastion.

![](images/ssh-ec2-1-2.jpg)
