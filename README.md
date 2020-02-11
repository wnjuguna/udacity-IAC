# Udacity Cloud Computing: Infrastructure as Code Project
 This cloud formation template will deploy a webapp on the following infrastructure:
 - VPC
 - s3 read-only IAM role
 - Internet gateway
 - NAT gateways
 - Public and Private subnets in 2 availability zones
 - Launch configuration for: Auto-scaling group, EC2 instances
 - Elastic Load Balancer with Health Checks 
 - Bastion host (Development environment only)

## Supported parameters:
 - EnvType: Prod or Dev
 - KeyName: EC2 Key-pair. (required when EnvType is Dev)
 - TrustedHosts: source ip address permitted to SSH to BastionHost (required when EnvType is Dev)
 - InstanceType: EC2 instance type to deploy
 - VPCSubnet: CIDR network for your VPC
 - FleetSize: Number of EC2 instances to deploy

## How to deploy:
 - Run the following aws-cli command:
  aws cloudformation create-stack --stack-name udagram --parameters ParameterKey=KeyName,ParameterValue=udacity-www-ec2 ParameterKey=TrustedHosts,ParameterValue=102.140.215.137/32 --capabilities CAPABILITY_IAM --template-body file:///mnt/c/Users/williamn/Documents/Udacity/IAC/udagram.yml
## How to destroy stack
 - Run the following aws-cli command:
  aws cloudformation delete-stack --stack-name udagram
