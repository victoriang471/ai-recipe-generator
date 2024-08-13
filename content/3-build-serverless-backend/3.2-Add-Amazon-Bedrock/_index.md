---
title: "Add Amazon Bedrock as a data source"
date : "`r Sys.Date()`"
weight : 12
chapter : false
pre : " <b> 3.2 </b> "
---
1. Update the amplify/backend.ts file with the following code. Then, save the file.
The code adds an HTTP data source for Amazon Bedrock to your API and grant it permissions to invoke the Claude model.
```
import { defineBackend } from "@aws-amplify/backend";
import { data } from "./data/resource";
import { PolicyStatement } from "aws-cdk-lib/aws-iam";
import { auth } from "./auth/resource";

const backend = defineBackend({
  auth,
  data,
});

const bedrockDataSource = backend.data.resources.graphqlApi.addHttpDataSource(
  "bedrockDS",
  "https://bedrock-runtime.us- east-1.amazonaws.com",
  {
    authorizationConfig: {
      signingRegion: "us-east-1",
      signingServiceName: "bedrock",
    },
  }
);

bedrockDataSource.grantPrincipal.addToPrincipalPolicy(
  new PolicyStatement({
    resources: [
      "arn:aws:bedrock:us- east-1::foundation-model/anthropic.claude-3-sonnet-20240229-v1:0",
    ],
    actions: ["bedrock:InvokeModel"],
    
  })
);
```
You have defined a Lambda function using Amplify, and added Amazon Bedrock as an HTTP data source.

![backend ts config](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.3/3.3.png?raw=true?featherlight=false&width=90pc)
