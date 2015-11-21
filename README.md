# About this Repo
This is a Git repo for a customized version of the official Docker image for RabbitMQ, that allows RabbitMQ to be run as a cluster within a Rancher service.

# Usage

1. Refer to [Official RabbitMQ Docker Repository](https://hub.docker.com/_/rabbitmq/) for basic instructions.
1. Set Docker *hostname* to service name, using Rancher's internal DNS FQDN (e.g. rabbit.rancher.internal)
1. Provide Rancher service name to environment variable *RANCHER_SERVICE_NAME*

## Example docker-compose.yml

    rabbit:
      ports:
        - 15672/tcp
      hostname: rabbit.rancher.internal
      environment:
        RANCHER_SERVICE_NAME: rabbit
        RABBITMQ_ERLANG_COOKIE: "RABBITCOOKIE"
      labels:
        io.rancher.container.dns: true
      image: dsvmacdonald/rancher-rabbitmq

## Example rancher-compose.yml

    rabbit:
      scale: 3
