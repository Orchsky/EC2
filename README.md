# What is ec2
- ec2 concept - virtual machines / concept of virtualization
- terminology of ec2 --> instances
  
## AMI's
- AMI's: An Amazon Machine Image (AMI) is a template that contains a software configuration (for example, an operating system, an application server, and applications). From an AMI, you launch an instance, which is a copy of the AMI running as a virtual server in the cloud. You can launch multiple instances of an AMI.
- Your instances keep running until you stop, hibernate, or terminate them, or until they fail. If an instance fails, you can launch a new one from the AMI.
- Examples: Linux, Windows, Mac OS

## Instance Types
- When you launch an instance, the instance type that you specify determines the hardware of the host computer used for your instance. Each instance type offers different compute, memory, and storage capabilities, and is grouped in an instance family based on these capabilities. Select an instance type based on the requirements of the application or software that you plan to run on your instance.
- [Types](https://aws.amazon.com/ec2/instance-types/)
  
## Regions / AZ
- What is a region: collection of AWS data centers.
- What is an AZ: individual data center
- Each Region is a separate geographic area.
Availability Zones are multiple, isolated locations within each Region.

## Tags
- Tags are used across all different AWS resources. They provide metadata about the resource for auditing / organization purposes.

## Networking & Security of EC2: Keypairs
- Keypairs: SSH keys used for secure method of connecting to your instance.
- Public key / private key.
- Never give out private key or expose it.
- SSH keys stored in ~/.ssh/authorized_keys
- You can use Amazon EC2 to create your key pairs. You can also use a third-party tool to create your key pairs, and then import the public keys to Amazon EC2.
- EC2 doesn't keep a copy of your private key, there is no way to recover a private key if you lose it. However, there can still be a way to connect to instances for which you've lost the private key.

## EC2 Networking / Security - VPC
- VPC is the underlying foundation to EC2.
- EC2 is provisioned inside of a VPC.

## EC2 Networking / Security - Security Groups
- A security group acts as a virtual firewall for your EC2 instances to control incoming and outgoing traffic. Inbound rules control the incoming traffic to your instance, and outbound rules control the outgoing traffic from your instance. When you launch an instance, you can specify one or more security groups. If you don't specify a security group, Amazon EC2 uses the default security group. 
- Security groups can allow traffic to and from certain HTTP + HTTPS ports.
- Security in general is a shared responsibility between AWS and you.
- [More info](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)
  
## Networking & Security - Elastic IP
- An Elastic IP address is a static IPv4 address designed for dynamic cloud computing. An Elastic IP address is allocated to your AWS account, and is yours until you release it. By using an Elastic IP address, you can mask the failure of an instance or software by rapidly remapping the address to another instance in your account.
- IP's change everytime for public instances however if you need a static IP then this is the solution.
- Example use case --> web server IP serving content must remain the same otherwise customers will not be able to find the website again.

## Storage
- EBS: Elastic Block Store provides block level storage volumes for use with EC2 instances. EBS volumes behave like raw, unformatted block devices. You can mount these volumes as devices on your instances. EBS volumes that are attached to an instance are exposed as storage volumes that persist independently from the life of the instance. You can create a file system on top of these volumes, or use them in any way you would use a block device (such as a hard drive). You can dynamically change the configuration of a volume attached to an instance.
- When you provision an instance the data is persisted in an external block so if in the case that the server goes down you still have your data for backup.

## Pricing of ec2
- On-Demand Instances
Pay for the instances that you use by the second, with a minimum of 60 seconds, with no long-term commitments or upfront payments.
- Savings Plans
You can reduce your Amazon EC2 costs by making a commitment to a consistent amount of usage, in USD per hour, for a term of 1 or 3 years.
- Reserved Instances
You can reduce your Amazon EC2 costs by making a commitment to a specific instance configuration, including instance type and Region, for a term of 1 or 3 years.
- Spot Instances
Request unused EC2 instances, which can reduce your Amazon EC2 costs significantly.

# What is Linux
- Linux is an open source operating system in which a majority of the cloud and current devops tools have been developed on

## Why is Linux important in DevOps
- It has native integrations to a lot of devops tooling and allows us more control over the operating system.

### Distros
- What is a distro -> linux flavor
- What are the differences - package managers
- Main distros include debian and redhat

### commands
- switch to root --> ```sudo su```
- change directory --> ```cd```
- show current directory --> ```pwd```
- list current files in directory --> ```ls``` or ```ls -al```
- how to create empty files --> ```touch filename.txt```
- how to show contents of the file --> ```cat filename.txt``` 
- how to delete files --> ```rm -rf filename.txt```
- how to copy and move files --> ```cp filename.txt filename2.txt``` and ```mv filename.txt folder1/``` 
- how to create directories and remove them --> ```mkdir folder2``` and ```rmdir folder2``` , if the folder has files in it use ```rm -rf folder2/```
- update packages --> ```sudo yum update -y```
- install packages ```sudo yum install example -y```
- filter for words in large terminal output --> ```example command | grep -i wordyou'relookingfor```
- make a file executible --> ```chmod +x```
- run a script --> ```sudo ./example.sh```

### vim editor
- edit a file --> ```vi filename.txt```
- type i in your keyboard to enter insert mode
- type contents into file
- type ^c (control c) or escape when done
- type ```:x``` to save 
- type ```:q!``` to not save
