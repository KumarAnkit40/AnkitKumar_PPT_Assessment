## Objective
Create a CloudWatch alarm to monitor EC2 CPU usage and automatically stop the instance and send an email when CPU exceeds 70%.

## Steps

1. Create SNS topic
   - Go to SNS → Topics → Create topic
   - Type: Standard
   - Provide topic name

2. Create email subscription
   - Protocol: Email
   - Enter email address
   - Confirm subscription from email inbox

3. Open CloudWatch
   - Go to CloudWatch → Alarms → Create alarm

4. Select metric
   - Choose EC2 → Per-Instance Metrics
   - Select CPUUtilization for the EC2 instance

5. Configure condition
   - Threshold type: Static
   - Whenever CPUUtilization ≥ 70%
   - Period: 5 minutes

6. Configure actions
   - Notification: Select SNS topic
   - EC2 Action: Stop this instance

7. Create alarm

8. Generate load on EC2 (optional)
   sudo apt update -y
   sudo apt install stress -y
   stress --cpu 2 --timeout 300

9. Wait for alarm to trigger

## Result
An email notification is received and the EC2 instance automatically stops when CPU utilization exceeds 70%.