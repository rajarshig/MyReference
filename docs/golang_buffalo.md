## Install
- [https://gobuffalo.io/en/docs/getting-started/installation](https://gobuffalo.io/en/docs/getting-started/installation)
```
wget https://github.com/gobuffalo/buffalo/releases/download/v0.15.0/buffalo_0.15.0_linux_amd64.tar.gz
$ tar -xvzf buffalo_0.15.0_linux_amd64.tar.gz
$ sudo mv buffalo /usr/local/bin/buffalo
```

## Create new project
- Refer to 
[https://gobuffalo.io/en/docs/getting-started/new-project](https://gobuffalo.io/en/docs/getting-started/new-project)
- 
```
buffalo new [projectname]
buffalo new [projectname] --api  # configure for api server
- Go to project folder & start
```
cd [projectfolder]
buffalo dev # should start the application at http://127.0.0.1:3000/
```
