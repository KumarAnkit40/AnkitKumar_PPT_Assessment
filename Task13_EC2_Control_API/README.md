## Objective
Automate starting and stopping of an EC2 instance using a Lambda function triggered through API Gateway.

## Steps

1. Create IAM role for Lambda
   - Go to IAM → Roles → Create role
   - Trusted entity: AWS service
   - Use case: Lambda
   - Attach policy: AmazonEC2FullAccess and AWSLambdaBasicExecutionRole

2. Create Lambda function
   - Go to Lambda → Create function
   - Runtime: Python 3.x
   - Select the created IAM role

3. Add Lambda code
   import boto3

   ec2 = boto3.client('ec2')
   instance_id = "INSTANCE-ID"

   def lambda_handler(event, context):
       action = event.get('action')

       if action == "start":
           ec2.start_instances(InstanceIds=[instance_id])
           return "Instance Started"

       elif action == "stop":
           ec2.stop_instances(InstanceIds=[instance_id])
           return "Instance Stopped"

       else:
           return "Invalid Action"

4. Test Lambda
   - Create test event
     { "action": "start" }

5. Create API Gateway
   - Go to API Gateway → Create API → HTTP API
   - Create route: /ec2
   - Method: POST
   - Integration: Lambda function

6. Deploy API
   - Create stage and deploy
   - Copy Invoke URL

7. Test using browser or Postman
   - POST request body:
     { "action": "stop" }

8. Verify EC2 instance state in EC2 console

## Result
The EC2 instance starts or stops successfully using the API endpoint.