---
title: "Style the App UI"
date : "`r Sys.Date()`"
weight : 16
chapter : false
pre : " <b> 5.2 </b> "
---
1. On your local machine, navigate to the *ai-recipe-generator/src/index.css* file, and update it with the following code to center the App UI. Then, **save** the file.
```
:root {
  font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
  line-height: 1.5;
  font-weight: 400;

  color: rgba(255, 255, 255, 0.87);

  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

}

.card {
  padding: 2em;
}

.read-the-docs {
  color: #888;
}

.box:nth-child(3n + 1) {
  grid-column: 1;
}
.box:nth-child(3n + 2) {
  grid-column: 2;
}
.box:nth-child(3n + 3) {
  grid-column: 3;
}
```
![style the ui](https://raw.githubusercontent.com/victoriang471/ai-recipe-generator/main/static/images/p.5/5.2.png?featherlight=false&width=90pc)

2. **Update** the *src/App.css* file with the following code to style the ingredients form. Then, **save** the file.
```
.app-container {

  margin: 0 auto;
  padding: 20px;
  text-align: center;
}

.header-container {
  padding-bottom: 2.5rem;
  margin:  auto;
  text-align: center;

  align-items: center;
  max-width: 48rem;
  
  
}

.main-header {
  font-size: 2.25rem;
  font-weight: bold;
  color: #1a202c;
}

.main-header .highlight {
  color: #2563eb;
}

@media (min-width: 640px) {
  .main-header {
    font-size: 3.75rem;
  }
}

.description {

  font-weight: 500;
  font-size: 1.125rem;
  max-width: 65ch;
  color: #1a202c;
}

.form-container {
  margin-bottom: 20px;
}

.search-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
  align-items: center;
}

.wide-input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.search-button {
  width: 100%; /* Make the button full width */
  max-width: 300px; /* Set a maximum width for the button */
  padding: 10px;
  font-size: 16px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.search-button:hover {
  background-color: #0056b3;
}

.result-container {
  margin-top: 20px;
  transition: height 0.3s ease-out;
  overflow: hidden;
}

.loader-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.result {
  background-color: #f8f9fa;
  border: 1px solid #e9ecef;
  border-radius: 4px;
  padding: 15px;
  white-space: pre-wrap;
  word-wrap: break-word;
  color: black;
  font-weight: bold;
  text-align: left; /* Align text to the left */
}
```
![style the ui](https://github.com/victoriang471/ai-recipe-generator/blob/main/static/images/p.5/5.3.png?raw=true?featherlight=false&width=90pc)
