# Install
- In Ubuntu
```
sudo apt-get install mysql-server mysql-client
```
- Use wIth python
```
sudo apt-get install python3.6-dev
sudo apt-get install build-essential
sudo apt update gcc
sudo apt-get install libssl-dev
sudo apt-get install libmysqlclient-dev
```

## Create user
- Create new user
```
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
```
- Provide user access
```
GRANT ALL PRIVILEGES ON dbname.* TO 'newuser'@'localhost' IDENTIFIED BY 'password';
```
- Update permissons
```
FLUSH PRIVILEGES;
```
- Reference
[https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)

## Allow user access from remote system
- Grant access for remote host
```
GRANT ALL PRIVILEGES ON dbname.* TO 'newuser'@'%' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
```
- In /etc/mysql/mysql.conf.d/mysqld.cnf, comment out the line with 'bind-address'
- Restart mysql

## Mysqldump
```
mysqldump --single-transaction -u username -p dbname tablename --where "updated_at < '2018-07-01 00:00:00'">backup_filename.sql
```
