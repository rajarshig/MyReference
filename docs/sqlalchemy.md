# Documentation
[http://docs.sqlalchemy.org/en/latest/core/tutorial.html](http://docs.sqlalchemy.org/en/latest/core/tutorial.html)

# Imports
```
from sqlalchemy import create_engine, Table, MetaData, text, select, func
```
# Connection String
- Mysql
```
con_url = 'mysql://user:password@host/database?charset=utf8mb4'
```
# Create connection
```
DB_CONFIG = create_engine(con_url, pool_size=20, max_overflow=0)       
engine = DB_CONFIG
connection = engine.connect()
metadata = MetaData(engine, reflect=True)
```
# Raw query
- Set raw sql as variable & run using text() function
```
query_str = "SELECT A.location_woeid, B.name,  DATE_FORMAT(MIN(A.updated_at), '%d/%m/%Y %H:%i:00') AS timestamp, A.trend_id, UNIX_TIMESTAMP(MIN(A.updated_at)) AS unix_timestamp, SUM(A.stream_match_count) AS Count FROM A  HAVING A.trend_id= :trend_id);"

trend_count_query = connection.execute(text(query_str), location_woeid=location_woeid, trend_id=trend_id, start_dt=start_dt)

trend_count_data = trend_count_query.fetchall()
```
# Query using schema
- Create table metadata
```
tablename = metadata.tables['tablename']
```
- Select query
```
interval_query = select([tablename]).order_by('id').limit(12)
interval_data = connection.execute`(interval_query)
- Select LIKE query
```
q = select([tablename]).where(tablename.c.colname.like('%' + var_name + '%'))
```
- Select IN query
```
q = select([tablename]).where(tablename.c.colname.in_(['', '']))
```

first = interval_data.fetchone()
````
- Insert query
```
time_entry = {'interval_time': interval_time}
interval_result = connection.execute(interval_tracker.insert(), time_entry)
```
- Update query
```
trend_added = connection.execute(master_trends.update().where(master_trends.c.id == trend_id).values(category=new_trend_category, category_id=category_id))      
```