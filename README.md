# terra-branch

Simple Terraform infrastructure. Creates surrounding infrastructure and launches a simple instance into it with a public IP and SSH access.

## Project Inputs

- access_key: **String**
- secret_key: **String**

Both pulled from system environment variables named;

- TF_VAR_access_key
- TF_VAR_secret_key

## Project Outputs

- instance_ip: **Outputs the Public IP of the Instance to the Console**

***

## EC2 Module

The EC2 module is configured to create a single EC2 instance with a network interface.
### Inputs

- instance_type: **String**
- ami: **String**
- security_group: **Security Group ID**
- subnet_id: **Subnet Group ID**
- key_name: **String**
- availability_zone: **String**
- instance_private_ip: **String**

### Outputs

- instance_public_IP: **Public IP of instance on launch**

***

## Subnets Module

The Subnets module is configured to create a single (public) subnet that maps a public IP to instance automatically on launch.
Also creates a security group for the subnet and assosiates a provided route table to it.
### Inputs

- vpc_id: **VPC ID**
- subnet_cidr: **String**
- availability_zone: **String**
- route_table_id: **Route Table ID**

### Outputs

- subnet_id: **ID of Created Subnet**
- security_group: **ID of Created Security Group**
- subnet_cidr: **CIDR of Subnet**

***

## VPC Module

The VPC module creates a new VPC, containing a standard Internet Gateway and a route table to properly allow access to the gateway.
### Inputs

- vpc_cidr: **String**

### Outputs

- vpc_id: **ID of Created VPC**
- route_table_id: **ID of Created Route Table**
