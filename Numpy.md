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
	1. np.random.random((3,3))

#### Array properties

`arr = np.array([[1,2,4],[1,5,7]])
`arr.shape - (nxm)
`arr.ndim - 2 - Dimensions
`arr.size - 6 - Total elements 
`arr.dtype - Data Type - int64

#### array reshaping 
`arr = np.arange(0,10) - [0 1 2 3 4 5 6 7 8 9]
`reshaped = arr.reshape((2,5)
`print(reshaped) - [[0 1 2 3 4] [5 6 7 8 9]]

1. `flattened = reshaped.flatten()`
2. `raveled = reshaped.ravel() - returns view instead of copy 

3. `reshaped.transpose()`
# 2. Numpy Array Operations

#### slicing 

![[Pasted image 20260413091028.png]]
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



