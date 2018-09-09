[https://stackoverflow.com/questions/12341514/tika-how-to-extract-text-from-pdf-text-underlined-highlighted-crossed-out]
[http://tika.apache.org/1.7/examples.html#Picking_different_output_formats]
[http://tika.apache.org/1.18/gettingstarted.html]
[https://github.com/chrismattmann/tika-python]
[https://wiki.apache.org/tika/TikaJAXRS]

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
