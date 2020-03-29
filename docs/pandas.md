## Create a pandas dataframe directly from a s3 object
Create a pandas dataframe directly from a s3 object, which is a csv file (without downloading the file & reading from it)
```
import pandas as pd
import io

s3_obj = s3_client.get_object(Bucket=bucket, Key=filename)
s3_obj_df = pd.read_csv(io.BytesIO(s3_obj['Body'].read()), encoding='utf8')
```
As pd.read_csv() allows a file like object, here we created a file like object from the s3 binary file. which is similar to
```
f = open("data.csv", "rb")
```

## Pandera - A flexible & expressive pandas validation library
- [https://pandera.readthedocs.io/en/latest/index.html](https://pandera.readthedocs.io/en/latest/index.html)
- [https://www.pyopensci.org/blog/pandera-python-pandas-dataframe-validation](https://www.pyopensci.org/blog/pandera-python-pandas-dataframe-validation)

## Merge, Join & Concat
- [https://pandas.pydata.org/pandas-docs/stable/user_guide/merging.html](https://pandas.pydata.org/pandas-docs/stable/user_guide/merging.html)
- [https://www.dataquest.io/blog/pandas-concatenation-tutorial/](https://www.dataquest.io/blog/pandas-concatenation-tutorial/)




## CSV to Mysql table
```
import pandas as pd
from sqlalchemy import create_engine, Table, MetaData, text, select, func
import os


files = os.listdir('data')
db_connection = "mysql://{}:{}@{}/{}?charset=utf8mb4".format('user','password','host','database')
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
