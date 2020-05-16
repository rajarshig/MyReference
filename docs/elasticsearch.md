## Install
-
Reference
[https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started-install.html](https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started-install.html)
```
curl -L -O https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.6.2-linux-x86_64.tar.gz
tar -xvf elasticsearch-7.6.2-linux-x86_64.tar.gz
cd elasticsearch-7.6.2/bin
./elasticsearch
```

## Configure
- Test if running
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-elasticsearch-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-elasticsearch-on-ubuntu-16-04)
```
curl -X GET 'http://localhost:9200'
```
