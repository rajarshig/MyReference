[https://stackoverflow.com/questions/12341514/tika-how-to-extract-text-from-pdf-text-underlined-highlighted-crossed-out]
[http://tika.apache.org/1.7/examples.html#Picking_different_output_formats]
[http://tika.apache.org/1.18/gettingstarted.html]
[https://github.com/chrismattmann/tika-python]
[https://wiki.apache.org/tika/TikaJAXRS]

## REST Server
[https://wiki.apache.org/tika/TikaJAXRS](https://wiki.apache.org/tika/TikaJAXRS)
git clone https://github.com/apache/tika.git tika-trunk
cd ./tika-trunk/

Installing the Oracle JDK

If you want to install the Oracle JDK, which is the official version distributed by Oracle, you will need to follow a few more steps.

First, add Oracle's PPA, then update your package repository.

    sudo add-apt-repository ppa:webupd8team/java
    sudo apt-get update

sudo apt-get install oracle-java8-installer
https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04

apt-get install maven

mvn install
(install issues:)
mvn clean install -U
mvn dependency::tree
https://stackoverflow.com/questions/13170860/failed-to-execute-goal-org-apache-maven-pluginsmaven-surefire-plugin2-10test

- Run
cd ./tika-server/target/
java -jar tika-server-1.8-SNAPSHOT.jar


##
[https://tika.apache.org/1.10/gettingstarted.html](https://tika.apache.org/1.10/gettingstarted.html)
## Tika REST Server docker image
- [https://github.com/LogicalSpark/docker-tikaserver](https://github.com/LogicalSpark/docker-tikaserver)
- First you need to pull down the build from Dockerhub, which can be done by invoking:
```
sudo docker pull logicalspark/docker-tikaserver
```
- Then to run the container, execute the following command:
```
docker run -d -p 9998:9998 logicalspark/docker-tikaserver
```
Should show like
```
CONTAINER ID        IMAGE                            COMMAND                  CREATED             STATUS              PORTS                    NAMES
7d969c8e356a        logicalspark/docker-tikaserver   "/bin/sh -c 'java -j…"   43 seconds ago      Up 39 seconds       0.0.0.0:9998->9998/tcp   kind_newton
```

## Python wrapper
[https://github.com/chrismattmann/tika-python](https://github.com/chrismattmann/tika-python)
- install
```
pip install tika
```
- Use with TIKA rest api
```
import tika
from tika import parser
parsed = parser.from_file('filename', 'http://0.0.0.0:9998/', xmlContent=True)
```
