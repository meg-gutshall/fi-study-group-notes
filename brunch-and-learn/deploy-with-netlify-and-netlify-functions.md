# Deploy with Netlify & Netlify Functions

> **Beth Schofield on 03/28/20**

* Can use continuous deployment  from GitHub
* `.ENV` works for the frontend as well
  * Be sure to add `*.env` to the `.gitignore` file
  * Then in the `.env` file, preface the variable with `REACT_APP_VARNAME`
  * Access in the app by typing `process.env.REACT_APP_VARNAME`
* Look into Jets: [https://blog.boltops.com/2018/12/21/jets-afterburner-serverless-rails-on-aws-lambda-in-5-minutes](https://blog.boltops.com/2018/12/21/jets-afterburner-serverless-rails-on-aws-lambda-in-5-minutes)
* Look into FaunaDB, a serverless database
* A controlled form flow is when you explicitly set what the values of the form will be using `this`
  * You store the form values in one part of the code and add an `onChange` event listener to the form itself
* Remember to use `preventDefault()` for events when appropriate
  * For a `submit` event, the default is to refresh the page

