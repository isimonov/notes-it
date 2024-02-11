# Remove

Remove all images, containers, volumes `docker system prune -a --volumes`

Remove one image by name or code `docker rmi <image>`

Remove all images `docker rmi $(docker images -qa)`
# Build image and run container

```shell
docker build -t sm-mnp .
docker run --name sm-mnp --publish 8080:8080 -d sm-mnp
docker logs sm-mnp
curl -X GET http://localhost:8080/actuator/info
```
# Images

## Images list

```shell
docker images
docker image ls
docker images -a
docker images -qa
```
# Containers

## Containers list

```shell
docker ps
docker ps -a
```
## Execute cmd inside container

```shell
docker exec <container> <command>
docker exec -it <container> /bin/bash
```
# Volumes

Volumes list `docker volume ls`
 Volume information `docker volume inspect <volume>`
 Volume size `du -sh /var/lib/docker/volumes/<volume>`
All volumes size `du -shc /var/lib/docker/volumes/*`
## Credentials and security

### For a private Nexus repository

```shell
docker login nexusrepo.domain.com:8343 --username <nexusrepo-username> --password <nexusrepo-password>
```
### For not https registries put into /etc/docker/daemon.json and restart docker service

```shell
{ "insecure-registries":["nexusrepo.domain.com:8343"] }
```
# Difference

Ports used last container `docker port $(docker ps -lq)`

Used spase on disk `docker system df`
# Docker Compose

Build images and start containers `docker-compose up -d`

Stop and remove runned docker-compose containers `docker-compose down`

List runned containers (in dir with docker-compose.yml file) `docker-compose ps`

List runned containers with custom name compose.yml file `docker-compose -f compose.yml ps`
# Docker rapid deployment of services

RabbitMQ http://localhost:15672 guest/guest<br>
`docker run -d --hostname local --name rabbit -p 5672:5672 -p 15672:15672 rabbitmq:3-management`

PostgreSQL jdbc:postgresql://localhost:5432/postgres?user=postgres&password=postgres

`docker run -d --name posgres -p 5432:5432 -e POSTGRES_PASSWORD=postgres postgres:alpine`
