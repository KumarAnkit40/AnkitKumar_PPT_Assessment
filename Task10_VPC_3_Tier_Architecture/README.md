## Objective
Design a 3-tier network architecture using VPC with public and private subnets.

## Steps

1. Create VPC
   - Go to VPC → Create VPC
   - IPv4 CIDR: 10.0.0.0/16

2. Create Subnets
   - Public Subnet: 10.0.1.0/24
   - Private App Subnet: 10.0.2.0/24
   - Private DB Subnet: 10.0.3.0/24

3. Create Internet Gateway
   - Attach Internet Gateway to VPC

4. Configure Route Table for Public Subnet
   - Create route table
   - Add route: 0.0.0.0/0 → Internet Gateway
   - Associate with Public Subnet

5. Create NAT Gateway
   - Allocate Elastic IP
   - Create NAT Gateway in Public Subnet

6. Configure Private Route Table
   - Create new route table
   - Add route: 0.0.0.0/0 → NAT Gateway
   - Associate with Private App and DB Subnets

7. Launch EC2 Instances
   - Bastion Host in Public Subnet
   - Application Server in Private App Subnet
   - Database Server in Private DB Subnet

8. Configure Security Groups
   - Bastion: allow SSH from internet
   - App Server: allow SSH from Bastion
   - DB Server: allow DB port from App Server

9. Access Private Instance
   - SSH into Bastion host
   - From Bastion, SSH into private instance

## Result
Instances in private subnets securely access the internet through NAT and are reachable only through the Bastion host in the public subnet.