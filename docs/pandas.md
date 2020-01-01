## Pandera - A flexible & expressive pandas validation library
- [https://pandera.readthedocs.io/en/latest/index.html](https://pandera.readthedocs.io/en/latest/index.html)
- [https://www.pyopensci.org/blog/pandera-python-pandas-dataframe-validation](https://www.pyopensci.org/blog/pandera-python-pandas-dataframe-validation)

## Merge, Join & Concat
- [https://pandas.pydata.org/pandas-docs/stable/user_guide/merging.html](https://pandas.pydata.org/pandas-docs/stable/user_guide/merging.html)
- [https://www.dataquest.io/blog/pandas-concatenation-tutorial/](https://www.dataquest.io/blog/pandas-concatenation-tutorial/)


## Quick way to get Min & Max of columns
-
```
>>> df
```
```
>>>
Year      Month
2019.0    12.0
2019.0    11.0
....
2018.0    2.0
2018.0    1.0
```
Min of Month column
```
>>> df['Month'].min()
>>> Out[]: 1.0
```
Max of Year column
```
>>> df['Year'].max()
>>> Out[]: 2019.0
```
Min of both Month & Year combination
```
>>> df.min()
>>>
Year     2018.0
Month       1.0
dtype: float64
```
Max of both Month & Year combination
```
>>> df.max()
>>>
Year     2019.0
Month      12.0
dtype: float64
```
- Reference
[https://stackoverflow.com/questions/12169170/find-the-max-of-two-or-more-columns-with-pandas](https://stackoverflow.com/questions/12169170/find-the-max-of-two-or-more-columns-with-pandas)


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
