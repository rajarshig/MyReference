


## Install PostGreSQL 10
## Ubuntu 16.04
- Uninstall if any previous version
- Add the official postgres apt repository
```

Ubuntu 14.04: sudo add-apt-repository 'deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main'
Ubuntu 16.04: sudo add-apt-repository 'deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main'
Ubuntu 17.04: sudo add-apt-repository 'deb http://apt.postgresql.org/pub/repos/apt/ zesty-pgdg main'
```
- Import the repository signing key, followed by an update to the package lists
```
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | \
  sudo apt-key add -
sudo apt-get update
```
- Install 
```
sudo apt-get install postgres-10
```
- Ensure that the server is started by switching to the postgres user.
```
sudo su - postgresql
```