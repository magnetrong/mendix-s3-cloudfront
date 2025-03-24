# How-to: Configure a CloudFront Distribution for your Amazon S3 video content

## Prerequisites

- Mendix Studio Pro 9.6.0 or higher
- An IAM user that has the following rights:
  - Access to the AWS console
  - Amazon S3
    - Create a bucket (CreateBucket)
    - Upload a file (PutObject)
  - Amazon CloudFront
    - Create a distribution (CreateDistribution)

## Step-by-Step Guide

### Navigate to Amazon S3 Console

1. Log in into the AWS console using the IAM user that has the rights.
2. Once logged in, search for 'S3' in the top bar and click the top result. 

![navigate-to-s3](https://raw.githubusercontent.com/magnetrong/mendix-s3-cloudfront/refs/heads/main/manual/assets/_1_navigate-to-s3.gif)

### Creating a bucket

3. You should see an overview of S3 Buckets, hit the 'Create bucket' button.
4. General configuration:
   - AWS Region: What makes sense for your use case? Choose close proximity to the end-user
   - Bucket type: General purpose
   - Bucket name: Provide your bucket with a name, the name should be DNS compatible
5. The rest can be left on default values, hit the 'Create bucket' button in the bottom.

![create-a-bucket](https://raw.githubusercontent.com/magnetrong/mendix-s3-cloudfront/refs/heads/main/manual/assets/_2_creating-a-bucket.gif)

### Uploading your video

6. You'll return to the overview of S3 Buckets, navigate to the bucket you just created.
7. You should see an overview of S3 Object resources, hit the 'Upload' button.
8. Specify a video file for your upload using the drag-and-drop or use either the "Add files" or "Add folder" button.
9. Once the file is specified, click the 'Upload' button.

![uploading-a-video](https://raw.githubusercontent.com/magnetrong/mendix-s3-cloudfront/refs/heads/main/manual/assets/_3_uploading-video.gif)

### Creating a distribution endpoint

10. Search for 'CloudFront' in the top bar and click the top result.
11. You should see an overview of CloudFront Distribution resources, hit the 'Create distribution' button.
12. Origin settings:
    - Origin domain: Select the created S3 Bucket
    - Origin access: Origin Access Control settings
      - Selecting this option, a drop-down should appear with a button "Create new OAC", click on this button.
      - A pop-up window should appear, click the 'Create' button.
13. Web Application Firewall (WAF):
    - For the sake of this guide, do not enable security protections. For production purposes, you might want to consider enabling this feature to block malicious actors.
14. The rest can be left on default values, hit the 'Create distribution' button in the bottom.
15. Your distribution is now being deployed, this might take about 5 minutes.
16. You should see a yellow-colored toaster message 'The S3 bucket policy needs to be updated'. Click 'Copy policy'.

![create-distribution-endpoint](https://raw.githubusercontent.com/magnetrong/mendix-s3-cloudfront/refs/heads/main/manual/assets/_4_create-distribution-endpoint.gif) 

### Allowing your CloudFront distribution to retrieve the video to cache it

17. Search for 'S3' in the top bar and click the top result.
18. Navigate to the S3 Bucket created earlier.
19. Click the 'Permissions' tab.
20. In the Bucket policy section, click 'Edit' in the top right corner.
21. Paste the policy you had copied in step 16 and click 'Save changes' in the bottom right corner.

![setting-permissions](https://raw.githubusercontent.com/magnetrong/mendix-s3-cloudfront/refs/heads/main/manual/assets/_5_setting-permissions.gif)

### Testing access

22. Search for 'CloudFront' in the top bar and click the top result.
23. Navigate to the CloudFront Distribution created earlier.
24. In the Details section, copy the Distribution domain name, it should look something like `1234abc.cloudfront.net`.
25. The endpoint to access the uploaded video file should be your endpoint appended with `/<yourfilename.extension>`, e.g., `https://1234abc.cloudfront.net/video.mp4`.

![testing-access](https://raw.githubusercontent.com/magnetrong/mendix-s3-cloudfront/refs/heads/main/manual/assets/_6_testing-access.gif)

### Stream the video content to your Mendix application

26. In your Mendix application, use the 'Video Player' widget.
27. Configure the 'Video URL' parameter to the endpoint for your video.
