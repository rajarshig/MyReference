# Glances - python based system monitoring tool. Can be used as standalone, Client/server, Web server
Documentation
[https://glances.readthedocs.io](https://glances.readthedocs.io)

## Install
- Ubuntu
```
apt-get install glances
```
- python pip
```
pip install glances
```

## Standalone
- Monitor local system
```
$ glances
```

## Client Server mode
- In Server system
```
glances -s --password
```
- In Client system
```
client$ glances -c @server --password
```

## Central client
Glances can centralize available Glances servers using the --browser option. The server list can be statically defined via the configuration file
```
[serverlist]
# Define the static servers list
server_1_name=xps
server_1_alias=xps
server_1_port=61209
server_2_name=win
server_2_port=61235
```
To start the central client, use the following option:
```
client$ glances --browser
```
## Web Server Mode
If you want to remotely monitor a machine, called server, from any device with a web browser, just run the server with the -w option:
```
server$ glances -w

```
then on the client enter the following URL in your favorite web browser, where @server is the IP address or hostname of the server.
```
http://@server:61208
```
To change the refresh rate of the page, just add the period in seconds at the end of the URL. For example, to refresh the page every 10 seconds:
```
http://@server:61208/10
```
