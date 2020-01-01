# Django Cheatsheet

## View generated SQL
- display the SQL statements for specific migration of the app
```
python manage.py sqlmigrate <appname> <migration no eg. 0001 or 0004>
```
- View all the sql for specific app
```
python manage.py sqlmigrate <appname>
```
