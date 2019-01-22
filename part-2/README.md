# **Versioning and Aliases of Lambda Functions**
This is part of a set of labs/tutorials [serverless-website-labs] with this part focusing on versioning and aliases of Lambda functions.

## Overview
This part creates multiple versions of a Lambda function, sets up aliases and then configures traffic routing
1. Create a simple Lambda function
2. Create 3 versions of the Lambda function
3. Create aliases for the Lambda function for the latest version and a previous version


## Architecture
The below shows the process flow/architecture for this lab
![alt text][Serverless Website]

## Steps

### 1. Setup S3 bucket to host static Website
create new S3 bucket and configure to host a static website

### 2. Upload files to S3 bucket
Upload index.html and error.html files to newly created S3 bucket.

[comment]: # (references used in README)
[serverless-website-labs]:../README.md
[Serverless Website]:../images/Serverless-Website-Lab.jpeg
[Part-1]:part-1/
