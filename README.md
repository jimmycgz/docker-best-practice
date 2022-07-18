# My Collections for Docker and Docker-compose

## WOrk with docker-compose

Features:

* Auto restart the container if creashes
### HEY, do you still need kubernetes if the docker containers can be automatically restared when crash ?? Should it be simply happy?

* Get image name from Host ENV variables

* Map ports

* Pass Env variables 


```
version: "3"
services:

  mydb-v3:
    image: "${Docker_Hub_URL}/mydb-v3:${DB_VER_TAG}"
    container_name: "stage-db-v3"
    environment:
      - HOSTHOME=$HOME

    ports:
      - "5432:5432"

    restart: always

```

## DOCKER COMPOSE WITH TWO CONTAINERS - FLASK REST API SERVICE CONTAINER AND AN APACHE SERVER CONTAINER
Refer:https://www.bogotobogo.com/DevOps/Docker/Docker-Compose-FlaskREST-Service-Container-and-Apache-Container.php

or: https://github.com/Einsteinish/docker-compose-flask-rest-api-service-container-and-apache-container

## Load Balancing for Docker containers 
## Work with Nginx
https://www.youtube.com/watch?v=HJ9bECmuwKo



## Work with AWS ECS

## Kubernetes AKS EKS GKS
