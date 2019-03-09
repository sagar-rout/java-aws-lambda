# AWS Lambda

AWS Lambda lets you run code without provisioning. https://aws.amazon.com/lambda/

In the sample application, we are receiving sample request ({"name" : "Sagar"}) in src/test/resources/test.json
and sending "hello ${name}"

## Test locally using AWS SAM

SAM : Serverless Application Model https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html 

1. Install aws cli https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html
2. Install aws SAM https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html

I used pip to install both aws cli and sam.

### Build Step
`mvn package`

### test
` mvn clean package && sam local invoke --event src/test/resources/test.json`

Note : SAM uses [template](template.yaml) and creates environment by using docker <strong>lambcli/java8</strong> container.

FYI : https://stackoverflow.com/questions/45633822/parse-json-error-with-java-and-aws-lambda-function