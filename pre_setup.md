1. Install aws cli

2. install docker 


To use the floci services using docker 
>Running first time.
docker run -d --name floci -p 4566:4566 -v /var/run/docker.sock:/var/run/docker.sock floci/floci:latest

The -v flag in Docker is for volume mounting (bind mount).

-v /var/run/docker.sock:/var/run/docker.sock means: map the host’s Docker socket into the container.

This lets the container talk directly to the Docker daemon on your machine, so Floci can start/stop/manage other containers as if it were Docker itself.

👉 Without this mount, Floci wouldn’t be able to orchestrate Docker resources.

> stop running container
`docker stop <id>`

>remove stoped container
`docker rm <id>`

>start again stoped/Exited container
`docker restart <id>` or name

>remove image `docker rmi <image_name>`

C:\Users\Alpha_320>set AWS_ENDPOINT_URL=http://localhost:4566

C:\Users\Alpha_320>set AWS_ACCESS_KEY_ID=test

C:\Users\Alpha_320>set AWS_SECRET_ACCESS_KEY=test

C:\Users\Alpha_320>set AWS_DEFAULT_REGION=us-east-1

Test - 

- `aws --endpoint-url=http://localhost:4566 s3 mb s3://test-bucket`

- `aws --endpoint-url=http://localhost:4566 s3 ls`

- `aws --endpoint-url=http://localhost:4566 dynamodb list-tables`

- `aws --endpoint-url=http://localhost:4566 lambda list-functions`




