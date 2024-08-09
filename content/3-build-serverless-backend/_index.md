---
title: "Build a Serverless Backend"
date : "`r Sys.Date()`"
weight : 10
chapter : false
pre : " <b> 3. </b> "
---
#### Overview
In this module, you will configure a serverless function using **AWS Amplify** and **AWS Lambda**. This function takes an input parameter i.e. ingredients to generate a prompt. It then sends this prompt to **Amazon Bedrock** via an *HTTP POST* request to the **Claude 3 Sonnet** model. The body of the request includes the prompt string within a messages array.

#### Main content
3.1 [Create a Lambda function for handling requests](3.1-Create-a-Lambda-function)

3.2 [Add Amazon Bedrock as a data sources](3.2-Add-Amazon-Bedrock)