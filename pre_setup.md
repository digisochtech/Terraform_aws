# AWS floci setup for Terraform 
## 1. Install aws cli

## 2. install docker 

### Configure aws cli in command prompt :

`aws configure`
```
AWS Access Key ID [None]: test
AWS Secret Access Key [None]: test
Default region name [None]: us-east-1
Default output format [None]: json
```
### set the endpoint:
set --endpoint-url=http://localhost:4566

### Create docker compose file
docker-compose.yml

```
services:
  localstack:
    container_name: localstack-main
    image: localstack/localstack:latest
    ports:
      - "127.0.0.1:4566:4566"            # LocalStack Edge Proxy
      - "127.0.0.1:4510-4559:4510-4559"  # External service port range
    environment:
      - DEBUG=1
      - DOCKER_HOST=unix:///var/run/docker.sock
    volumes:
      - "./localstack_data:/var/lib/localstack"
      - "//var/run/docker.sock:/var/run/docker.sock" # Double slash is required for Git Bash/Windows compatibility
```

### Run floci
in the same path run command `docker compose up -d`

or you can run below command as well.

`docker run -d --name floci -p 4566:4566 -v /var/run/docker.sock:/var/run/docker.sock floci/floci:latest`

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



Test - 

- `aws s3 mb s3://test-bucket`

- `aws s3 ls`

- `aws dynamodb list-tables`

- `aws lambda list-functions`




