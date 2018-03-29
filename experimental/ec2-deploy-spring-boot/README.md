aws-cloudformation-template-ec2-spring-boot
===
Deploy Spring-boot application to Single EC2 server.  

### Prerequisites
 - VPC
 - Subnet
 - EC2 keypair
 - EC2 Security Group
 - S3 bucket
 - AWS CLI & Access keys


### Step 1: Clone the demo Spring-boot app

```
git clone https://github.com/randika/demo-spring-boot-service.git
```

### Step 1: Build the application and deploy it to a s3 bucket.

```
gradle build
aws s3 cp aws-demo-0.0.1-SNAPSHOT.jar s3://randika-docs/aws-demo-0.0.1-SNAPSHOT.jar
```

### Step 2: Provision the EC2 instance using cloudformation
```
aws cloudformation create-stack \
--stack-name SpringEc2 \
--template-body file://ec2-deploy.json \
--capabilities CAPABILITY_IAM \
--parameters \
ParameterKey=SourceCodeBucket,ParameterValue=randika-docs \
ParameterKey=SubnetId,ParameterValue=subnet-5ee6d871 \
ParameterKey=AMI,ParameterValue=ami-6869aa05 \
ParameterKey=KeyName,ParameterValue=awsdemo \
ParameterKey=InstanceType,ParameterValue=t2.micro \
ParameterKey=BuildJar,ParameterValue=aws-demo-0.0.1-SNAPSHOT.jar
```

### Step 3: Access the application
- Once the stack creation completed, find the EC2 instance public DNS.
- Access the URL http://ec2-xx-xx-xx-xx.compute-1.amazonaws.com:8080 (Make sure to open the port in your Security Group)
