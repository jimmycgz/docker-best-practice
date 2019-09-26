# My Collections for Docker and Docker-compose

## WOrk with docker-compose

Feature List:

* Auto restart the container if creashes

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
## Load Balancing for Docker containers 
## Work with Nginx
https://www.youtube.com/watch?v=HJ9bECmuwKo



## Work with AWS ECS

## Kubernetes AKS EKS GKS
