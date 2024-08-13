---
title: "Setup Amazon Bedrock Model Access"
date : "`r Sys.Date()`"
weight : 9
chapter : false
pre : " <b> 2.2 </b> "
---
Amazon Bedrock enables users to request access to a variety of Generative AI models. In this tutorial, you will need access to Claude 3 Sonnet from Anthropic.
1. Sign in to the AWS Management console in a new browser window, and open the AWS Amazon Bedrock console at  <https://console.aws.amazon.com/bedrock/.> Verify that you are in the **N. Virginia us-east-1 region**, and choose **Get started**.
![Bedrock request](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.2/2.2.png?raw=true?featherlight=false&width=90pc)
2. In the Foundation models section, choose the Claude model.
![Bedrock request](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.2/2.3.png?raw=true?featherlight=false&width=90pc)
3. Scroll down to the Claude models section, and choose the Claude 3 Sonnet tab, and select Request model access.
{{% notice info %}}
Note: If you already have access to some models, then the button will display Manage model access.
{{% /notice %}}
![Bedrock request](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.2/2.4a.png?raw=true?featherlight=false&width=90pc)
4. In the Base models section, for **Claude 3 Sonnet**, choose **Available to request**, and select **Request model access**.
![Bedrock request](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.2/2.4b.png?raw=true?featherlight=false&width=90pc)
5.  On the Edit model access page, choose **Next**.
![Bedrock request](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.2/2.4c.png?raw=true?featherlight=false&width=90pc)
6.  On the **Review and Submit page**, choose **Submit**.
![Bedrock request](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.2/2.4d.png?raw=true?featherlight=false&width=90pc)

You have configured Amplify for authentication and customized the verification email, and enabled access to Amazon Bedrock and Claude 3 Sonnet.
