# localstack-helper-readme
Intent is to document aws cli commands for LocalStack work!

## LocalStack Installation

Resource: https://github.com/localstack/localstack

```Recommend using via docker-compose.yml```
Mac:
```
version: '2.1'

services:
  localstack:
    container_name: "${LOCALSTACK_DOCKER_NAME-localstack_main}"
    image: localstack/localstack
    ports:
      - "4566-4599:4566-4599"
      - "${PORT_WEB_UI-8081}:${PORT_WEB_UI-8080}"
    environment:
      - SERVICES=${SERVICES-s3,kinesis }
      - DEBUG=${DEBUG- }
      - DATA_DIR=${DATA_DIR- }
      - PORT_WEB_UI=${PORT_WEB_UI- }
      - LAMBDA_EXECUTOR=${LAMBDA_EXECUTOR- }
      - KINESIS_ERROR_PROBABILITY=${KINESIS_ERROR_PROBABILITY- }
      - DOCKER_HOST=unix:///var/run/docker.sock
      - HOST_TMP_FOLDER=${TMPDIR}
    volumes:
      - "/private${TMPDIR:-/tmp/localstack}:/tmp/localstack"
      - "/var/run/docker.sock:/var/run/docker.sock"
```
## AwsLocal Installation
```sudo pip install awscli-local```

## Resources

### S3 bucket:
- [x] https://docs.aws.amazon.com/cli/latest/userguide/cli-services-s3-commands.html

- [x] create bucket

```awslocal s3 mb s3://mytestbucket```

- [x] view bucket

``` awslocal s3 ls ```

- [x] copy file to bucket

``` awslocal s3 cp /tmp/mongo.log s3://mytestbucket```

- [x] delete file from bucket

``` awslocal s3 rm s3://mytestbucket/mongo.log ```

- [x] delete bucket

``` awslocal s3 rb s3://mytestbucket```

