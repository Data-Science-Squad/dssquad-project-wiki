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

Use the following code snippets to connect to our MySQL database in Python and submit database queries. Note that your credentials will need to be stored as **environment variables** to prevent sensitive information from being showin in plain text in the codebase.

To set environment variables in Python, use `os.environ["CASKEY5_USERNAME"] = "<username>"`. Note that this will save the environment variable *for the current session only*. If you begin a new Python session, the environment variables must be saved again. There are ways to set permanent environment variables, but I'll leave that up to you.

:exclamation::exclamation: Any files pushed to GitHub should not contain any credentials exposed in plain text.

### Using mysql-connector and pandas

Kudos to Melvin for submitting this contribution.

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

### Using SQLAlchemy, pymysql, and pandas

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