CloudFormation template for a Jenkins server with automatic backup and recovery using S3.

# Prerequisites
 - Route 53 hosted zone for the desired DNS address (e.g., yourdomain.com)
 - S3 bucket
 - VPC
 - Subnets

 # USAGE
 - Launch the stack via the AWS console, a script, or aws-cli.


 ## AWS CLI

 ```
 aws cloudformation create-stack \
    --template-body file://jenkins.json \
    --stack-name <stackName> \
    --capabilities CAPABILITY_IAM \
    --parameters \
        ParameterKey=SshKey,ParameterValue=<key> \
        ParameterKey=S3Bucket,ParameterValue=<bucket> \
        ParameterKey=VpcId,ParameterValue=<vpc_id> \
        ParameterKey=Subnets,ParameterValue='<subnet_id_1>\,<subnet_id_2>' \
        ParameterKey=AdminSecurityGroup,ParameterValue=<sg_id> \
        ParameterKey=DnsZone,ParameterValue=<zone>
 ```

 ## AWS Console
 - CloudFormation -> Stacks -> Upload template 
