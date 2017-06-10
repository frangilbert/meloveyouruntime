---
layout: post
title:  "Serverless and Lambda"
comments: true
categories: [AWS,Lambda,Serverless]
---

I've been working more with serverless projects using stuff like AWS Lambda or Azure Functions. Very handy indeed: easy to deploy and then use. Sometimes though, you want a little more: you need an S3 bucket or want API Gateway in front of the Lambda function. Enter [serverless](https://serverless.com/)!

The Serverless Framework allows for easy deployment of your Lambda and other services by just describing your infrastructure in a serverless.yml file. You can define what API Gateway endpoints you need and which Lambdas they can point to, set up a DynamoDB or S3 bucket with permissions. You can then run 'serverless deploy' from the project root and it'll package everything up in a .serverless folder and upload to AWS, setting up a Cloudformation template and running it so you can then tear down the environment. It's simple and really powerful. If you're doing any work with Lambdas or AWS Functions, I'd recommend looking into serverless.

Below is an very simple yaml file for serverless. You can set the provider (serverless runs on Azure, AWS, IBM OpenWhisk currently), language version of your code. In environment, this would just read a yml file in the 'vars' folder depending on the stage. You can also run {% highlight bash %}serverless deploy --stage testing{% endhighlight %} To change the file being used from "dev" - which is set in the stage setting to "testing". You can exclude files from being packaged up and if you have multiple Lambda functions, you can choose to package them up individually.

At the bottom of the yaml there is an API Gateway endpoint pointing to the Lambda function.

{% highlight yml %}
# For full config options, check the docs:
#    docs.serverless.com
service: middleware
provider:
  name: aws
  runtime: nodejs4.3
  stage: dev
  profile: lambda
  region: us-east-1
  environment: ${file(vars/${self:custom.stage}.yml)}
custom:
  stage: "${opt:stage, self:provider.stage}"

package:
   individually: true
exclude:
  - .gitignore
  - .jshintrc
  - .npmignore

functions:
  myfunction:
    handler: functions/myfunction.handler
    events:
      - http:
          path: someendpoint
          method: post
          cors: true
{% endhighlight %}

 You can even run the Lambda function locally by using [invoke local](https://serverless.com/framework/docs/providers/aws/cli-reference/invoke-local/) {% highlight bash %}serverless invoke local: --function myfunction{% endhighlight %}. This is useful for local development.

 Serverless is a great, powerful way to quickly deploy Lambda based services (or Functions if using Azure) and the best part is, it'll work with your current system just by adding a yaml file. In this short blog post I've given a quick example of how to deploy a simple Lambda & API Gateway endpoint. You can also set up a Dynamo DB instance and many other services in the yaml file.