# Building an End-to-End-Web-app-with-AWS
## Project Overview
The cloud is ideal for hosting static websites that require no server-side processing.<br>
In this project, I developed an end-to-end web application using various AWS services. <br>
Firstly i created and hosted a simple web Application with Amplify, this web app is written in HTML and CSS for the landing page and python to perform calculations.<br>
Next , I set up an API endpoint using AWS API Gateway to facilitate data submission for calculations. This endpoint triggers a Lambda function responsible for performing the calculations.  <br>
IAM services were utilized to configure permissions for the Lambda function, allowing it to write results to a DynamoDB database.

## Architecture

![scrren1](https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/9319b540-b77a-435e-acb7-93be25429e43)
## The Web Application
Our web app consists of a simple user interface that calculates the power of a number.
The user specifies the base number and its exponent and get the result displayed in an alert message .

![web app](https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/269360c5-8f00-41b9-8da8-3f37033c55db)

## AWS Amplify
<div style="display: flex; justify-content: center;">
<img src="https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/753a0456-4f6a-40d3-ad74-73cab1b8d799" alt="Example Image" width="100" height="100">
</div>
AWS Amplify is a set of tools and services offered by Amazon Web Services (AWS) to help developers build scalable and full-stack web and mobile applications.
We used AWS Amplify in our project to host the web app.<br>
You can choose to drag and drop the zip file of your app or to get it from An S3 bucket or any url. <br><br>

![step2](https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/3e623bbf-cbbc-4072-bbe0-01c90b02ef30)
<br><br>
Once the upload is finished , you have your app deployed and ready to go ! 
<br><br>
![step1](https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/651d1e96-8fc6-443e-b6eb-2b43e6542099)

## Amazon API Gateway

<div style="display: flex; justify-content: center;">
<img src="https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/8413df08-3110-4c82-b48f-6764e620bd81" alt="Example Image" width="100" height="100">
</div>
Now that we have our app deployed and accessible to the users. Once they fill out the input boxes the data collected will be sent to the backend for calculations.<br>
For that we need to set up an api endpoint to which we send the data for processing . We have set up a post request using the Amazon API Gateway service .<br>
<b> Amazon API Gateway  </b> 
is a managed service provided by AWS that enables developers to create, publish, maintain, monitor, and secure APIs at any scale. <br>

AWS offers you the possibility to choose the type of API you want to create : HTTP,REST,Websocket ...   <br><br>
In our case,we used REST API to send a POST request in which we're going to send our data.<br><br>



![step3](https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/7dcf1b42-8c93-451e-9dd8-5d1f573b7e1e)
You can check your created APIs :<br> <br>
![step4](https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/e0ac64a3-1e48-4fd8-bd28-33e51b44ba41)


## AWS Lambda
<div style="display: flex; justify-content: center;">
<img src="https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/c9170105-10b2-48ef-a037-f417605663f3" alt="Example Image" width="100" height="100">
</div>
Now that we have our API set up, we need a way to perform our calculations.<br>
<b> AWS lambda </b>, a serverless computing service provided by Amazon Web Services (AWS) that allows you to run code without provisioning or managing servers.<br>
AWS offers you the possibility to write your lambda function in different programming languages : Python, javascript , C# , ruby ... and for that you can choose the runtime environment on which you want your code to run.<br> <br>

![lambdafn](https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/9c5f218d-3d4d-4319-ac72-78e860a0701c) 
<br> <br>
For our app , we will be using a python script that will run after triggering the Lambda function by the API call.
In this code we perform the calculations and return the result that we store in DynamoDB. 
<br> <br>
![fnCode](https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/b230a1b5-7a62-488c-b662-2ed08a4fe215)

## Amazon DynamoDB
<div style="display: flex; justify-content: center;">
<img src="https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/ccd86328-28a4-468f-b5b8-37df188fd559" alt="Example Image" width="100" height="100">
</div>
To store the results of calculations , we are going to use DynamoDB.<br>
<b>DynamoDB </b> is Amazon Web Services's fully managed NoSQL database service. It's designed for applications that need low-latency data access at any scale.<br> 
We created our table in which we're going to store the data . <br> <br>

![dynamo](https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/16b8b7f3-54eb-4934-8086-65f8160bbbb7) 
<br>

## AWS IAM (Identity and Access Management)
<div style="display: flex; justify-content: center;">
    <img src="https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/6690ba76-44fd-40b6-b00f-9674d7d4bf4f" width="100" height="100">
</div>


In order to AWS Lambda to be able to write into the Database , we have to ensure it has the right permissions.<br>
<b>IAM </b> stands for <b> Identity and Access Management</b>. It's a crucial service provided by AWS that helps you manage access to AWS services and resources securely. We have specified the permissions for the AWS Lambda to be able to get, update ,delete, run query or scan DynamoDB.<br>
<br>

![policy](https://github.com/Amanyft/End-to-end-Web-app-with-AWS/assets/80603078/be87622f-a4a0-42f8-9cde-2c4cd5aca7d8)




