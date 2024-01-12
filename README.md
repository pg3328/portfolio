# portfolio
The Portfolio Website uses React, HTML, CSS, JS, and the application is launched on AWS using Serverless Architecture. 

# Systems Design

The application utilizes AWS Amplify for hosting. When users submit data through the "Contact Me" section, Ajax calls trigger the API Gateway. The API Gateway then exports this request to a Lambda function, which stores the data in Amazon DynamoDB. Additionally, the Lambda function triggers the Simple Email Service (SES) for sending alert emails. This setup is designed to handle data submission and email notifications within the application efficiently. 




