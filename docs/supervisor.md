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

## Sample configuration for python project with Anaconda
```
[program:bses_amr]

directory=/home/xtage/py_projects/bses_amr_demo/bses_amr
environment=PATH=/home/xtage/miniconda3/envs/bses_amr/bin
command=/home/xtage/miniconda3/envs/bses_amr/bin/gunicorn bses_amr.wsgi:application -b 0.0.0.0:9098

autostart=true
autorestart=true
user=xtage
stopasgroup=true
stderr_logfile=/var/log/bses_amr_err.log
stdout_logfile=/var/log/bses_amr_err.log
```