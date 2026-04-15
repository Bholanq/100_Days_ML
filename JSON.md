JSON - JS Object Notation 
Universal Notation - understood by most languages 
API replies are usually in JSON format 

`import numpy as np`
`import pandas as pd`
## 1. reading local file 
`pd.read_json('path')`

## 2. from url 
`pd.read_json("url")`

# Working with SQL Data

`!pip install mysql.connector`
`import mysql.connector`

## 1. reading sql file 
#### Set up a connection with the server hosted, using XAMPP and phpMyAdmin
`conn = mysql.connector.connect(host = "localhost", user = "root",password = "",database = "world"`)

host, user, password, and database name is taken from phpMyAdmin.

`pd.read_sql_query("SELECT * FROM city",conn)`
