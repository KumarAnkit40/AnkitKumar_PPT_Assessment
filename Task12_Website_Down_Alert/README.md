## Objective
Monitor a website and send an alert email if the website becomes unavailable.

## Steps

1. Create SNS topic
   - Go to SNS → Topics → Create topic
   - Type: Standard
   - Provide topic name

2. Create email subscription
   - Protocol: Email
   - Enter email address
   - Confirm the subscription from email inbox

3. Open CloudWatch
   - Go to CloudWatch → Synthetics Canaries → Create canary

4. Configure Canary
   - Blueprint: Heartbeat monitoring
   - Provide website URL
   - Schedule: Every 5 minutes
   - Runtime: Python

5. Configure IAM role
   - Allow CloudWatch Synthetics permissions

6. Create alarm
   - Go to CloudWatch → Alarms → Create alarm
   - Metric: Canary Failed
   - Threshold: greater than 0

7. Add notification
   - Select SNS topic created earlier

8. Test monitoring
   - Stop the website or provide invalid URL
   - Wait for monitoring interval

9. Check email notification

## Result
An alert email is received when the monitored website becomes unavailable.