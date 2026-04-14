Tensors in machine learning are just generalized containers for data.
Tensor is the same as n-dimensional array 
### 0D Tensor/Scalar
- single number
- eg. 5
- ndim = 0

```
import numpy as np
a = np.array(90)
a.ndim 
```

we need to create the array/tensor using numpy
### 1D Tensor/Vector/1D Array
- list of number 
- eg. `[1,2,3]
- ndim = 1
```
arr = np.array([1,3,23,5])
arr.ndim
```


## No. of Axis = No. of dimensions = rank 

# Scalar Dimensions and Vector Dimensions are not the same

eg. `[1,2,3,5]` - is a 1D Scalar but the Vector itself has 4 Dimensions. ie. 4D vector.
The CS 4D vector would usually mean 4D tensor but here it just means a list with 4 elements.
In ML a vector is always a 1D tensor.
![[Pasted image 20260412085917.png|347]]

## 2D Tensor/Matrices 

```
mat = np.array([[1,2,4],[4,5,6]])
mat.ndim
```

## nD Tensors 
![[Pasted image 20260412084845.png|289]]

3D Tensors are nothing but a list of 2D tensors,
4D Tensor would be a list of 3D tensors and 
5D Tensor would be a matrix of 3D tensors or a list of 4D tensors.

# Shape vs Rank vs Axes
![[Pasted image 20260412085404.png]]

## Example of 3D Tensors
- Vectorization of text in NLP
- Time series Data
 ![[Pasted image 20260412090404.png|262]]
## 4D 
![[Pasted image 20260412090545.png|272]]

# 5D
Videos - Images/frames over time 

