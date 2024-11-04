# 🚀 Deploying a Static Website with Amazon S3 ☁️

This repository provides a step-by-step guide to hosting a static website on Amazon S3. By using S3 for static web hosting, we can achieve a high-performance, globally accessible website.

## Prerequisites
- AWS Account
- AWS CLI (optional for additional configuration)
- Basic knowledge of HTML, CSS, and JavaScript

## Steps to Set Up S3 Static Website Hosting

### 1. Create an S3 Bucket

1. Go to the [S3 Console](https://s3.console.aws.amazon.com/).
2. Create a new bucket and name it to match your domain (e.g., `example.com`).
3. Select the appropriate region for your audience.

### 2. Configure Bucket for Static Website Hosting

1. In your S3 bucket, go to **Properties** > **Static website hosting**.
2. Enable **Static website hosting**.
3. Set the **Index document** to `index.html`.
4. Optionally, set the **Error document** to `error.html` (if you have one).

### 3. Upload Website Files

1. Navigate to **Objects** in your S3 bucket.
2. Upload your HTML, CSS, and JavaScript files located in the `website-files` folder.
3. Ensure public read access by setting permissions (we'll apply a bucket policy below).

### 4. Set Bucket Policy for Public Access

To make the website files publicly accessible, apply the following bucket policy. Replace `YOUR_BUCKET_NAME` with the name of your S3 bucket.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
    }
  ]
}
 
