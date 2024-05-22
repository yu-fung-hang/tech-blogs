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
2. exit without stopping the container: `ctrl+q+p`.

## Scenario 4: re-enter a container
```
docker exec -it your-container-id bash
```

## Scenario 5: export & import as an image
**export**: `docker export your-container-id > your-tar-name.tar`;

**import as an image**: `cat your-tar-name.tar | docker import - a-username/your-image-name:your-tag`

## Scenario 6: commit an image
```
docker commit -m="your commit message" -a="author name" your-container-id your-package-name/your-new-image-name:your-tag
```

## Scenario 7: save logs
```
docker logs containername >& logs/myFile.log
```

## Scenario 8: restart
```
systemctl start docker
```