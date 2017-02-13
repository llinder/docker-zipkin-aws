[![Build Status](https://travis-ci.org/openzipkin/docker-zipkin-aws.svg)](https://travis-ci.org/openzipkin/docker-zipkin-aws)
[![zipkin-aws](https://quay.io/repository/openzipkin/zipkin-aws/status "zipkin-aws")](https://quay.io/repository/openzipkin/zipkin-aws)

# docker-zipkin-aws

This repository contains the Docker build definition and release process for
[openzipkin/zipkin-aws](https://github.com/openzipkin/zipkin-aws).

This layers Amazon Web Services support on the base [zipkin docker image](https://github.com/openzipkin/docker-zipkin).

Currently, this adds SQS Collector support

## Running

Zipkin AWS has no dependencies beyond the optional AWS services that you choose to use.

Running a minimal Zipkin server that consumes from SQS with in-memory storage:

`docker run -p 9411:9411 -e SQS_QUEUE_URL="https://sqs.us-east-1.amazonaws.com/123456789/my-zipkin-queue" -e SQS_AWS_ACCESS_KEY_ID="XqgzeGF3tC7u" -e SQS_AWS_SECRET_ACCESS_KEY="F75uEjHM7ykLzXDJMTHrQ5Jr" openzipkin/zipkin-aws:latest`

See the ui at (docker ip):9411

## Configuration

Configuration is via environment variables, defined by [zipkin-aws](https://github.com/openzipkin/zipkin-aws/blob/master/README.md).

In docker, the following can also be set:

    * `JAVA_OPTS`: Use to set java arguments, such as heap size or trust store location.

### SQS

SQS Configuration variables are detailed [here](https://github.com/openzipkin/zipkin-aws/tree/master/autoconfigure/collector-sqs#configuration).
