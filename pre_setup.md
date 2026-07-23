Install aws cli
install docker 


To use the floci services using docker 

docker run -d --name floci -p 4566:4566 -v /var/run/docker.sock:/var/run/docker.sock floci/floci:latest

C:\Users\Alpha_320>set AWS_ENDPOINT_URL=http://localhost:4566

C:\Users\Alpha_320>set AWS_ACCESS_KEY_ID=test

C:\Users\Alpha_320>set AWS_SECRET_ACCESS_KEY=test

C:\Users\Alpha_320>set AWS_DEFAULT_REGION=us-east-1

Test - 
aws --endpoint-url=http://localhost:4566 s3 mb s3://test-bucket
aws --endpoint-url=http://localhost:4566 s3 ls
aws --endpoint-url=http://localhost:4566 dynamodb list-tables
aws --endpoint-url=http://localhost:4566 lambda list-functions




