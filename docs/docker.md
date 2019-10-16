# About
## Dockerfile
The Dockerfile defines an application’s image content via one or more build commands that configure that image. Once built, you can run the image in a container. 
Reference:
[https://docs.docker.com/engine/reference/builder/](https://docs.docker.com/engine/reference/builder/)

## Docker-Compose
The docker-compose.yml file describes the services that make your app. In this example those services are a web server and database. The compose file also describes which Docker images these services use, how they link together, any volumes they might need mounted inside the containers. Finally, the docker-compose.yml file describes which ports these services expose. 


# Install
## Install using the repository
Before you install Docker CE for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.
Reference:
[https://docs.docker.com/compose/compose-file/](https://docs.docker.com/compose/compose-file/)


### Set up the repository
- Update the apt package index:

`sudo apt-get update`

- Install packages to allow apt to use a repository over HTTPS:

```
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```

-  Add Docker’s official GPG key:

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
Verify that you now have the key with the fingerprint

```
sudo apt-key fingerprint 0EBFCD88
```

- Use the following command to set up the stable repository.
    
```
sudo add-apt-repository \
"deb [arch=amd64] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) \
stable"
```

### Install Docker CE
- Update the apt package index & install the latest version of Docker CE

```
apt-get update
apt-get install docker-ce
```

### Test Docker Installation
- Run the following command to test docker installation

```
sudo docker run hello-world
```

Console output for successful install

```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
9db2ca6ccae0: Pull complete 
Digest: sha256:4b8ff392a12ed9ea17784bd3c9a8b1fa3299cac44aca35a85c90c5e3c7afacdc
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
1. The Docker client contacted the Docker daemon.
2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
(amd64)
3. The Docker daemon created a new container from that image which runs the
executable that produces the output you are currently reading.
4. The Docker daemon streamed that output to the Docker client, which sent it
to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
$ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
https://hub.docker.com/

For more examples and ideas, visit:
https://docs.docker.com/engine/userguide/
 
```
## Commands
- View info
```
docker info
```
- List running containers
```
docker container ls
```
- Stop container 
[https://docs.docker.com/engine/reference/commandline/stop/](https://docs.docker.com/engine/reference/commandline/stop/)
```
docker stop [container id]
```
- Check exited containers
```
docker ps -aq -f status=exited # show only ids
docker ps -f status=exited
```

- Remove container
```
docker container rm [container id]
```


- Start docker
```
docker-compose up -d
```
- Check version
```
docker version
```
- View docker images with size
```
docker images
``` 
- Remove images
```
docker rmi [image id]
```




## Pull docker images
- sudo docker login
- add your user to docker group 
```
usermod -aG docker $USER
```
- 
```
sudo docker pull logicalspark/docker-tikaserver
```
- Run
```
docker run -d -p 9998:9998 logicalspark/docker-tikaserver
```
- Check with 
```
docker container ls --all
```

## Create docker image
- Install docker compose
```
sudo apt-get install docker-compose
```
- Create a folder where you want to place the project & create Dockerfile file in there
- Sample Dockerfile
- Build image (Django sample)
```
FROM python:3.6.7-alpine
ENV PYTHONUNBUFFERED 1
RUN apk update
# for numpy etc related dependencies
RUN apk add make automake gcc g++ subversion python3-dev
# for postgres dependency 
RUN apk add postgresql-dev gcc python3-dev musl-dev
RUN pip install psycopg2
RUN mkdir /code
WORKDIR /code
ADD requirements.txt /code/
RUN pip install -r requirements.txt
ADD ./ /code/
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```
- Build an image from Dockerfile
[https://docs.docker.com/engine/reference/commandline/build/](https://docs.docker.com/engine/reference/commandline/build/)
```
docker build -t [proj-tagname] .
```
- Run Container from docker image. Docker runs processes in isolated containers. A container is a process which runs on a host. The host may be local or remote. When an operator executes docker run, the container process that runs is isolated in that it has its own file system, its own networking, and its own isolated process tree separate from the host.
[https://docs.docker.com/engine/reference/run/](https://docs.docker.com/engine/reference/run/)
```
run -p 8000:8000 --name apai_portal [imagename]
```

## Use AWS ECR(Elastic Container Registry)
- Create repository in AWS ECR, then follow instruction like below
-
```
$(aws ecr get-login --no-include-email --region us-west-2)
```
- 
```
docker tag apai_portal:latest 032809623502.dkr.ecr.us-west-2.amazonaws.com/apai_portal:latest
```
-
```
docker push 032809623502.dkr.ecr.us-west-2.amazonaws.com/apai_portal:latest
```



