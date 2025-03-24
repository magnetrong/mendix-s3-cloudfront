# Mendix S3 CloudFront Integration

This repository provides resources and guides for implementing an optimized video delivery solution for Mendix applications using Amazon S3 and CloudFront.

## Overview

When Mendix applications serve video content directly, files must be loaded entirely into memory before delivery, creating performance bottlenecks. This repository offers a solution by integrating Amazon S3 for scalable storage and CloudFront for efficient content delivery.

## Benefits

- **Improved Performance**: Eliminate memory bottlenecks in your Mendix application
- **Scalable Solution**: Handle any amount of video content with ease
- **Global Delivery**: Deliver videos with minimal latency worldwide via CloudFront's edge locations
- **Cost Efficiency**: Pay only for what you use with AWS's elastic pricing model

## Implementation Options

We provide two different approaches to implement this solution:

### [Quick Setup with CloudFormation (15 minutes)](./cloudformation/README.md)

For developers looking to get up and running quickly with minimal AWS configuration:
- Deploy a pre-configured CloudFormation template
- Upload video content to the automatically created S3 bucket
- Use the CloudFront distribution endpoint in your Mendix application

👉 [CloudFormation Setup Guide](./cloudformation/README.md)

### [Manual Configuration (30 minutes)](./manual/README.md)

For developers who prefer to understand each component or need custom settings:
- Step-by-step instructions for creating and configuring S3 buckets
- Detailed guide for setting up CloudFront distributions
- Instructions for connecting your Mendix application

👉 [Manual Setup Guide](./manual/README.md)

## Support and Contributions

If you encounter issues or have suggestions for improvements, please open an issue in this repository. Contributions via pull requests are welcome.
