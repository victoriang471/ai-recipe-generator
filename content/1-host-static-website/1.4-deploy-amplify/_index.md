---
title: "Deploy your app on Amplify"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 1.4 </b> "
---
In this step, you will connect the GitHub repository you just created to AWS Amplify. This will enable you to build and deploy your app on AWS.
1. Sign in to the **AWS Management console** in a new browser window, and open the AWS Amplify console at <https://console.aws.amazon.com/amplify/apps.> 
2. Choose **Create new app**. 
![New app](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.1/1.7.png?raw=true?featherlight=false&width=90pc)
3. On the Start building with Amplify page, for Deploy your app, select **GitHub**, and select **Next**.
![New app with Github](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.1/1.8.png?raw=true?featherlight=false&width=90pc)
4. When prompted, authenticate with GitHub. You will be automatically redirected back to the Amplify console. Choose the repository and main branch you created earlier. Then select **Next**.
![New app with Github](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.1/1.9.png?raw=true?featherlight=false&width=90pc)
5. Leave the default **build settings**, and select **Next**.
![New app with Github](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.1/1.10.png?raw=true?featherlight=false&width=90pc)
6. Review the inputs selected, and choose **Save and deploy**.
![New app with Github](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.1/1.11.png?raw=true?featherlight=false&width=90pc)
AWS Amplify will now build your source code and deploy your app at <https://...amplifyapp.com>, and on every git push your deployment instance will update. It may take up to 5 minutes to deploy your app.
7. Once the build completes, select the **Visit deployed URL** button to see your web app up and running live. 
![New app with Github](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.1/1.12.png?raw=true?featherlight=false&width=90pc)
You have deployed a React application to AWS by integrating with GitHub and using AWS Amplify. With AWS Amplify, you can continuously deploy your application in the Cloud and host it on a globally available CDN.