# ☁️ Serverless Contact Form with API Gateway and Lambda ☁️

Serverless computing is a cloud computing execution model where the cloud provider dynamically manages the allocation of computing resources. You, as the developer, don't have to provision or manage servers. In this activity, a static website application will be deployed using serverless services of AWS, specifically, API Gateway, Lambda, and DynamoDB. The following architecture will be developed:

![architecture](https://github.com/user-attachments/assets/40b19137-337f-4b3c-8fab-8a776f00a3de)

**Disclaimer:** This activity is based on Avinash Reddy's [project](https://www.youtube.com/watch?v=dsH2QC6O3Gg).

## 📋 Requirements
1. Browser (Google Chrome, Microsoft Edge, Opera GX, etc.)
2. AWS account

## 🎯 Objectives
1. Create a Lambda Function for processing form submissions.
2. Create a DynamoDB table to store form data.
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

## Part 2: Create a DynamoDB table to store form data
1. Navigate to `DynamoDB` (Type "DynamoDB" in the console search bar).
2. On the left tab, navigate to `Tables` and click `Create table`.
3. For table name, enter `demo-table`, and under Partition key, enter `email`. 
4. Keep the other settings default and click `Create table`.

## Part 3: Set Up an API Gateway Endpoint to trigger the Lambda function
1. Navigate to `API Gateway` (Type "API Gateway" in the console search bar).
2. Scroll down to find `REST API` and click `Build`.
3. Select `New API` and enter the API name `demo-api`. Keep the API endpoint type to `Regional` and click `Create API`.
4. In the API Resources page, click `Create method`. Under method type, select `GET` in method type, and `Lambda function` for integration type.
5. Turn on `Lambda proxy integration`, then, select the region where you created the Lambda function, and select the corresponding function, which should have the keyword of the name of the function (demo-function).
6. Keep the default timeout and click `Create method`. Then, click `/` in the navigation pane and create another method.
7. Under method type, select `POST` in method type, and repeat the process done before.
8. In the API Resources page, click `Deploy API`. Under stage, select `New stage` and enter `dev` in stage name. Click `Deploy`.
9. In the stages page, copy the `Invoke URL`. Enter the URL in a new tab, it should display the contact form web page.

## Part 4: Test the API Endpoint with a contact form
1. In the web page, enter dummy details and screenshot your entries before clicking `Submit`. 
2. To enter more dummy entries, refresh the page and submit. Make sure to screenshot your entries.
3. In the AWS Console, navigate again to `DynamoDB` > `Tables` and select `demo-table` and go to `Explore items`.
4. Select `demo-table` and the dummy entries should be shown. Screenshot this page.
5. After taking all the required screenshot, delete all created services in Lambda, DynamoDB, and API Gateway.
