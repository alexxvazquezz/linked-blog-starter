---
title: Docker Instructions
authors:
  - Docker
source: 
source_description: 
link: 
created_date: 2024-10-31
tags:
  - code
---

How to work on docker, some commands. 

Stop all containers:
```bash
docker stop $(docker ps -q)
```

List all containers:
```bash
docker ps -q
```

Remove all containers:
```bash
docker rm $(docker ps -a -q)
```

The `docker ps -a q)` lists all IDs of all containers, regardless of being active or not (running or stopped).

Stop and remove on one line:
```bash
docker ps -aq | xargs docker stop | xargs docker rm
```

Forcefully remove a contianer
``` bash
docker rm -f $(docker ps -aq)
```


# Docker Images
Remove docker image:
```bash
docker rm dockerimageId
```

Remove all docker images
```bash
docker rmi $(docker images -q)
```

Optional: Clear all volumes and networks
Remove all volumes:
```bash
docker volume rm $(docker volume ls -q)
```

Remove all networks:
```bash
docker network rm $(docker network ls -q)
```

Confirm deletion:
```bash
docker images
docker ps -a
docker volume ls
docker network ls
```