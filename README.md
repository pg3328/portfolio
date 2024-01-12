# Portfolio Website

## Overview

This repository contains the source code for my personal portfolio website. The website is built using HTML, CSS, and Javascript for the front end, and the serverless architecture on AWS is utilized for deployment. 

## Technologies Used

- **HTML/CSS/JS:** Standard web development technologies are employed to create a visually appealing and interactive user experience.

- **AWS (Amazon Web Services):** The application is deployed on AWS using a serverless architecture, leveraging services such as AWS Lambda, API Gateway, and DynamoDB.


## Deployment

The portfolio website is deployed using a serverless architecture on AWS. The deployment utilizes AWS Amplify for hosting. When users submit data through the "Contact Me" section, Ajax calls trigger the API Gateway. The API Gateway then exports this request to a Lambda function, which stores the data in Amazon DynamoDB. Additionally, the Lambda function triggers the Simple Email Service (SES) for sending alert emails. This setup is designed to handle data submission and email notifications within the application efficiently.

## How to Run Locally

To run the project locally, follow these steps:
1. Clone the repository or download the zip file.
2. Ensure that you have editor such as vs code to make the changes.
3. Create backend architecture on with Lambda, API Gateway , Dynamo DB, and SES.
4. Use the below code under lambda with nodejs 16. x.
```
 import { SESClient, SendEmailCommand } from "@aws-sdk/client-ses";
const ses = new SESClient({ region: "us-east-1" });

export const handler = async (event) => {
  const command = new SendEmailCommand({
    Destination: {
      ToAddresses: ["Your email"],
    },
    Message: {
      Body: {
        Text: {
          Data: "Hi Pradeep,\nSomeone is trying to contact you. Please find their details below:\nname: " + event.name + '\nemail: ' + event.email + '\ndesc: ' + event.desc,
          Charset: 'UTF-8'
        },
      },

      Subject: { Data: "Website Referral from " + event.name },
    },
    Source: "Source email",
  });

  try {
    let response = await ses.send(command);
    // process data.
    console.log(response);
    return "success";
  } catch (error) {
    return "error";
    // error handling.
  }
};
```

5. Ensure that both the source and destination emails are verified in the SES Sandbox.

## Additional Information

Feel free to download and use the above content for your project. 





