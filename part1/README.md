# Part 1

## 1.1: Getting started

- Start 3 containers from image that does not automatically exit, such as nginx, detached.

```shell
$ docker container run -d nginx
$ docker container run -d nginx
$ docker container run -d nginx
```

- Stop 2 of the containers leaving 1 up.

```shell
$ docker container stop cranky_borg 
$ docker container stop angry_wing 
```

- Result

```shell
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                        PORTS     NAMES
7b4aef13f94c   nginx     "/docker-entrypoint.…"   2 minutes ago    Exited (0) 34 seconds ago               cranky_borg
2fb2109dd71c   nginx     "/docker-entrypoint.…"   2 minutes ago    Exited (0) 23 seconds ago               angry_wing
639ed88f5757   nginx     "/docker-entrypoint.…"   3 minutes ago    Up 3 minutes                  80/tcp    gracious_lehman
```

## 1.2: Clean up

- Clean up the containers

```shell
$ docker container stop gracious_lehman
$ docker container prune
```

- Clean up the images 
    
```shell
$ docker image prune -a
```

- Result
    
```shell
$ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

```shell
$ docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
```

## 1.3: Secret message

- Commands

```shell
$ docker run -d --rm -it --name secret-message devopsdockeruh/simple-web-service:ubuntu
$ docker exec -it secret-message bash
$ tail -f ./text.log
```

- Secret Message

```shell
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
```

## 1.4: Missing dependencies

- Method 1

Create container and install curl

```shell   
$ docker run -it --name ubuntu-container ubuntu
```

```
# apt-get update && apt-get install curl -y
```
In another terminal run the shell script 

```shell
$ docker exec -it ubuntu-container sh -c 'while true; do echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website; done'
```
- Method 2

Create container

```shell
$ docker run -it --name ubuntu-container ubuntu sh -c 'while true; do echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website; done'
```

In another terminal , open bash and install curl

```shell
$ docker exec -it ubuntu-container bash
```

```
# apt-get update && apt-get install curl -y
```
Go to the first terminal and provide the Input website.

## 1.5: Sizes of images

- Image size comparison command

```shell
$ docker images
```

- Result

```shell
REPOSITORY                          TAG       IMAGE ID       CREATED       SIZE
devopsdockeruh/simple-web-service   alpine    fd312adc88e0   2 years ago   15.7MB
devopsdockeruh/simple-web-service   ubuntu    4e3362e907d5   2 years ago   83MB
```


## 1.6: Hello Docker Hub

- Command

```shell
$ docker run -it devopsdockeruh/pull_exercise
```

- Secret message

```shell
You found the correct password. Secret message is:
"This is the secret message"
```

## 1.7: Image for script

- See file  [Exercise1.7](Exercise1.7/README.md)

## 1.8: Two line dockerfile

- See file [Exercise1.8](Exercise1.8/README.md)

## 1.9: Volumes

- Commands

```shell
$ touch text.log
$ docker run -v $(pwd)/text.log:/usr/src/app/text.log devopsdockeruh/simple-web-service
```

## 1.10: Ports Open

- Commands

```shell
$ docker run -p 8080:8080 web-server
```

- Result

```
{"message":"You connected to the following path: /","path":"/"}
```