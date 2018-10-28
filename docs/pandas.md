## CSV to Mysql table
```
import pandas as pd
from sqlalchemy import create_engine, Table, MetaData, text, select, func
import os


files = os.listdir('data')
db_connection = "mysql://{}:{}@{}/{}?charset=utf8mb4".format('root','admin','localhost','rjt')
DB_CONFIG = create_engine(db_connection, pool_size=20, max_overflow=0)       
engine = DB_CONFIG
db_connection = engine.connect()

for filename in files:
    if filename.endswith('.csv'):
        df = pd.read_csv('data/'+filename)
        try:
            table_name = filename.split('.csv')[0]
            df.to_sql(table_name, con=engine, if_exists='append')   
        except Exception as e:
            pass
        print("{} updated".format(filename)) 
        # break
```