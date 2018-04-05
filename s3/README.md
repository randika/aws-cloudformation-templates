```
aws cloudformation create-stack \
   --template-body file://s3.json \
   --stack-name {AppEnv}-{AppId}-{AppComponentId} \
   --capabilities CAPABILITY_IAM
```
