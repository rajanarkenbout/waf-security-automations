# Summary
This is an extension for SO0006-CloudFront (aws-waf-security-automations) with which you can use a S3 bucket as a source for whitelist automation (Lambda)

# Preparations

### GIT setup
Run this command from the root of this repository to setup the correct remote git repo so you can import the latest aws-waf-security-automations from the AWS Github account.

`$ git config --local include.path ../.gitconfig`

`$ git pull origin aws`

### S3 Bucket creation

The cloudformation template expects the source code (Lambdas) to be stored in a S3 bucket appendend with the region name.

`For example: yourbucketname-ap-southeast-2`

The cloudformation template ALSO expects to copy the contents of the dist directory into a sub directory of the S3 bucket called "aws-waf-security-automations"

`For example: yourbucketname-ap-southeast-2/aws-waf-security-automations/`

### Deployment

`$ cd deployment`

`$ ./build-s3-dist.sh yourbucketname (without the region name!)`

Copy the template files from the dist directory to the following location s3://yourbucketname/

Copy the rest (all directories recursive) to the following location s3://yourbucketname/aws-waf-security-automations/

Create a new stack from CloudFormation in the AWS console and select the available options