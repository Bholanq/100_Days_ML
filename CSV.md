1. **Importing Pandas**
	 1. `import pandas as pd`
2. **Local csv file**
	1. `df_csv = pd.read_csv("file_name.csv"`
3.  **CSV from URL**
	1. 
	   ```
	   import requests
		from io import StringIO
		url = "https://raw.githubusercontent.com/cs109/2014_data/master/countries.csv"
		headers = {"User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:66.0) Gecko/20100101 Firefox/66.0"}
		req = requests.get(url, headers=headers)
		data = StringIO(req.text)
	   ```
4. **Sep Parameter**
	1. sep aka Separator Parameter
	2. By default in .csv files the sep is ","
	3. ![[Pasted image 20260414143700.png]]
	4. Eg. if we try reading a .tsv file with .read_csv the df will be wrong, We need to specify the separator.
	5. ![[Pasted image 20260414143831.png|242]]
	6. `sample_tsv = pd.read_csv("/sample-1.tsv",sep = "\t")
5. **Index_col parameter**
	1. We can convert one of the columns in present in the data into the index column eg. id cols
	2. `pd.read_csv("aug_train.csv",index_col = "column_name")
6. **Header Parameter**
	1. Used for in cases where the first row in the column headers, but taken as entries while reading the file.
	2. `pd.read_csv('test.csv',header = 1)` - this will read the first row the header
7. **use_cols parameter**
	1. only select the cols you want
	2. `pd.read_csv("test.csv",use_cols = ['col1','col2'])
8. **squeeze parameters**
	1. `pd.read_csv("a.csv",usecols = ['enrollee_id'],squeeze = True)
	2. This will convert the df into a series with only the usecols column 
9. **Skiprows/nrows parameter**
	1. `pd.read_csv('aud.csv', skiprows = [0,2])
	2. this will skip the rows with index 0 and 2
	3. `nrow = 100` - this will give only 100 rows
10. **encoding parameter** ????
	1. `pd.read_csv(".csv",encoding = 'latin-1')
#### 11. **skip bad files** 
	1. `` pd.read_csv(".csv",sep = ";", encoding = 'latin-1',error_bad_lines = False)
	2. This will skip any rows that could cause the data to not parse 

12. **dtypes parameter**
	1. By default pandas detects the dtype of the column(can check with .info())
	2. `pd.read_csv(".csv",dtype={'col_name':'data_type'})
	3. this would set the data_type of the col to preferred dtype 
13. **Handling Dates**
	1. Usually in pandas the date columns are treated as object datatype, in-order to perform date operations on these column we'll have to convert it into a datetime type column using the `parse_dates` parameter.
	2. `pd.read_csv(".csv",parse_date=['dates'])`
14. **Convertors** 
	1. With convertors we can apply functions on column data
	2. 
	   ```
 	   def func_name(): 
 	   pass
 	   
 	   pd.read_csv(".csv",converters('col_name',func_name))
	   ```
	   the function func_name will be applied on the entire column.
	3. 
15. **na_values parameters**
	1. this helps replace placeholders for NaN, with NaN 
	2. `pd.read_csv('aug_train.csv',na_values = ['entry1',"entry2"..])`
	3. This will replace all entries in the list with NaN
16. **Loading a huge dataset in chunks**(chunksize)
	1. `dfs = pd.read_csv("name.csv",chunksize = 5000)
	2. ```
	   for chunks in dfs:
		   print(chunk.shape)
	   ```
	3. This is will divide the entire dataset in the shape of iterable chunks. Tries to be the nearest number to the chunksize.	