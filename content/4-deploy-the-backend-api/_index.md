---
title: "Deploy the Backend API"
date : "`r Sys.Date()`"
weight : 13
chapter : false
pre : " <b> 4. </b> "
---

## Set up Amplify Data
In this module, you will configure a custom query that will reference the data source and the resolver you defined the previous model to produce a recipe based on a list of ingredients. This query will use a custom type to structure the response from Amazon Bedrock. 
1. On your local machine, navigate to the *ai-recipe-generator/amplify/data/resource.ts* file, and update it with the following code. Then, **save** the file.

The following code defines the askBedrock query that takes an array of strings called ingredients and returns a BedrockResponse. The *.handler(a.handler.custom({ entry: "./bedrock.js", dataSource: "bedrockDS" }))* line sets up a custom handler for this query, defined in *bedrock.js*, using bedrockDS as its data source.
```
import { type ClientSchema, a, defineData } from "@aws-amplify/backend";

const schema = a.schema({
  BedrockResponse: a.customType({
    body: a.string(),
    error: a.string(),
  }),

  askBedrock: a
    .query()
    .arguments({ ingredients: a.string().array() })
    .returns(a.ref("BedrockResponse"))
    .authorization((allow) => [allow.authenticated()])
    .handler(
      a.handler.custom({ entry: "./bedrock.js", dataSource: "bedrockDS" })
    ),
});

export type Schema = ClientSchema<typeof schema>;

export const data = defineData({
  schema,
  authorizationModes: {
    defaultAuthorizationMode: "apiKey",
    apiKeyAuthorizationMode: {
      expiresInDays: 30,
    },
  },
});
```
![resource ts config](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.4/4.1.png?raw=true?featherlight=false&width=90pc)

2. Open a new terminal window, navigate to your apps project folder (*ai-recipe-generator*), and run the following command to deploy cloud resources into an isolated development space so you can iterate fast.
```
npx ampx sandbox
```

3. Once the cloud sandbox has been fully deployed, your terminal will display a confirmation message and the *amplify_outputs.json* file will be generated and added to your project. 
![npx sandbox](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.4/4.2.png?raw=true?featherlight=false&width=90pc)
You have configured a GraphQL API to define a custom query to connect to Amazon Bedrock and generate recipes based on a list of ingredients. 

