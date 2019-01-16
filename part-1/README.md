# **Simple Serverless Website Lab as part of acloudguru course**
This is part of a set of labs/tutorials [serverless-website-labs]

## Overview
This part creates a simple website page hosted on S3 that calls a Lambda function via a API Gateway API.  The steps are as follows:
1. Create/update website S3 bucket and add index.html and error.html files
2. Register public domain or use the public URL for the S3 bucket.

## Architecture
The below shows the process flow/architecture for this part
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



		helpmestudyawspolly-djh.com
	Permissions
		public
			needed to see html files
	bucket setup as a static website
		index.html
		error.html
	Needed custom bucket policy to make everything here public
		{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::helpmestudyawspolly-djh.com/*"
        }
    ]
}
		NOTE: Resource needs to be updated to be the address of the bucket
	address
		ARN: arn:aws:s3:::helpmestudyawspolly-djh.com
2.  Register public domain
	Using Route 53, check for domain name and register
	Can use the S3 URL instead of paying for a domain name
3.  Create a Lambda function
	Author from scratch and use the code provided in the hellocloudgurus.py
	Runtime
		Python 3.6
	Policy template for Role (if it doesn't exist)
		Simple Microservice template
	Configure Triggers
		API Gateway
		Create a new API
			myServerlessWebsite
			Deployment Stage
				prod
			Security
				open
4.  Configure the API Gateway API
	Delete the ANY method
	Add a GET method
		Lambda function is the integration type
		enable Use Lambda Proxy Integration
5.  Deploy the API
	Deployment stage
		prod (from previous)
6.  Invoke the API via the URL
	Go to the Stages and choose the GET method.  The URL will be there