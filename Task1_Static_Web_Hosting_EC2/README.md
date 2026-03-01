# Task 1 – Static Web Hosting on AWS EC2 (Ubuntu + Nginx)

## Objective
The objective of this task is to deploy a static website on an AWS EC2 Ubuntu instance using the Nginx web server and make it publicly accessible through the instance Public IP address.

## Step 1: Launch EC2 Instance

1. Login to AWS Management Console
2. Open EC2 Dashboard
3. Click Launch Instance
4. Configure instance with following details:
   Name:-
   AMI:- Ubuntu Server 24.04 LTS(HVM)
   Instance Type:- t3.micro (Free Tier) 
   Key Pair:-Create new key pair 

### Security Group Rules

Allow the following inbound rules:
SSH  22
HTTP  80

Launch the instance.

## Step 2: Connect to EC2 Instance
Open terminal in the folder containing the `.pem` key and run:

ssh -i mykey.pem ubuntu@<Your-Public-IP> eg:-98.92.217.182(my instance public IP)

If prompted:
Are you sure you want to continue connecting?

Type:
yes

## Step 3: Update the package manager
sudo apt update
sudo apt upgrade -y

## Step 4: Install Nginx Web Server
sudo apt install nginx -y

Check the service status:
sudo systemctl status nginx
You should see active (running).

## Step 5: Create Static Website

Move to web directory:
cd /var/www/html

Edit index page by using this command:
sudo nano index.html

Add the following HTML code:

<!DOCTYPE html>
<html>
<head>
    <title>AWS EC2 Website</title>
</head>
<body>
    <h1>Welcome to My AWS EC2 Server</h1>
    <p>successfully hosted the static website (Task-1)</p>
</body>
</html>

Save and exit:
CTRL + S for save  and CTRL + X for exit

## Step 7: Access the Website
Open a web browser and enter:
http://<Your-Public-IP> i.e.98.92.217.182

The custom webpage should appear successfully.

## Output / Result
The default Nginx page was replaced with a custom HTML page and the website became publicly accessible through the EC2 Public IP address.

