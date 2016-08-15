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
