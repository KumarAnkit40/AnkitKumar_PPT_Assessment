## Objective
Host a static website using an Amazon S3 bucket.

## Steps

1. Create an S3 bucket
   - Go to S3 → Create bucket
   - Bucket name: unique name
   - Region: any region
   - Disable “Block all public access”
   - Acknowledge warning and create bucket

2. Enable Static Website Hosting
   - Open the bucket
   - Go to Properties tab
   - Enable Static website hosting
   - Index document: index.html
   - Save changes

3. Upload website files
   - Go to Objects → Upload
   - Upload index.html file

4. Set public permissions
   - Select index.html
   - Actions → Make public using ACL

5. Add bucket policy
   - Go to Permissions → Bucket Policy
   - Add the following policy:

   {
     "Version":"2012-10-17",
     "Statement":[
       {
         "Sid":"PublicRead",
         "Effect":"Allow",
         "Principal":"*",
         "Action":["s3:GetObject"],
         "Resource":["arn:aws:s3:::YOUR-BUCKET-NAME/*"]
       }
     ]
   }

6. Copy website endpoint
   - Go to Properties → Static Website Hosting
   - Copy the endpoint URL

7. Open endpoint in browser

## Result
The static website is successfully accessible using the S3 website endpoint URL.