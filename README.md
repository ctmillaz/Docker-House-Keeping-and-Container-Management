# Docker-House-Keeping-and-Container-Management


## Docker House Keeping for Containers

### You need to kill running containers before deleting them
```
docker kill $(docker ps -q)
```
### Delete all stopped containers
```
docker rm $(docker ps -a -q)
```
### Docker House Keeping for Images

### Remove a Docker Image
```
docker rmi <image name>
```
### Delete Untagged(dangling) Images **Note** If you pull an image and then pull latest the previous image becomes untagged(dangling)
```
docker rmi $(docker images -q -f dangling=true)
```
### Delete All Images
```
docker rmi $(docker images -q)
```
### Docker House Keeping for Volumes

### Remove all dangling volumes
```
docker volume rm $(docker volume ls -f dangling=true -q)
```
### Remove all stopped containers, volumes and networks not used by atleast one container, all dangling images
```
docker system prune (you can use flags -a which removes all images including dangling and -f for force)
```

------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------

## Docker Container Management

### How to see Docker logs
```
docker logs <container id>
```

### How to tail to output of the console for the docker container
```
docker logs -f <container id>
```

### To build a docker container you must be in the directory of the Dockerfile and run:
```
docker build -t <tag name> .
```

### How to tell docker container to run in the background
```
docker run -d <image name>
```

### How to specify an environment variable for a docker container
```
docker run -e MY_VAR=my_prop <image name>
```

### How do you shell into a docker container
```
docker exec -it <container name> bash
```

### How do you share storage on the host system with a docker container
###  -v <host path>:<container path>
```
docker run -v <my host path>:<the container path> <image name>
```

### How do you map a host port to a container port
###  -p <host port>:<container port>
```
docker run -p 8080:8080 <image name>
```