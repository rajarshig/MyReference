# ELK Stack (Elasticsearch, Logstash, Kibana)
----
## Elasticsearch 
### Install
As per [Elasticsearch document](/docs/elasticsearch.md)

## Logstash
### Install
- Reference
[https://www.elastic.co/guide/en/logstash/7.6/installing-logstash.html#_apt](https://www.elastic.co/guide/en/logstash/7.6/installing-logstash.html#_apt)
```
sudo apt-get install apt-transport-https
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
sudo apt-get update && sudo apt-get install logstash
```
- Test logstash
```
/usr/share/logstash/bin/logstash -f logstash-sample.conf
```

### Start
- For OS using systemd (eg. Ubuntu 15.10+) use `sudo systemctl start logstash.service` 

## Filebeat
Reference [https://www.elastic.co/beats/filebeat](https://www.elastic.co/beats/filebeat)

### Install
- 
```
sudo apt-get update && sudo apt-get install filebeat
```
- Configure filebeat to run automatically
```
sudo systemctl enable filebeat
```
- To configure Filebeat, you edit the configuration file. The default configuration file is called `filebeat.yml` which is located at `/etc/filebeat` in Ubuntu

## Kibana
### Install
-
```
curl -L -O https://artifacts.elastic.co/downloads/kibana/kibana-7.6.2-linux-x86_64.tar.gz
tar xzvf kibana-7.6.2-linux-x86_64.tar.gz
cd kibana-7.6.2-linux-x86_64/
./bin/kibana
```



In /etc/filebeat/filebeat.yml, uncomment line 
hosts: ["localhost:5044"]

we will use the system module, which collects and parses logs created by the system logging service of common Linux distributions.
sudo filebeat modules enable system

check list of enabled & disabled module
sudo filebeats modules list

module wise config files are located at
/etc/filebeats/modules.d/

create a configuration file called 10-syslog-filter.conf, where we will add a filter for system logs, also known as syslogs:
sudo nano /etc/logstash/conf.d/10-syslog-filter.conf



Next, load the index template into Elasticsearch. 
sudo filebeat setup --template -E output.logstash.enabled=false -E 'output.elasticsearch.hosts=["localhost:9200"]'

Now you can start and enable Filebeat:

sudo systemctl start filebeat
sudo systemctl enable filebeat


If you’ve set up your Elastic Stack correctly, Filebeat will begin shipping your syslog and authorization logs to Logstash, which will then load that data into Elasticsearch.

To verify that Elasticsearch is indeed receiving this data, query the Filebeat index with this command:

For debugging, check if both filebeat & logstash are running
sudo systemctl status logstash.service
sudo systemctl status filebeat.service


Filebeat log
/var/log/filebeat/

Logstash log
/var/log/logstash/