## Objective
Configure S3 bucket replication and lifecycle rules for backup and storage cost optimization.

## Steps

1. Create two S3 buckets
   - Source bucket (example: source-bucket)
   - Destination bucket (example: destination-bucket)
   - Enable versioning on BOTH buckets
     Properties → Bucket Versioning → Enable

2. Create IAM role for replication
   - Go to IAM → Roles → Create role
   - Trusted entity: AWS service
   - Use case: S3
   - Attach policy: AmazonS3FullAccess
   - Create role

3. Configure replication
   - Open source bucket → Management tab
   - Replication rules → Create rule
   - Rule scope: Apply to all objects
   - Destination: choose destination bucket
   - Select the IAM role created
   - Save rule

4. Test replication
   - Upload a file to the source bucket
   - Verify the file appears in the destination bucket

5. Create lifecycle policy
   - Go to source bucket → Management
   - Lifecycle rules → Create rule
   - Apply to all objects
   - Transition current versions to Standard-IA after 30 days
   - Expire objects after 365 days
   - Save rule

## Result
Objects uploaded to the source bucket are automatically replicated to the destination bucket, and lifecycle rules manage storage class transition and expiration.