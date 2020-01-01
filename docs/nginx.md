## Virtual Block
## Logging
- Define access log & error log in /etc/nginx/nginx.conf or /etc/nginx/sites-available/[virtual block]
```
access_log /var/log/nginx/access.log;
error_log /var/log/nginx/error.log;
```
- Create custom log format
```
log_format myapilogformat '$remote_addr - $remote_user xxx[$time_local]xxx '
 '"$request" $status $body_bytes_sent '
 '"$http_referer" "$http_user_agent" $response_time ';
```

- Update log file with log format
```
access_log /var/log/nginx/access.log myapilogformat;
```

## Allow large file upload (Error: 413 Request Entity Too Large)
- In /etc/nginx/nginx.conf, add the following line to http or server or location context to increase the size limit
```
client_max_body_size 2M;
```

Reference:
[Nginx log formats](http://nginx.org/en/docs/http/ngx_http_log_module.html)


## Test
- After any changes in Nginx configuration files, test using following code
```
nginx -t   #tests all nginx configurations
```
