## Objective
Use CloudFront CDN to deliver the static website hosted in an S3 bucket.

## Steps

1. Ensure S3 static website is working
   - Open S3 bucket
   - Static website hosting enabled
   - index.html uploaded

2. Create CloudFront distribution
   - Go to CloudFront → Create distribution
   - Origin domain: select S3 website endpoint
   - Protocol: HTTP only (for website endpoint)

3. Configure settings
   - Viewer protocol policy: Redirect HTTP to HTTPS
   - Default root object: index.html

4. Create distribution
   - Leave remaining settings as default
   - Create and wait for deployment

5. Copy CloudFront domain name
   - Example: dxxxxx.cloudfront.net

6. Open domain in browser

## Result
The website is successfully accessible using the CloudFront domain and loads through CDN.