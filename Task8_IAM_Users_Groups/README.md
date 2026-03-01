## Objective
Create IAM users and groups and assign permissions using policies.

## Steps

1. Open IAM service
   - Go to IAM → User groups → Create group

2. Create group
   - Group name: Developers
   - Attach policy: AmazonS3ReadOnlyAccess
   - Create group

3. Create IAM user
   - Go to IAM → Users → Add users
   - Username: user1
   - Access type: AWS Management Console access
   - Set custom password

4. Add user to group
   - Select the Developers group
   - Add user to the group

5. Sign in as new user
   - Open IAM sign-in URL
   - Login using created credentials

6. Verify permissions
   - Access S3 service
   - Confirm read-only access

## Result
IAM user successfully logs in and receives permissions based on the assigned group policy.