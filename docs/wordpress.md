## Install reference
[https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lamp-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lamp-on-ubuntu-16-04)
## Nginx virtual block
```
server {
        server_name example.com;
       # listen 80 default_server;
       # listen [::]:80 default_server ipv6only=on;

        root /var/www/site_folder;
        
        index index.php index.html index.htm;

        error_log /var/log/nginx/error.log info;

        location / {
                try_files $uri $uri/ =404;
                # try_files $uri $uri/ /index.php?q=$uri&$args;
        }

        error_page 404 /404.html;

        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
                root /usr/share/nginx/html;
        }

        location ~ \.php$ {
        #include fastcgi_params;
        #fastcgi_param SCRIPT_FILENAME $document_root/$fastcgi_script_name;
        # old code
        #fastcgi_pass   127.0.0.1:9000;
        #new code
        #fastcgi_index index.php;
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
        #try_files $uri =404;
    }
```