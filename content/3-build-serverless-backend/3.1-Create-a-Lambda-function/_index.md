---
title: "Create a Lambda function for handling requests"
date : "`r Sys.Date()`"
weight : 11
chapter : false
pre : " <b> 3.1 </b> "
---
1. On your local machine, navigate to the *ai-recipe-generator/amplify/data* folder, and create a file named ``bedrock.js``. 
2. Then, update the file with the following code:
The following code defines a request function that constructs the HTTP request to invoke the Claude 3 Sonnet foundation model in Amazon Bedrock. The response function parses the response and returns the generated recipe.
```
export function request(ctx) {
    const { ingredients = [] } = ctx.args;
  
    // Construct the prompt with the provided ingredients
    const prompt = `Suggest a recipe idea using these ingredients: ${ingredients.join(", ")}.`;
  
    // Return the request configuration
    return {
      resourcePath: `/model/anthropic.claude-3-sonnet-20240229-v1:0/invoke`,
      method: "POST",
      params: {
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          anthropic_version: "bedrock-2023-05-31",
          max_tokens: 1000,
          messages: [
            {
              role: "user",
              content: [
                {
                  type: "text",
                  text: `\n\nHuman: ${prompt}\n\nAssistant:`,
                },
              ],
            },
          ],
        }),
      },
    };
  }
  
  export function response(ctx) {
    // Parse the response body
    const parsedBody = JSON.parse(ctx.result.body);
    // Extract the text content from the response
    const res = {
      body: parsedBody.content[0].text,
    };
    // Return the response
    return res;
  }
```
![Bedrock js config](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.3/3.1.png?raw=true?featherlight=false&width=90pc)
