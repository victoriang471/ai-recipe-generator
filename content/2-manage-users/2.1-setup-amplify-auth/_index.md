---
title: "Setup Amplify Auth"
date : "`r Sys.Date()`"
weight : 8
chapter : false
pre : " <b> 2.1 </b> "
---
The app uses email as the default login mechanism. When the users sign up, they receive a verification email. In this step, you will customize the verification email that is sent to users.

1. On your local machine, navigate to the *ai-generated-recipes/amplify/auth/resource.ts* file and update it with the following code. Then, **save** the file.
```
import { defineAuth } from "@aws-amplify/backend";

export const auth = defineAuth({
  loginWith: {
    email: {
      verificationEmailStyle: "CODE",
      verificationEmailSubject: "Welcome to the AI-Powered Recipe Generator!",
      verificationEmailBody: (createCode) =>
        `Use this code to confirm your account: ${createCode()}`,
    },
  },
});
```
![Resource Config](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.2/2.1.png?raw=true?featherlight=false&width=90pc)
