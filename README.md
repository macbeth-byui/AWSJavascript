1. Install [webpack](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/webpack.html).  V3 of AWS allows for module architecture which will allow us to use AWS directly in our javascript without using Node.

```
npm install --save-dev webpack
npm install --save-dev path-browserify
npm install --save-dev webpack-cli
```

2. Create `webpack.config.js`.  The link above has a sample one.  I changed the `entry` to be `aws_test.js` and I changed the `output` to be `aws_test_browser.js`

3. Add the following to `package.json`:

```
  "scripts": {
    "build" : "webpack"
  },
  "dependencies": {
      "@aws-sdk/client-cognito-identity": "^3.32.0",
      "@aws-sdk/credential-provider-cognito-identity": "^3.32.0"
  },
```

4. Run `npm install` to automatically install the new dependencies.

5. Write a simple `aws_test.js`.  In this example, it will just import in the AWS libraries, display Hello World to the console and then also display info about the AWS library to the console.  

6. Run `npm run build` to generate `aws_test_browser.js` from `aws_test.js`

7. Created a simple `test.html` that includes the `aws_test_browser.js`.  Look for the output in the console (press F12 in chrome for windows).

8. Any additional changes to `aws_test.js` will require me to run `npm run build` again.  