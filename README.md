# PollCounter version 2 - Now with Amplify!

A (very) simple Vue application to enable voting across large numbers of users. The voting buttons trigger an API Gateway call to a Lambda function which stores the vote in DynamoDB. The front-end refreshes every 3 seconds.

This code is provided without any warranty. You are responsible for any AWS charges you incur. This is only provided for educational purposes.

- Read more about [AWS Amplify](https://aws-amplify.github.io/docs/js/api). 
- Read the tutorial accompanying this code: https://itnext.io/build-a-voting-website-that-doesnt-crash-part-two-now-with-amplify-9e4746b757e7.

Deploy this app to your AWS account with a single click:

[![amplifybutton](https://oneclick.amplifyapp.com/button.svg)](https://console.aws.amazon.com/amplify/home#/deploy?repo=https://github.com/jbesw/amplify-pollCounter)

The Amplify Console will fork this repo in your GitHub account, and then build and deploy your backend and frontend in a single workflow. Your app will be available at `https://master.appid.amplifyapp.com`.

## Project setup
```
npm install
amplify init
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
