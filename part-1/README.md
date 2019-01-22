# **Simple Serverless Website Lab as part of acloudguru course**
This is part of a set of labs/tutorials [serverless-website-labs]

## Overview
This part creates a simple website page hosted on S3 that calls a Lambda function via a API Gateway API.  The steps are as follows:
1. Create/update website S3 bucket and add index.html and error.html files
2. Register public domain or use the public URL for the S3 bucket.
3. Create Lambda function to return name
4. Create API Gateway API that will call Lambda function
5. Update index.html with API end point and test

## Architecture
The below shows the process flow/architecture for this part
![alt text][Serverless Website Process Flow-Part 1]

## Steps

### 1. Setup S3 bucket to host static Website
Create new S3 bucket and configure to host a static website.  Upload index.html and error.html files to newly created S3 bucket.

### 2. Register public domain or use the public URL for the S3 bucket.
If registering a domain, goto Route 53 and register a domain name.  The top level name of the domain must be the same as the S3 bucket name (e.g. helpmestudypolly.com domain must reference helpmestudypolly.com S3 bucket name).  Can use the S3 URL if not buying a domain name.

### 3. Create and configure Lambda function
Author from scratch and use the code provided in the hellocloudgurus.py file.
Runtime: Python 3.6
Create IAM Role if needed: Use a Policy Template for Simple Microservice
				
### 4. Create API Gateway API that will call Lambda function
Once created, configure a API Gateway trigger.  This will then take you to API Gateway to configure the API.
Deployment Stage: Give it a name
Security: Set as "Open"

Go to the API Gateway console and make the following updates:
* Remove the "ALL" resource method
* Add a new Resource Action for "GET"
* Choose Lambda Function for the Integration type
* Choose the Lambda function

Once completed, Deploy the API and choose the stage noted above.

### 5. Update the index.html code to make the call to the API endpoint
In the index.html file located in the S3 bucket, update xhttp.open function call with the URL to the API Gateway endpoint.  In the line below is the endpoint URL. 
'''
xhttp.open("GET", "https://y2iqw4meh8.execute-api.us-east-1.amazonaws.com/Production/MyServerlessWebsite", true);
'''

The index.html file has a single javascript function called 'myFunction()' as noted below.  This function opens a GET request to the API Endpoint via the URL

In the body of the HTML there is a button defined that calls the 'myFunction()' function when a button is clicked.
		'<h1>Hello <span id="my-demo">Cloud Gurus!</span></h1>
		<button onclick="myFunction()">Click me</button>'


				
[comment]: # (references used in README)
[serverless-website-labs]:../README.md
[Serverless Website Process Flow-Part 1]:../images/Serverless-Website-Acloudguru-ProcessFlow-Part-1
