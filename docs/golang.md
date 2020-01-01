## Install
- Reference
[https://golang.org/dl/](https://golang.org/dl/)
[https://golang.org/doc/install](https://golang.org/doc/install)
- Download binary file from [https://golang.org/dl/](https://golang.org/dl/)
- Extract to /usr/local
```
tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```
- Add to PATH
```
export PATH=$PATH:/usr/local/go/bin
source $HOME/.profile
```
- Test go command
```
go version
```
-
```
# Edit your ~/.bash_profile to add the following line:
export GOPATH=$HOME/go

# Save and exit your editor. Then, source your ~/.bash_profile.

source ~/.bash_profile
```

## Set GOPATH
- [https://github.com/golang/go/wiki/SettingGOPATH](https://github.com/golang/go/wiki/SettingGOPATH)
- [https://stackoverflow.com/questions/36017724/can-i-have-multiple-gopath-directories](https://stackoverflow.com/questions/36017724/can-i-have-multiple-gopath-directories)
-
```
go env -w GOPATH=$HOME/go
go env
```


```
