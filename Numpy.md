 ![[Pasted image 20260413073613.png]]
NumPy (short for **Numerical Python**) is a core Python library used for **fast mathematical and numerical computations**, especially when working with arrays and matrices.

- **List** → General-purpose, can store _anything_
- **NumPy Array** → Designed for _numerical computation_
# 1. np arrays
#### Creating a Array 
`np.array(1) -> scalar
`np.array([1,2,3,4])

`np.array([[1,2,3],[4,5,6]])`

![[Pasted image 20260413074908.png|183]]

#### Creating an array of range - arange()
`np.arange(10000) -> [0,1,...1000]
`np.arange(0,10000) -> [0,1,2,..9999]`

#### Creating array from scratch
1. zeros
	1. `np.zeros((5,5))`
2. ones
	1. `np.ones((5,5))`
3. only one element  - full
	1. `np.full((5,5),7) ->5x5 matrice with only 7
4. random 
	1. `np.random.random((3,3))

#### Array properties

`arr = np.array([[1,2,4],[1,5,7]])
`arr.shape - (nxm)
`arr.ndim - 2 - Dimensions
`arr.size - 6 - Total elements 
`arr.dtype - Data Type - int64

#### array reshaping 
`arr = np.arange(0,10) - [0 1 2 3 4 5 6 7 8 9]
`reshaped = arr.reshape((2,5))
`print(reshaped) - [[0 1 2 3 4][5 6 7 8 9]]

1. `flattened = reshaped.flatten()`
2. `raveled = reshaped.ravel() - returns view instead of copy 

3. `reshaped.transpose()`
# 2. Numpy Array Operations

#### slicing 
![[Pasted image 20260413091028.png]]
#### DF slicing 
`df[row_range:col_range]
![[Pasted image 20260413091451.png]]

for fetching form a dataframe,
`arr_2d[row_range,col_range]
cannot use 
`arr_2d[row_range][col_range] -> this is wrong 

#### sorting 
`np.sort(unsorted_arr)

For matrices: We sort them based on their axis - row or column , similarly for 3D vectors we sort them based on row, column or depth.

eg. `arr_2d = [[1,4,6],
         `    [5,4,3]]

` np.sort(arr_2d,axis = 0)` - sort each column independently

1,4,3
5,4,6

`np.sort(arr_2d,axis = 1)` - sort each row independently
1,4,6
3,4,5

## Using numpy we can apply operations on entire arrays/dfs,Masks

` even = arr[arr%2 ==0]` 
`arr%2 ==0` is essentially a mask 
### Filters with mask 
`mask = arr>5`
`print(arr[mask])


# Fancy indexing vs np.where()

```
numbers = np.array([1,2,3,4,5,6,7,8,9])
indices = [1,4,6]
print(numbers[indices])
[2 5 7]
```

```
where_res = np.where(numbers>5) ->stores indexes
print(numbers[where_res])
[6,7,8,9]
```

```
condition_array = np.where(numbers>5,numbers*4, numbers)

print(condition_array)
[ 1 2 3 4 5 24 28 32 36]
```

the above is the same as:
```
if(numbers>5){
numbers `*4
}
else
{
numbers}
```

# Adding and Removing Data 
1. adding arrays (summing values)
```
	    arr1 = np.array([1,2,3,4])
		arr2 = np.array([5,6,7,8])
		print(arr1+arr2)
		[6,8,10,12]
```
2. concatenating two arrays
		`concat_arr = np.concat((arr1,arr2))
		`print(concat_arr)
		`[1,2,3,4,5,6,7,8]`
	
3. array compatibility 
		`arr1.shape == arr2.shape`
4. vstack - stacks rows and hstack - stacks columns
		```
		orig = np.array([[1,2],[3,4]])
		new_col = np.array([[5],[6]])
		new_row = np.array([7,8,9])
		final = np.hstack((orig,new_col))
		final = np.vstack((final,new_row))
		print(final)
		[[1 2 5] [3 4 6] [7 8 9]]
		```
5. deleting from a numpy arr
		`arr = np.array([1,2,34,5])
		`arr.delete(arr,start,end,skips)` - similar to slicing 

```
arr = np.array([1,2,3,4,5,6,7,8])
new = np.delete(arr,arr[1:5])
print(new)
```

# Operations on datasets

```
sales_data = np.array([
    [1, 150000, 180000, 220000, 250000],  # Paradise Biryani
    [2, 120000, 140000, 160000, 190000],  # Beijing Bites
    [3, 200000, 230000, 260000, 300000],  # Pizza Hub
    [4, 180000, 210000, 240000, 270000],  # Burger Point
    [5, 160000, 185000, 205000, 230000]   # Chai Point
])
```

np has methods that you can apply on datasets 
### **Sum** 
Total sales per restaurant 
`np.sum(array,axis)
`print(np.sum(sales_data[:,1:],axis =1))`

### Min 
`np.min(arr,axis)`
`np.min(sales_data[:,1:],axis =1)
- min sales per rest

### Max
`np.max(sales_data[:,1:],axis =0)`
- max sales per year

### Avg
`np.mean(sales_data[:,1:],axis =1)
- avg sales per rest

### cumsum - cumulative sales
`np.cumsum(arr,axis)

### Matplotlib
`plt.figure(figsize = (10,6)) -> decides the size of the plot 
`plt.plot(np.mean(cumsum,axis =0)) -> the actual plot 


## Vector Operations

#### Vector Addition 
```
vec1 = np.array([1,2,3,4,5])
vec2 = np.array([6,7,8,9,10])
print(vec1+vec2)
[ 7 9 11 13 15]
```
#### Dot product
` np.dot(vec1,vec2)

#### Vectorize method
`vectorize` lets you apply a **normal Python function** to every element of an array — as if the function were “vectorized”.
```
resturant_types = np.array(['biryani','chinese','pizza','burger'])
vectorized_upper = np.vectorize(str.upper)
print(vectorized_upper(resturant_types))
['BIRYANI' 'CHINESE' 'PIZZA' 'BURGER']
```

## Broadcasting 

Where ever we perform any operation on a dataset using a scalar, that operation is applied on every element in that data set.

```
monthly_avg = sales_data[:,1:]/12
print(monthly_avg)
[[12500. 15000. 18333.33333333 20833.33333333] [10000. 11666.66666667 13333.33333333 15833.33333333] [16666.66666667 19166.66666667 21666.66666667 25000. ] [15000. 17500. 20000. 22500. ] [13333.33333333 15416.66666667 17083.33333333 19166.66666667]]
```

# Storing Images

### Storing arrays
`np.save(name_to_be_stored_as,arr)

![[Pasted image 20260414065742.png|315]]

https://numpy.org/doc/stable/user/index.html