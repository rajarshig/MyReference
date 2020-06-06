## Install (docker)
[https://hub.docker.com/_/rabbitmq](https://hub.docker.com/_/rabbitmq)
- Rabbitmq server
```
sudo docker run --hostname rabbitmq --name rabbitmq -p 5672:5672 rabbitmq:3
```

- Rabbitmq management portal (view at http://0.0.0.0:15672/ with guest:guest login)
```
sudo docker run --hostname rabbitmq --name rabbitmq -p 15672:15672 rabbitmq:3-management
```