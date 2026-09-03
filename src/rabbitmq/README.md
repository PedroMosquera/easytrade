# OTel Benchmark AppRabbitmq

RabbitMQ service along with its initialization.

## Technologies used

- Docker
- RabbitMQ

## Local build instructions

```bash
# default rabbitmq port is 15672

docker build -t otel-benchmark-apprabbitmq .
docker run -d --name rabbitmq otel-benchmark-apprabbitmq
```
