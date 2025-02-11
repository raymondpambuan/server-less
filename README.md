# ☁️ Serverless Contact Form with API Gateway and Lambda ☁️

Serverless computing is a cloud computing execution model where the cloud provider dynamically manages the allocation of computing resources. You, as the developer, don't have to provision or manage servers. In this activity, a static website application will be deployed using serverless services of AWS, specifically, API Gateway, Lambda, and DynamoDB. The following architecture will be developed:

![architecture](https://github.com/user-attachments/assets/40b19137-337f-4b3c-8fab-8a776f00a3de)

**Disclaimer:** This activity is based on Avinash Reddy's [project](https://www.youtube.com/watch?v=dsH2QC6O3Gg).

## 📋 Requirements
1. Browser (Google Chrome, Microsoft Edge, Opera GX, etc.)
2. AWS account

## 🎯 Objectives
1. Create a Lambda Function for processing form submissions.
2. Connect Lambda to DynamoDB to store form data.
3. Set Up an API Gateway Endpoint to trigger the Lambda function.
5. Test the API Endpoint with a contact form.

## Part 1: Create a Lambda Function for processing form submissions
1. Log in to your AWS Console.
2. Navigate to `IAM` (Type "IAM" in the search bar).
3. On the left tab, navigate to `Roles` and click the `Create role` button.
4. Select trusted entity type to `AWS service` and Use case `Lambda`, then click next.
5. In Permission policies, search `basic` and tick the checkbox of `AWSLambdaBasicExecutionRole` policy.
6. In Permission policies, search `dynamo` and tick the checkbox of `AmazonDynamoDBFullAccess` policy, then click next.
7. In role name, enter `admin-lambda`, then click `Create role`.
8. Now, navigate to `Lambda` (Type "Lambda" in the console search bar).
9. Click `Create function` and enter function name `demo-function`. Under Runtime, select `Python 3.12`.
10. Expand the default execution role and select the existing role recently created (admin-lambda) then click create function.
11. In this repository, click ` < > Code ` and `Download ZIP`. Name it `demo-function` and save it in your preferred directory.
12. In your Lambda function, click `Upload from`, select `.zip file`, and upload the downloaded ZIP file.
13. In the navigation tab, select `README.md` and delete it.
