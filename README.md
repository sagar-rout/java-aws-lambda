# AWS Lambda

AWS Lambda lets you run code without provisioning. https://aws.amazon.com/lambda/

In the sample application, we are receiving sample request ({"name" : "Sagar"}) in src/test/resources/test.json
and sending "hello ${name}"

## AWS SAM

SAM : Serverless Application Model https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html 

1. Install aws cli https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html
2. Install aws SAM https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html

I used pip to install both aws cli and sam.

### Build Step
`mvn package`

### Debugging with Editor : Using Intellij Community edition, remote debugging should work all modern IDE
` mvn clean package && sam local invoke -d 5858 --event src/test/resources/test.json`


Intellij -> Run/debug Configurations -> Add new configuration -> Click on "Remote" option -> Give a name something "aws-sam-lambda" and port <strong>5858</strong>(same port which you provided in previous command)

Set a debug point and Run the application in debug mode.

### Invoke Lambda locally
` mvn clean package && sam local invoke --event src/test/resources/test.json`

Note : SAM uses [template](template.yaml) and creates environment by using docker <strong>lambcli/java8</strong> container.