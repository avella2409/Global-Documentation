# Docker

## What is docker ?

Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly.

With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker’s methodologies for shipping, testing, and deploying code quickly, you can significantly reduce the delay between writing code and running it in production.

## Advantages of docker

- Package and run an application in a loosely isolated environment called a container
- Containers are lightweight because they don’t need the extra load of a hypervisor, but run directly within the host machine’s kernel
- Isolation and security allow you to run many containers simultaneously on a given host
- Can run Docker containers within host machines that are actually virtual machines
- Easy and rapid app deployment to any cloud
- Scale app by multiplying the number of containers

## Usefull command

Show all running containers

```bash
docker ps
```

Show all containers

```bash
docker ps -a
```

Show all images

```bash
docker image ls
```

Remove image

```bash
docker image rm IMAGE_NAME
```

Run a docker container from an image

- -d -> Dispatch, run in background
- -p -> Publish, map port 80 in the container to port 8080 on the docker host

```bash
docker run -d -p 8080:80 IMAGE:TAG
```

Build a docker image from a Dockerfile

- -t, Name and optionally a tag in the ‘name:tag’ format

```bash
docker build -t NAME:TAG .
```

## What is a Dockerfile ?

Docker can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using `docker build` users can create an automated build that executes several command-line instructions in succession.

## Simple Java Dockerfile

```docker
FROM openjdk:15
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```
