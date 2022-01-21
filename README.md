## serverless microservices ##

    $ npm install
    $ aws ec2 create-key-pair --region us-west-2  --key-name "ssh-key"  |  
    jq -r ".KeyMaterial" > ssh-key.pem
    $ chmod 400 ssh-key.pem

    $ npm run build
    $ cdk bootstrap
    $ cdk synth FargateVpclinkStack
    $ cdk deploy --all

    $ export EC2_IP_ADDRESS=x.x.x.x
    $ ssh -i ssh-key.pem ec2-user@$EC2_IP_ADDRESS
    $ sudo yum install jq -y
    $ export CSV_API_URL=https://xxxxx.execute-api.us-west-2.amazonaws.
    com/api/csv/health
    $ curl -s $CSV_API_URL | jq

    $ cdk destroy --all
    $ aws ec2 delete-key-pair --region us-west-2  --key-name "ssh-key"