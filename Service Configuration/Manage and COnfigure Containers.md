```bash 
# list docker images 
sudo docker images

# add your linux user to the docker group to run docker commands without sudo

# search for images 
docker search nginx 

# grab an image from the repository 
docker pull <image-name>

# remove an image from local 
docker rmi ubuntu/nginx:latest

# create a running container
# this command will keep us in the container
docker run nginx 

#run a container in detached mode 
# --detatch option allows it to run in the background 
# --publish routes traffic from local to container <host>:<container>
# --name name your container 
# image ALWAYS goes last, docker will throw away everything else
docker run --detatch --publish 8080:80 --name mywebserver nginx

# see running containers 
docker ps 

# list all containers 
docker ps --all

# stop a container 
docker stop <container-name> 

# remove stopped docker containers
# MUST TSTOP  ALL RUNNING CONTAINERS USING THAT IMAGW TO REMOVE THAT IMAGE
docker rm <container-name>

# Configure container to restart incase of an issue 
# use the --restart option 
docker run -d --restart always --name mywebserver2 nginx

```

## Creating & Building  Dockerfiles 
### creating 
```DOCKERFILE 
FROM nginx 
COPY index.html /usr/share/nginx/html/index.html 
```

### Building
```bash 
docker build --tag <repoName>/<imagwName:version> <directory to dockerfile>

```
