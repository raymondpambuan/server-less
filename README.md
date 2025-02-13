# ☁️ Serverless Contact Form with API Gateway and Lambda ☁️

Serverless computing is a cloud computing execution model where the cloud provider dynamically manages the allocation of computing resources. You, as the developer, don't have to provision or manage servers. In this activity, a static website application will be deployed using serverless services of AWS, specifically, API Gateway, Lambda, and DynamoDB. The following architecture will be developed:

![architecture](https://github.com/user-attachments/assets/40b19137-337f-4b3c-8fab-8a776f00a3de)

**Disclaimer:** This activity is based on Avinash Reddy Thipparthi's [project](https://www.youtube.com/watch?v=dsH2QC6O3Gg) and AWS 2025 UI.

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

![image](https://github.com/user-attachments/assets/2b00c74b-bcff-4727-9c10-7352d2994f5d)

4. Select trusted entity type to `AWS service` and Use case `Lambda`, then click next.
5. In Permission policies, search `basic` and tick the checkbox of `AWSLambdaBasicExecutionRole` policy.

![image](https://github.com/user-attachments/assets/e842893b-610d-4ce0-bbef-2048e5412b50)

6. Once more, in permission policies, search `dynamo` and tick the checkbox of `AmazonDynamoDBFullAccess` policy, then click next.
7. In role name, enter `admin-lambda`, then click `Create role` at the bottom of the page.
8. Now, navigate to `Lambda` (Type "Lambda" in the console search bar). 

![image](https://github.com/user-attachments/assets/9b3dbf56-be60-4867-a2f1-c0af677fb13d)

9. Click `Create function` and enter function name `demofunction`. Under Runtime, select `Python 3.12`, and architecture to `x86_64`.
10. Expand the  `Change default execution role`, then tick `Use an existing role`, and select the recently created (admin-lambda). Afterward, click create function.

![image](https://github.com/user-attachments/assets/335fe3da-d4a7-4413-a4a5-29ee8817b999)

11. In this repository, select the file `demofunction.zip`. Click the download icon on the right-side and save it in your preferred directory.

![image](https://github.com/user-attachments/assets/51112788-911b-422d-a48f-7e835f6dd4f6)

12. In your Lambda `Code` section, click `Upload from`, select `.zip file`. 

![image](https://github.com/user-attachments/assets/8d627c5b-f348-4319-a11d-9545e1398359)

13. Click `Upload` and select downloaded ZIP file, then click `Save`.

![image](https://github.com/user-attachments/assets/1426ac0a-d36a-45f4-84db-8eefae60dfa4)

## Part 2: Create a DynamoDB table to store form data
1. Navigate to `DynamoDB` (Type "DynamoDB" in the console search bar).
2. On the left tab, navigate to `Tables` and click `Create table`.

![image](https://github.com/user-attachments/assets/eaab7fb2-f785-4113-b11c-b1dbc861c5d2)

3. For table name, enter `demotable`, and under Partition key, enter `email`. 

![image](https://github.com/user-attachments/assets/02ba5fd4-ac5b-4f92-b021-b9eb42a413bb)

4. Keep the other settings default and click `Create table` at the bottom. Wait for the status to become `Active` before proceeding.

## Part 3: Set Up an API Gateway Endpoint to trigger the Lambda function
1. Navigate to `API Gateway` (Type "API Gateway" in the console search bar).
2. Scroll down to find `REST API` and click `Build`.

![image](https://github.com/user-attachments/assets/45d043be-cd6f-4826-ae96-dbc964bbd8be)

3. Select `New API` and enter the API name `demoapi`. Keep the API endpoint type to `Regional` and click `Create API`.
4. In the API Resources page, click `Create method`. Under method type, select `GET` in method type, and `Lambda function` for integration type.
5. Turn on `Lambda proxy integration`, then, select the region where you created the Lambda function, and select the corresponding function, which should have the keyword of the name of the function (demo-function).

![image](https://github.com/user-attachments/assets/49389920-2847-468e-8bdc-52fbf4fef0c8)

6. Keep the rest settings at default and click `Create method` at the bottom. Then, click `/` in the navigation pane and create another method.

![image](https://github.com/user-attachments/assets/8be7ff8f-3221-4845-99d8-9222a2ebcd17)

7. Click `Create method`. Under method type, select `POST` in method type, and repeat the process done before.
8. In the API Resources page, click `Deploy API`. Under stage, select `New stage` and enter `dev` in stage name. Click `Deploy`.

![image](https://github.com/user-attachments/assets/f22ef6ed-ed92-460f-be63-3f0cea27611e)

9. In the stages page, copy the `Invoke URL`. Enter the URL in a new tab, it should display the contact form web page.

![image](https://github.com/user-attachments/assets/7bb2d8b5-0c53-4fd3-af14-6342bfa0aa3e)

## Part 4: Test the API Endpoint with a contact form
1. In the web page, enter dummy details and **screenshot** your entries before clicking `Submit`. If the submission was successful, it should display a thank you page.

![image](https://github.com/user-attachments/assets/c175dcbf-039f-4b5e-ba61-19b962b79308)

2. To enter more dummy entries, refresh the page using the address bar. Make sure to **screenshot** your entries.
3. In the AWS Console, navigate again to `DynamoDB` > `Tables` and select `demotable` and click `Explore table items`. If the submission was successful, it should display items. **Screenshot** this page.

![image](https://github.com/user-attachments/assets/a86643b9-1c06-4c5e-9833-aa13ce394a43)

4. Once you are finished with the activity and obtained the required screenshots, delete all created services in Lambda, DynamoDB, and API Gateway to avoid incurring costs.

## Authors
### Activity and Code Materials Prepared by:
- Avinash Reddy Thipparthi ([avizway1](https://github.com/avizway1/aws-projects))
### Learning Material Prepared by:
- Raymond Irwin Pambuan (raymondpambuan)
