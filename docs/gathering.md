# DS: Gathering & Preparation

## DS: Collection

# Open Data

wikipedia dumps: [https://dumps.wikimedia.org/other/pagecounts-raw/](https://dumps.wikimedia.org/other/pagecounts-raw/)

# DS: Explore Data Analysis

Ok. You've assigned a machine learning task, then you get some data. What's next?

Explore Data Analysis is step you must do now.

## Question 1: What's size of your data set?

How many rows? How many columns?

## Question 2: What type of variables?

categorical, continuous or discrete

## Question 3: What are missing value?


# Tooling

* [pandas-profiling](https://github.com/JosPolfliet/pandas-profiling), [*demo*](http://nbviewer.jupyter.org/github/JosPolfliet/pandas-profiling/blob/master/examples/meteorites.ipynb)

> pip install -U pandas-profiling

[code language="python"]
import pandas as pd
import pandas_profiling
df = pd.read_csv("train.csv", parse_dates=True, encoding='UTF-8')
pandas_profiling.ProfileReport(df)
[/code]

# Gathering

Python: Read and Write Data

### Read and Write Data in python

This post shows how to import data to Python from numerous resources

<strong>CSV File</strong>

Read a csv file from local or from a server

[sourcecode language="python"]
import numpy as np
import pandas as pd
# read data
df = pd.read_csv('data.csv', header = 0)
# write data
df.to_csv('data.csv', header=1, index=False)
[/sourcecode]

**Excel File** [^1]

[code lang="python"]
import pandas as pd
# read data
df = pd.read_excel('data.xls')
[/code]

**Sqlite File** [^2] [^3]

[code lang="python"]
import sqlite3

DB_NAME = "db.sqlite3"
SELECT_QUERY = "SELECT page_id, type FROM service_page"
# connect to sqlite3
db_connector = sqlite3.connect(DB_NAME)
# excute query
cursor = db_connector.execute(SELECT_QUERY)
# return dataset
data_set = cursor.fetchall()
[/code]

[^1]: [pandas.read_excel](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_excel.html)\

[^2]: [pandas.read_sqlite](http://www.datacarpentry.org/python-ecology/08-working-with-sql)\

[^3]: [sqlite3.read_sqlite](http://www.tutorialspoint.com/sqlite/sqlite_python.htm)\

