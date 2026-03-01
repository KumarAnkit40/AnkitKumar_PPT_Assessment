## Objective
Send an email notification when a file is uploaded to an S3 bucket using Lambda and SNS.

## Steps

1. Create SNS topic
   - Go to SNS → Topics → Create topic
   - Type: Standard
   - Provide topic name

2. Create subscription
   - Protocol: Email
   - Enter email address
   - Confirm subscription from email inbox

3. Create S3 bucket
   - Go to S3 → Create bucket
   - Provide unique name

4. Create IAM role for Lambda
   - Go to IAM → Roles → Create role
   - Trusted entity: AWS service
   - Use case: Lambda
   - Attach policies: AWSLambdaBasicExecutionRole and AmazonSNSFullAccess

5. Create Lambda function
   - Go to Lambda → Create function
   - Runtime: Python 3.x
   - Select the created IAM role

6. Add Lambda code
   import json
   import boto3

   sns = boto3.client('sns')
   topic_arn = "SNS-TOPIC-ARN"

   def lambda_handler(event, context):
       message = "File uploaded to S3 bucket"
       sns.publish(
           TopicArn=topic_arn,
           Message=message,
           Subject="S3 Upload Notification"
       )
       return {'statusCode': 200}

7. Add S3 trigger
   - Open Lambda → Add trigger
   - Select S3
   - Event type: PUT (Object Created)

8. Test
   - Upload a file to the S3 bucket

9. Check email inbox

## Result
An email notification is received whenever a file is uploaded to the S3 bucket.