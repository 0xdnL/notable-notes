---
tags: [serverless]
title: sam
created: '2021-02-08T12:46:40.753Z'
modified: '2023-03-22T08:47:34.947Z'
---

# sam

> `aws serverless application model` extends [[aws cloudformation]] to provider simplified way of defining resources needed to run lambda functions in aws

## install

```sh
brew tap aws/tap && brew install aws-sam-cli
```

## environment

```sh
SAM_CLI_TELEMETRY         # 0
```

## usage

```sh
sam --version

sam init                # download a sample application, interactively
       
sam build               # build your application

sam deploy --guided     # deploy your application


sam local start-api

sam local invoke "HelloWorldFunction" -e events/event.json
```

## see also

- [[aws]]
- [[serverless]]
- [[terraform]]
- [[tcl]]
- [[virtualenv]]
- [docs.aws.amazon.com/serverless-application-model/../serverless-getting-started-hello-world.html](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started-hello-world.html)
- [speaking.brunoamaro.com/yUeFUQ/deployment-automation-for-an-aws-serverless-project-sam-vs-cloudformation-vs-terraform#s73xjwC](https://speaking.brunoamaro.com/yUeFUQ/deployment-automation-for-an-aws-serverless-project-sam-vs-cloudformation-vs-terraform#s73xjwC)
