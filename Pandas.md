Pandas is an open source data analysis library written in python
It leverages the power and speed of numpy to make data analysis and preprocessing easier.

# Creating a dataframe 

`df = pd.DataFrame(input)`

the input can of anything that can be represented in a tabular format. eg. Matrices, Dictionaries, arrays etc

```
dict1 = {
    "name":["harry","rohan"],
    "marks":[92,34],
    "city":["rampur","kolkata"]
}
```

`df = pd.DataFrame(dict1)
![[Pasted image 20260414073556.png|247]]

`df.to_csv('marks.csv')` - creates a csv file 

### 1. df methods

`df.head()
`df.tail()

` df.describe()` - Gives statistical information about the df
eg: 
![[Pasted image 20260414074052.png|140]]

### 2. Importing to df

1. Reading CSV
` harry = pd.read_csv('name.csv')

- Setting the index
	`harry.index = ['name','you','want','the','cols','to','be']

# Pandas Data Structures

Pandas has two types of data Structures:
1. **Series** - It is a one dimensional array with indexes, it stores a single column or row of data in a Dataframe.
2. **Dataframe** - It's a tabular spreadsheet like structure representing rows each of which contain one or multiple columns.
 Dataframe are made of Series

Declaring Series and DF:
1. `ser = pd.Series(np.random.rand(10))`
2. `newdf =pd.DataFrame(np.random.rand(344,5))
3. `newdf.dtypes()`- Shows the datatypes in each col
4. `type(newdf)` - Dataframe

We can change any entry in the DF,
`newdf[0][0] = "name"` - Valid
![[Pasted image 20260414081537.png]]
But the datatype of that col will be changed to a `Object`

`newdf.index` - shows all the row indexes
`newdf.column` - shows all the column headings

![[Pasted image 20260414081730.png]]

# Transformations

1. `newdf.to_numpy()` - Converts the Series/Row to numpy format (2D Tensors/Matrices)
2. `newdf.T` - Transposes the entire DF
	1. ![[Pasted image 20260414083046.png|360]]
3. `newdf.sort_index(axis=0,ascending = False)` - will sort the entire df based on its index

## Difference between copy and view

Same logic applies in general Python.

Suppose we have an obj1,
A view is just another pointer pointing to the same (obj1)
Whereas a copy is a pointer pointing to another object with the same data a obj1.

view:
```
df2 = df1
```
any changes made in df2 will also reflect in df1.

```
df2 = df1.copy()
```
df2 is entirely different from df1

# .loc v/s .iloc 
- `loc` → **“location by name”**
- `iloc` → **“location by index number”**

|Feature|`loc`|`iloc`|
|---|---|---|
|Based on|Labels (names)|Integer positions|
|Index type|'x', 'y', 'z'|0, 1, 2|
|Slice end|Inclusive|Exclusive|
|Use case|When labels matter|When position matters|
## dropping a column/row

`newdf.drop(0,axis=1)`
`newdf.drop(0,axis=)`

## displaying only selected rows,cols

Similar to numpy but using .loc

`df.loc[[row_range],[col_range]]`
`df.loc[[1,2],['a','b']]`

`newdf[:, :]
is **NumPy-style indexing**, but pandas does **not support it directly**.

- NumPy → `arr[row, col]`
- Pandas → `df.loc[row_label, col_label]` or `df.iloc[row_index, col_index]`

We can also add conditions within .loc and .iloc

`newdf.loc[(newdf['a']<0.3)]

# df.dropna() - removes NULL - drops entire row
1. df.dropna(how = "all",axis =1) - drops the column if entire column is NaN
2. df.dropna(how = 'any',axis=0) - drops the row if any element is NaN
# df.drop_duplicates() 

# Dates are  represented with the data type object in pandas