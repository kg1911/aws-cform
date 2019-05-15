# aws-cform
CloudFormation Template for ready&amp;go basic environment

This template is subject to change for continuous improvement. The goal is to have the user enter the least information will having a working basic environment in seconds.

#################################PARAMETERS#################################
"Parameters" is the section of the template where you define input values that will be used in the resources section. This section allow you to prompt the user about precise information needed to complete the environment setup.

"InstanceType": parameter used to list the EC2 instance size wanted for the bastion host

"MyVpcCidrBlock": Define the IP range of your VPC. This range will be the container of region's subnets

"BastionKeyName": Define the keypair to attach to your bastion host. Note that you have to create a keypair manually prior of deploying this template.

#################################RESOURCES#################################
This is where you define all the component necessary in your architecture.
Include:
- VPC
- InternetGateway (for public subnet)
- NatGateway (for private subnet)
- Two public & two private subnet
- Route table for either private & public subnet
  - Private route table default route is the NatGateway
  - Public route table default route is the InternetGateway
- A bastion host for remote cli access to your environment
- A bastion security group with predefine SSH access to only your corporate or home public IP
