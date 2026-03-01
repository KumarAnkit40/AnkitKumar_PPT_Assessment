## Objective
Configure an Auto Scaling Group with a Load Balancer to provide high availability and automatic scaling for EC2 instances.

## Steps

1. Create a Launch Template
   - Go to EC2 → Launch Templates → Create launch template
   - AMI: Ubuntu Server
   - Instance type: t2.micro
   - Key pair: select existing key
   - Security Group: allow ports 22 and 80

2. Add User Data script
   #!/bin/bash
   apt update -y
   apt install nginx -y
   systemctl start nginx
   systemctl enable nginx
   echo "<h1>Server Running</h1>" > /var/www/html/index.html

3. Create Target Group
   - Go to EC2 → Target Groups
   - Type: Instances
   - Protocol: HTTP
   - Port: 80
   - VPC: select default VPC

4. Create Application Load Balancer
   - Scheme: Internet-facing
   - Listener: HTTP (80)
   - Select public subnets
   - Attach the created target group

5. Create Auto Scaling Group
   - Select launch template
   - Choose same VPC
   - Select public subnets
   - Attach to existing load balancer
   - Desired capacity: 2
   - Minimum: 2
   - Maximum: 4

6. Configure Health Checks
   - Type: ELB health check

7. Wait for instances to launch and register in target group.

8. Copy Load Balancer DNS name and open in browser.

## Result
The website is accessible using the Load Balancer DNS, and multiple EC2 instances are automatically managed by the Auto Scaling Group.