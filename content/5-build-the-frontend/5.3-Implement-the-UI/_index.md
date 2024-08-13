---
title: "Implement the  UI"
date : "`r Sys.Date()`"
weight : 17
chapter : false
pre : " <b> 5.3 </b> "
---
1. On your local machine, navigate to the ai-recipe-generator/src/main.tsx file, and update it with the following code. Then, save the file.
```
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";
import "./index.css";
import { Authenticator } from "@aws-amplify/ui-react";

ReactDOM.createRoot(document.getElementById("root")!).render(
  <React.StrictMode>
    <Authenticator>
      <App />
    </Authenticator>
  </React.StrictMode>
);
```
The code will use the Amplify Authenticator component to scaffold out an entire user authentication flow allowing users to sign up, sign in, reset their password, and confirm sign-in for multifactor authentication (MFA).
![implement the ui](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.5/5.4.png?raw=true?featherlight=false&width=90pc)

2. Open the *ai-recipe-generator/src/App.tsx* file, and update it with the following code. Then, **save** the file.

The code starts by configuring the Amplify library with the client configuration file *(amplify_outputs.json)*. It then generates a data client using the *generateClient()* function. The app presents a form to users for submitting a list of ingredients. Once submitted, it will use the data client to pass the list to the *askBedrock query* and retrieve the generated recipe then display it to the user.
```
import { FormEvent, useState } from "react";
import { Loader, Placeholder } from "@aws-amplify/ui-react";
import "./App.css";
import { Amplify } from "aws-amplify";
import { Schema } from "../amplify/data/resource";
import { generateClient } from "aws-amplify/data";
import outputs from "../amplify_outputs.json";


import "@aws-amplify/ui-react/styles.css";

Amplify.configure(outputs);

const amplifyClient = generateClient<Schema>({
  authMode: "userPool",
});

function App() {
  const [result, setResult] = useState<string>("");
  const [loading, setLoading] = useState(false);

  const onSubmit = async (event: FormEvent<HTMLFormElement>) => {
    event.preventDefault();
    setLoading(true);

    try {
      const formData = new FormData(event.currentTarget);
      
      const { data, errors } = await amplifyClient.queries.askBedrock({
        ingredients: [formData.get("ingredients")?.toString() || ""],
      });

      if (!errors) {
        setResult(data?.body || "No data returned");
      } else {
        console.log(errors);
      }

  
    } catch (e) {
      alert(`An error occurred: ${e}`);
    } finally {
      setLoading(false);
    }
  };

  return (
    <div className="app-container">
      <div className="header-container">
        <h1 className="main-header">
          Meet Your Personal
          <br />
          <span className="highlight">Recipe AI</span>
        </h1>
        <p className="description">
          Simply type a few ingredients using the format ingredient1,
          ingredient2, etc., and Recipe AI will generate an all-new recipe on
          demand...
        </p>
      </div>
      <form onSubmit={onSubmit} className="form-container">
        <div className="search-container">
          <input
            type="text"
            className="wide-input"
            id="ingredients"
            name="ingredients"
            placeholder="Ingredient1, Ingredient2, Ingredient3,...etc"
          />
          <button type="submit" className="search-button">
            Generate
          </button>
        </div>
      </form>
      <div className="result-container">
        {loading ? (
          <div className="loader-container">
            <p>Loading...</p>
            <Loader size="large" />
            <Placeholder size="large" />
            <Placeholder size="large" />
            <Placeholder size="large" />
          </div>
        ) : (
          result && <p className="result">{result}</p>
        )}
      </div>
    </div>
  );
}

export default App;
```
3. Open a new terminal window, navigate to your projects root directory *(ai-recipe-generator)*, and **run** the following command to launch the app:  
```
npm run dev
```
4. **Select** the **Local host link** to open the Vite + React application.
![implement the ui](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.5/5.6a.png?raw=true?featherlight=false&width=90pc)

5. Choose the **Create Account tab**, and use the authentication flow to create a new user by entering your *email address* and a *password*. Then, choose **Create Account**.
6. You will get a verification code sent to your email. Enter the **verification code** to log in to the app.
![implement the ui](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.5/5.7.png?raw=true?featherlight=false&width=90pc)
7. When signed in, you can start **inputting ingredients** and **generating recipes**. 
![implement the ui](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.5/5.8.png?raw=true?featherlight=false&width=90pc)
8.  In the open terminal window, run the following command to push the changes to GitHub: 
```
git add .
git commit -m 'connect to bedrock'
git push origin main
```
9. Sign in to the AWS Management console in a new browser window, and open the AWS Amplify console at <https://console.aws.amazon.com/amplify/apps>.

10. AWS Amplify automatically builds your source code and deployed your app at <https://...amplifyapp.com>, and on every git push your deployment instance will update. Select the **Visit deployed URL** button to see your web app up and running live.

You have now connected your app to the Amplify backend and built a frontend to generate a recipe based on a list of ingredients submitted by the user.






