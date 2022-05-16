

# SUMMMARY
- **[INTRODUCTION](#introduction)**
- **[ARRAY BASICS](#array-basics)**
- **[ACCESSING AND CHANGING ARRAYS](#accessing-and-changing-arrays)**





# INTRODUCTION
This module aims to summarize codes that can help in data science using numpy, some function parameters will be hidden, as this module intends to be simple and synthesized, for more information follow the documentation link for each function.



# ARRAY BASICS
- **[CREATE ARRAY](#create-array---documentation)**
- **[GET INFORMATIONS](#get-informations)**
  - **[DIMENSIONS](#dimensions---documentation)**
  - **[SHAPE (ROWS AND COLS)](#shaperows-and-cols---documentation)**
  - **[GET TYPE](#get-type---documentation)**


https://numpy.org/doc/stable/reference/generated/numpy.array.html
## CREATE ARRAY - **[DOCUMENTATION](https://numpy.org/doc/stable/reference/generated/numpy.array.html)**
To create an array, you can fill or declare dimensions, see the example below.<br>
**OBS.:** The dtype parameter is used to convert the declared array according to the type entered in the parameter, it is usually used for economical memory space.
```python
array = numpy.array(object, dtype=None, ndmin=0)

EX.:
array = np.array([[1, 2, 3],[4, 5, 6]])

array
[[1 2 3]
 [4 5 6]]
```
For create an array more easily with more dimensions, use:
```python
EX.:
array = np.array([1, 2, 3], ndmin=4)

array
[[[[1 2 3]]]]
```
**OBS.:** To create a predefined array, you cannot insert different amount of values at each 'position' in the array, unless you define the type as ```object```.<br>,
**This operation is not recommended.**
```python
EX.:
array = np.array([[1, 2, 3],[4, 5, 6, 7]], dtype='object')

[list([1, 2, 3]) list([4, 5, 6, 7])]
```

## GET INFORMATIONS

### DIMENSIONS - **[DOCUMENTATION](https://numpy.org/doc/stable/reference/generated/numpy.ndarray.ndim.html)**
For get dimensions of an array, use:
```python
array
[[1 2 3]
 [4 5 6]]

array.ndim
2
```
### SHAPE(ROWS AND COLS) - **[DOCUMENTATION](https://numpy.org/doc/stable/reference/generated/numpy.ndarray.shape.html)**
For get number of rows and cols of an array, use:
```python
array
[[1 2 3]
 [4 5 6]]

array.shape
(2, 3)
```
### GET TYPE - **[DOCUMENTATION](https://numpy.org/doc/stable/reference/generated/numpy.ndarray.dtype.html)**
For get datatype of an array, use:
```python
array
[[1 2 3]
 [4 5 6]]

array.dtype
int32
```


# ACCESSING AND CHANGING ARRAYS
- **[GET A SPECIFIC ELEMENT](#get-a-specific-element)**
- **[GET COL](#get-col)**
- **[GET ROW](#get-row)**

## GET A SPECIFIC ELEMENT
```python
array[pos][pos][pos]....

EX.:
array
[[[ 1  2  3]
  [ 4  5  6]]
  
 [[ 8  9 10]
  [11 12 13]]]
 
array[0, 1, 0]
4
```
## GET COL
```python
EX.:
array
 [[ 8  9 10]
  [11 12 13]]]
 
array[:, 0]
[8 11]

```
## GET ROW
```python
EX.:
array
 [[ 8  9 10]
  [11 12 13]]]
 
array[0, :]
[ 8  9 10]
```

### DATAFRAME - **[DOCUMENTATION]()**
```python


```







