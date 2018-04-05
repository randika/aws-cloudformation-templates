aws cloudformation create-stack \
   --template-body file://ec2-asg-elb.json \
   --stack-name {AppEnv}-{AppId}-{AppComponentId} \
   --capabilities CAPABILITY_IAM \
   --parameters \
       ParameterKey=KeyName,ParameterValue={KeyName} \
       ParameterKey=VpcId,ParameterValue={vpc_id} \
       ParameterKey=Subnets,ParameterValue='{subnet_id_1}\,{subnet_id_2}' \
       ParameterKey=AppEnv,ParameterValue={AppEnv} \
       ParameterKey=AppId,ParameterValue={AppId} \
       ParameterKey=AppComponentId,ParameterValue={AppComponentId}
