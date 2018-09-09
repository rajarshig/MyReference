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

## Mysqldump
```
mysqldump --single-transaction -u username -p dbname tablename --where "updated_at < '2018-07-01 00:00:00'">backup_filename.sql
```
