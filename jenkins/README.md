aws-cloudformation-template-jenkins
===
CloudFormation template for a Jenkins server with automatic backup and recovery using S3.

### Prerequisites
 - VPC
 - Subnets (as much as you need)
 - EC2 keypair
 - EC2 Security Group
 - Route 53 hosted zone for the desired DNS address (e.g., yourdomain.com)
 - S3 bucket

### Usage
 - Launch the stack via the AWS console, a script, or aws-cli.


 #### AWS CLI

 ```
 aws cloudformation create-stack \
    --template-body file://jenkins.json \
    --stack-name {AppEnv}-{AppId}-{AppComponent} \
    --capabilities CAPABILITY_IAM \
    --parameters \
        ParameterKey=SshKey,ParameterValue={key} \
        ParameterKey=S3Bucket,ParameterValue={bucket} \
        ParameterKey=VpcId,ParameterValue={vpc_id} \
        ParameterKey=Subnets,ParameterValue='{subnet_id_1}\,{subnet_id_2}' \
        ParameterKey=AdminSecurityGroup,ParameterValue={sg_id} \
        ParameterKey=DnsZone,ParameterValue={zone} \
        ParameterKey=AppEnv,ParameterValue={AppEnv} \
        ParameterKey=AppId,ParameterValue={AppId}
 ```

 #### AWS Console
 - CloudFormation -> Stacks -> Upload template
