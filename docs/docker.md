# Install
## Install using the repository
Before you install Docker CE for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

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
docker ps -aq -f status=exited
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

## Push in dockerhub
- 
```
docker tag project:latest newrepo:tagname
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
docker container ls
```

## Create docker image
- Install docker compose
```
sudo apt-get install docker-compose
```
- Create a folder where you want to place the project & create docker-compose.yml file in there




