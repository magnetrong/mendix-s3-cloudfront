# Quick Start: Deploy S3 and CloudFront Using CloudFormation

## What This Template Does

Our CloudFormation template automates the creation of:
- An Amazon S3 bucket for video storage
- An Amazon CloudFront distribution
- Necessary IAM roles and permissions
- Secure access configurations

## Estimated Deployment Time: 15 minutes

### Prepare Your AWS Environment

1. Log in to the AWS Management Console
2. Navigate to the CloudFormation service
3. Ensure you're in the desired AWS region for your deployment

### Deploy the CloudFormation Template

#### Deploy via AWS Console

1. Click "Create stack"
2. Save the contents of the CloudFormation template as a YAML file, you can right-click and save this [link](https://raw.githubusercontent.com/magnetrong/mendix-s3-cloudfront/refs/heads/main/cloudformation/cloudformation.yaml)
3. For `Template Source` select "Upload a template file" 
4. Select the file you saved in step 4
5. Click "Next"

### Configure Stack Parameters

During deployment, you'll be prompted to provide:
- Stack name
- Bucket name

### Configure stack options

1. The default options suffice, review the stack configuration
2. Click "Create stack"
3. Wait for stack creation (typically 5-10 minutes)

### Retrieve Outputs

After successful deployment, go to the Outputs tab in CloudFormation to find:
- S3 Bucket Name
- CloudFront Distribution Domain

![deploy-aws-resources](https://raw.githubusercontent.com/magnetrong/mendix-s3-cloudfront/refs/heads/main/cloudformation/assets/deploy-aws-resources.gif)

### Upload Your Video

1. Navigate to the created S3 bucket
2. Upload your video file
3. Verify the file is accessible via the CloudFront URL, the URL at which you can access the video file should be the distribution endpoint + your video file name. E.g., `https://1234abc.cloudfront.net/video.mp4`

![upload-video](https://raw.githubusercontent.com/magnetrong/mendix-s3-cloudfront/refs/heads/main/cloudformation/assets/upload-video.gif)

### Integrate with Mendix

1. Open your Mendix application
2. Use the Video Player widget
3. Set the Video URL to the CloudFront distribution URL + video filename
