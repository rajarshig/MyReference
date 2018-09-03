# Install
- In ubuntu, first install SASL
```
sudo apt-get install libsasl2-dev
```
- Install hive related python packages
```
pip install sasl
pip install thrift
pip install thrift-sasl
pip install PyHive
```
- Connect with hive
```
from pyhive import hive
conn = hive.Connection(host="YOUR_HIVE_HOST", port=PORT, username="YOU")
```
- Direct connection
```
cursor = conn.cursor()
cursor.execute("SELECT cool_stuff FROM hive_table")
for result in cursor.fetchall():
  use_result(result)
```
- Use with Pandas
```
import pandas as pd
df = pd.read_sql("SELECT cool_stuff FROM hive_table", conn)
```