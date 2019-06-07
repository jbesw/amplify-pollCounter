# PollCounter version 2 - Now with Amplify!

A (very) simple Vue application to enable voting across large numbers of users. The voting buttons trigger an API Gateway call to a Lambda function which stores the vote in DynamoDB. The front-end refreshes every 3 seconds.

This code is provided without any warranty. You are responsible for any AWS charges you incur. This is only provided for educational purposes.

Read more about [AWS Amplify](https://aws-amplify.github.io/docs/js/api).

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
