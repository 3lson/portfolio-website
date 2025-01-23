# Personal Portfolio Website on AWS

**This website is now archived as I have migrated it to github.io** [SEE HERE]()

This repository contains a step by step guide for a personal portfolio website, which is hosted on Amazon Web Services (AWS) using S3 for static website hosting and CloudFront for content delivery. Below are the steps I followed to set up the website.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Deployment Steps](#deployment-steps)
- [Updating the Website](#updating-the-website)
- [Conclusion](#conclusion)

## Prerequisites

Before you begin, ensure you have the following:

- An AWS account.
- AWS CLI installed and configured (optional for advanced users).
- Basic knowledge of HTML, CSS, and JavaScript.

## Deployment Steps

### Step 1: Create an S3 Bucket

1. Log in to the [AWS Management Console](https://aws.amazon.com/console/).
2. Navigate to **S3** under the Services menu.
3. Click on **Create bucket**.
4. Enter a unique bucket name (e.g., `your-portfolio-website`).
5. Choose the appropriate AWS Region.
6. Uncheck the **Block all public access** option.
7. Click on **Create bucket**.

### Step 2: Upload Website Files

1. Open your created S3 bucket.
2. Click on **Upload** and add your website files (e.g., `index.html`, `styles.css`, etc.).
3. Click on **Upload** to complete the process.

### Step 3: Set Permissions

1. Go to the **Permissions** tab of your S3 bucket.
2. Click on **Bucket Policy** and add the following policy:
   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Sid": "PublicReadGetObject",
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
       }
     ]
   }

3. Replace `YOUR-BUCKET-NAME` with the name of your bucket.
4. Click Save

### Step 4: Enable Static Website Hosting
1. Go to the **Properties** tab.
2. Scroll down to the **Static website hosting** section.
3. Select **Use this bucket to host a website**.
4. Enter index.html as the **Index document**.
5. (Optional) Enter an error document if you have one (e.g., error.html).
6. Click **Save changes**.

### Step 5: Create a CloudFront Distribution
1. Navigate to the CloudFront console.
2. Click on **Create Distribution**.
3. Under **Web**, click **Get Started**.
4. In the **Origin Settings**:
- Set **Origin Domain Name** to your S3 static website endpoint (e.g., your-bucket-name.s3-website-us-east-1.amazonaws.com).
- Set **Protocol** to **HTTP** and **Port** to 80.
5. Configure the **Viewer Protocol Policy** to **Redirect HTTP to HTTPS**.
6. Click **Create Distribution** and wait for it to deploy.

### Step 6: Access Your Website
1. After deployment, note the CloudFront Domain Name (e.g., dxxxxxxxxxxxx.cloudfront.net).
2. Open a web browser and go to the CloudFront domain to view your live website.

## Updating the Website
Whenever you make changes to your website files (e.g., index.html), follow these steps to update:

1. Edit your files locally.
2. Log in to the AWS Management Console and navigate to S3.
3. Open your S3 bucket and locate the file to update.
4. Click on **Upload** to upload the new version of the file.
5. Confirm the upload and check your website to see the changes.

## Conclusion
This repository contains the code and configuration for my personal portfolio website, demonstrating my skills in web development and cloud infrastructure. Feel free to clone the repository, review the code, or follow the steps above to set up your own AWS-hosted portfolio.
