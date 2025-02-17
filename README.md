# What is Docker?
Docker is an open source containerization platform
Enables developers to package applications into containers

# What is Docker container?
A Docker container is a lightweight, portable, and isolated environment that allows you to run applications consistently across different computing environments

# What is Docker image
* Docker Image – File that defines what’s inside a container (OS, app, dependencies,command to execute).

# Docker Architecture & components

* Docker Engine 
 * Docker Server
 * Docker API
 * Docker CLI
 * Container Runtime (pulling images and managing container lifecycle)
 * Volumes
 * Network
 * Build Images

# Docker Commands 

* docker images -> list all images available
* docker pull -> fetch image
* docker run -> creates and start container in attached mode (pulls and starts container)
* docker run -d -> with -d flar starts container in detached mode
* docker stop <CONTAINER_ID>
* docker start <CONTAINER_ID>
* docker ps -> list running containers
* docker ps -a -> list all running and stoped contaiers 
* docker run -p<HOST_PORT>:<CONTAINER_PORT> (You can bind ports with -p)
* docker run --name (You can name containers with --name)
* docker logs <CONTAINER_ID>(Show log)
* docker logs <CONTAINER_NAME> (Show log)
* docker exec -it <CONTAINER_ID> sh
* docker exec -u 0 -it <CONTAINER_ID> sh (with -u 0 flag enter container as a root)
* docker network ls (check existing networks)
* docker network create (create new network)
* docker build -t <IMG_NAME>:<VERSION_TAG> . (build image)
* docker rm <CONTAINER_ID> (Delete container)
* docker rmi <IMAGE_ID> (Delete image)


### Docker Compose 
Docker Compose is a tool for defining and running multiple docker containers

* Create docker-compose.yaml file to configure your application's services
* It's help easier to maintain and update configuration

### Dockerfile
Dockerfile it's a blueprint for building images
Dockerfile is used in CI/CD to build the Docker image artifact, which later will be pushed to Docker repo

``` Dockerfile
# Use official Node.js base image
FROM node:20-alpine

# Set environment variables
ENV MONGO_DB_USERNAME=admin \
    MONGO_DB_PWD=password

# Create directory inside container
RUN mkdir -p /home/app

# Copy package files
COPY ./app /home/app

# set default dir so that next commands executes in /home/app dir
WORKDIR /home/app

# will execute npm install in /home/app because of WORKDIR
RUN npm install

# no need for /home/app/server.js because of WORKDIR
CMD ["node", "server.js"]

```

Docker image can then be pushed to multiple remote servers or pulled locally for development and
testing etc

# Best practices:
* Use official Docker images as Base image
* Use specific image version to avoid breaking app
* Only add as much as you need to the image and start with the smallest image
* Write cleaner and more maintainable Dockerfiles
* Use .dockerignore to exclude files and folders
* Do not use root user
* Use docker scan ensures your container images don’t have known vulnerabilities
