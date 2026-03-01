## Objective
Access an S3 bucket from an EC2 instance using an IAM role instead of access keys.

## Steps

1. Create S3 bucket
   - Go to S3 → Create bucket
   - Provide unique bucket name
   - Create bucket

2. Create IAM role
   - Go to IAM → Roles → Create role
   - Trusted entity: AWS service
   - Use case: EC2
   - Attach policy: AmazonS3FullAccess
   - Create role

3. Attach role to EC2
   - Go to EC2 → Instances
   - Select instance → Actions → Security → Modify IAM role
   - Attach the created IAM role

4. Connect to EC2
   ssh -i keypair.pem ubuntu@<Public-IP>

5. Install AWS CLI
   sudo apt update -y
   sudo apt install awscli -y

6. Verify role
   aws sts get-caller-identity

7. List S3 buckets
   aws s3 ls

8. Create test file
   echo "IAM Role Access Working" > test.txt

9. Upload file to S3
   aws s3 cp test.txt s3://<bucket-name>/

10. Verify in S3 console that file is uploaded

## Result
The EC2 instance successfully accesses and uploads files to the S3 bucket using the attached IAM role without access keys.