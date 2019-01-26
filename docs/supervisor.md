## Install
```
apt-get install supervisor
```

## Sample configuration
- Add projectname.conf in /etc/supervisor/conf.d/
```
[program:proj_name]

directory=/home/username/proj_env/proj_folder
command=/home/username/proj_env/bin/gunicorn proj.wsgi:application -b 0.0.0:9099


autostart=true
autorestart=true
user=username
stopasgroup=true
stderr_logfile=/var/log/proj_err.log
stdout_logfile=/var/log/proj_err.log

```