# Simple Java Hello World example

This is based off https://github.com/edwin/hello-world-java-docker/tree/master.

# Building/starting

You should be able to control containers using docker compose, this will pull/build the respective
containers if they do not already exist.

```bash
docker compose up
```

# Testing

```bash
curl -s http://localhost:8080/ | jq
```
