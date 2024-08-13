---
title: "Initialize a Github Repository"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 1.2 </b> "
---

In this step, you will create a GitHub repository and commit your code to the repository. You will need a GitHub account to complete this step, if you do not have an account, [sign up here](https://github.com/).

In the Start a new repository section, make the following selections:
For Repository name, enter ``ai-recipe-generator``, and choose the Public radio button.
Then select, **Create a new repository**.

Open a new terminal window, navigate to your projects root folder (ai-recipe-generator), and run the following commands to initialize a git and push of the application to the new GitHub repo:
![Github New Repo](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.1/1.4.png?raw=true?featherlight=false&width=90pc)

{{% notice info %}}
Note: Replace the SSH GitHub URL in the command with your GitHub URL.  
{{% /notice %}}
```
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:<your-username>/ai-recipe-generator.git
git branch -M main
git push -u origin main
```
![Git Push Command](/images/p.1/1.5.png?featherlight=false&width=90pc)
