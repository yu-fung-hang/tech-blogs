# Docker

## Scenario 1: run Ubuntu
```
docker run -it ubuntu bash
```
Define its name (optional):
```
docker run -it --name=a-name ubuntu bash
```

## Scenario 2: list running containers
```
docker ps
```

## Scenario 3: exit

There are two ways of exiting a container:
1. exit and stop the container: enter `exit`;
2. exit without stopping the container: `ctrl+p+q`.