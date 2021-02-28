---
title: Secure database connections and database queries using Python
author: Danny Morris
date: '2021-02-22'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
---

**Using `mysql-connector` and `pandas`**

```
import mysql.connector
import pandas as pd
import os

# Credentials
user = os.getenv('CASKEY5_USERNAME')
pwd = os.getenv('CASKEY5_PASSWORD')
host = os.getenv('CASKEY5_HOST')
database = 'caskey5_buffaloCrime'

# Database connection
cnx = mysql.connector.connect(user=user, password=pwd, host=host, database=database)

# SQL query
mycursor = cnx.cursor()
mycursor.execute("SELECT * FROM all_dates")

# Collect results from query and cast to Pandas DataFrame
df = pd.DataFrame(mycursor.fetchall())
df.columns = mycursor.column_names

# Close connection
cnx.close()

# Top 5 rows of data
df.head()
```

**Using `sqlalchemy`, `pymysql`, and `pandas`**

```
# Libraries
from sqlalchemy import create_engine
import pymysql
import pandas as pd
import os

# Credentials
user = os.getenv('CASKEY5_USERNAME')
password = os.getenv('CASKEY5_PASSWORD')
host = os.getenv('CASKEY5_HOST')
database = 'caskey5_buffaloCrime'

# Database connection
sqlEngine = create_engine('mysql+pymysql://{}:{}@{}:3306/{}'.format(user,password,host,database), pool_recycle=3600)
dbConnection = sqlEngine.connect()

# SQL query string
query = "select * from full_incidents limit 100"

# Execute query and return results as Pandas DataFRame
pd_df = pd.read_sql(query, dbConnection)

# Close connection!
dbConnection.close()
```