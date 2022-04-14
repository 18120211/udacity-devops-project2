# Instruction to run the infras template

1. Create your s3 bucket and upload your web file to it, for me it's `udacity-test-s3-bucket/project2/index.html`. Replace the value in `Infrastructure/role-and-server.yaml`
2. Create your keypair, for me it's `udacity-test-keypair`. Replace the value in `Infrastructure/role-and-server.yaml`
3. Be sure you have permission to create AWS CloudFormation Stack
4. Run this command to create **network** resource
   ```
    aws cloudformation create-stack --stack-name network-stack --template-body file://cfn-template/network.yaml
   ```
5. Wait for step 4 create stack completed then run this command to create **Role** and **Server** resource
   ```
    aws cloudformation create-stack --stack-name role-and-server-stack --template-body file://cfn-template/role-and-server.yaml --capabilities CAPABILITY_NAMED_IAM
   ```
    Notice that `--capabilities CAPABILITY_NAMED_IAM` allow us to deploy IAM policy, role with cloudformation

6. When you finally create two above stacks. Go to the out the EC2 UI dashboard -> LoadBalancer get the DNS name access it from your browser. The result is your reward
   