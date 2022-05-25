```shell
# python3
$ pip install pymysql
$ pip install sqlalchemy
```

### SQL Alchemy, PyMysql, MySQLdb 
- install_as_MySQLdb() 함수를 통해  MySQLdb와 호환 가능.
- 이제 sql alchemy를 통해 DB에 연결할 수 있음. 

```python 
import pandas as pd
from sqlalchemy import create_engine

# MySQL Connector using pymysql
pymysql.install_as_MySQLdb()
import MySQLdb

engine = create_engine("mysql+mysqldb://root:"+"password"+"@localhost/db_name", encoding='utf-8')
conn = engine.connect()
```

### MySQL에 저장하기 
이제 DataFame을 Mysql에 테이블 형태로 저장할 차례. 
아래와 같이 pandas의 to_sql 함수를 사용하여 저장하면 된다.

```python 
df.to_sql(name=table, con=engine, if_exists='append')
```
