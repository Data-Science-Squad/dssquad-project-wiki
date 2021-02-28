---
title: Database queries using Python and SQLAlchemy and Pandas
author: Danny Morris
date: '2021-02-27'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
---

The following code snippet shows how to connect to our MySQL database using Python and SQLAlchemy, and how to execute SQL queries and collect the results in a Pandas DataFrame.

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