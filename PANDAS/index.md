

# SUMMMARY
- **[INTRODUCTION](#introduction)**
- **[CREATE DATAFRAME](#create-dataframe)**
- **[DATAFRAME INDEX](#dataframe-index---documentation)**
- **[INFORMATION ABOUT DATAFRAME AND EDITS](#information-about-dataframe-and-edits)**
- **[READING AND WRITING IN CSV AND EXCEL FILE](#reading-and-writing-in-csv-and-excel-file)**
- **COLUMNS, ROWS AND DATA**
  - **[CREATING AND DELETE COLUMNS](#creating-and-delete-columns)**
  - **[SELECTION (OR SEARCH) DATAFRAME OR SERIES](#selection-or-search-dataframe-or-series)**
  - **[ADVANCED DATA FILTER](#advanced-data-filter)**
  - **[BASIC CHANGES TO COLUMNS VALUES](#basic-changes-to-columns-values)**
  - **[ADVANCED CHANGE VALUES](#advanced-change-values)**




# INTRODUCTION
This module aims to summarize codes that can help in data science using pandas, some function parameters will be, because this module intends to be simple and synthesized, for more information follow the documentation link for each function.










# CREATE DATAFRAME
The best way to create a dataframe is using dictionaries, where the keys will be the columns and the values the rows.<br>
**OBS.:** For each value of the "list" within the dictionary a line will be created with that value, that is, as in the example below, the first values of **'number_order', | 'client' | 'value'**, will compose the first line: **1 | x | 120**<br>
If you don't pass any value to the **index** parameter, the dataframe created will have indexes from 0 to the number of rows -1

```python
d = {'number_order' : [1, 2, 3, 4, 5, 6],
'client' : ['x', 'y', 'z', 'd', 'e', 'f'],
'value' : ['120', '187.74', '188.7', '300', '563.2', '198.0']
}
df = pd.DataFrame(data = d, index = ['a', 'b', 'c', 'd', 'e', 'f'])

df
   number_order |  client  |  value
a        1      |     x    |   120
b        2      |     y    |   187.74
c        3      |     z    |   188.7
d        4      |     d    |   300
e        5      |     e    |   563.2
f        6      |     f    |   198.0

WITHOUT INDEX PARAMTER

df = pd.DataFrame(data = d)

df
   number_order |  client  |  value
0        1      |     x    |   120
1        2      |     y    |   187.74
2        3      |     z    |   188.7
3        4      |     d    |   300
4        5      |     e    |   563.2
5        6      |     f    |   198.0
```
















# INFORMATION ABOUT DATAFRAME AND EDITS
- **[DATAFRAME.INFO()](#dataframeinfo---documentation)**
- **[DATAFRAME.DESCRIBE()](#dataframedescribe---documentation)**
- **[DATAFRAME.VALUE_COUNTS()](#dataframevalue_counts---all-column-documentation--dataframecolumnvalue_counts---specific-column-documentation)**
- **[DATAFRAME.HEAD()](#dataframehead---documentation)**
- **[DATAFRAME.SHAPE](#dataframeshape---documentation)**
- **[DATAFRAME.COLUMNS](#dataframecolumns---documentation)**
- **[DATAFRAME.RENAME()](#dataframerename---documentation)**

### DATAFRAME.INFO() - **[DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.info.html)**
```python
DataFrame.info() -> This method prints information about a DataFrame including the index dtype and columns, non-null values and memory usage.

EX: 
int_values = [1, 2, 3, 4, 5]
text_values = ['alpha', 'beta', 'gamma', 'delta', 'epsilon']
float_values = [0.0, 0.25, 0.5, 0.75, 1.0]
df = pd.DataFrame({"int_col": int_values, "text_col": text_values,
                  "float_col": float_values})
df
    int_col text_col  float_col
0        1    alpha       0.00
1        2     beta       0.25
2        3    gamma       0.50
3        4    delta       0.75
4        5  epsilon       1.00

df.info()

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 5 entries, 0 to 4
Data columns (total 3 columns):
 #   Column     Non-Null Count  Dtype  
---  ------     --------------  -----  
 0   int_col    5 non-null      int64  
 1   text_col   5 non-null      object 
 2   float_col  5 non-null      float64
dtypes: float64(1), int64(1), object(1)
memory usage: 248.0+ bytes

```

### DATAFRAME.DESCRIBE() - **[DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html)**
This function provides a detailed description about the data in dataframe, contain [count, mean, std, min, max and percentiles (25%, 50%, 70%)] these values are separated and calculated for each column.
```python
DataFrame.describe()

EXAMPLE OF ESTRUCTURE DESCRIBE
DataFrame.describe()['COLUMN']
DataFrame.describe()[['COLUMN1','COLUMN2','COLUMN'3]]
DataFrame['COLUMN'].describe()

EX.:
   col1  col2
0     1    10
1     2    11
2     3    12
3     4    13
4     5    14
5     6    15
6     7    16
7     8    17
8     9    18


df.describe()

df
           col1       col2
count  9.000000   9.000000
mean   5.000000  14.000000
std    2.738613   2.738613
min    1.000000  10.000000
25%    3.000000  12.000000
50%    5.000000  14.000000
75%    7.000000  16.000000
max    9.000000  18.000000
```
**OBS.:** Case you want get specific values, you can use:
```python
describe_result = DataFrame.describe()
describe_result.loc[['metod']]

EXAMPLE OF ESTRUCTURE DESCRIBE
describe_result.loc[['metod','metod']]
describe_result.loc[['metod','metod'], ['COLUMN']]
describe_result.loc[['metod','metod'], ['COLUMN', 'COLUMN1']]

EX.:
   col1  col2
0     1    10
1     2    11
2     3    12
3     4    13
4     5    14
5     6    15
6     7    16
7     8    17
8     9    18

describe_result = df.describe()
print(describe_result.loc[['min', 'max'],['col1']])

describe_result
     col1
min   1.0
max   9.0
```
### DATAFRAME.VALUE_COUNTS() - [ALL COLUMN DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.value_counts.html) / DATAFRAME['COLUMN'].VALUE_COUNTS() - [SPECIFIC COLUMN DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.Series.value_counts.html)
Counts how many occurrences or records of a given value in a given column:
```python
DataFrame.value_counts()
DataFrame['COLUMN'].value_counts()



df
    int_col   text_col  float_col
0         1      alpha       0.00
1         2       beta       0.25
2         3      gamma       0.50
3         4      delta       0.75
4         5    epsilon       1.00
5         9         pi       3.14
6        10      regex       2.00
7        23      other       4.10
8        25  imaginary       2.70
9        52       star       8.10
10       12       beta       0.50
11       35      gamma       0.75
12       92         pi       1.00
13       23       beta       8.00


df['text_col'].value_counts()

df
beta         3
gamma        2
pi           2
alpha        1
delta        1
epsilon      1
regex        1
other        1
imaginary    1
star         1
Name: text_col, dtype: int64
```
### DATAFRAME.HEAD() - **[DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.head.html)**
Return the DataFrame limited by 5 lines if you don't change the parameter **n**.
```python
DataFrame.head(n)

df = pd.DataFrame({'col1': [1, 2, 3, 4, 5, 6, 7, 8, 9], 'col2': [10, 11, 12, 13, 14, 15, 16, 17, 18, 19]})
df.head()

df
   col1  col2
0     1    10
1     2    11
2     3    12
3     4    13
4     5    14
```
### DATAFRAME.SHAPE - **[DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.shape.html)**
Return a tuple representing the dimensionality of the DataFrame.
```python
df = pd.DataFrame({'col1': [1, 2], 'col2': [3, 4]})
df.shape
(2, 2)
```
### DATAFRAME.COLUMNS - **[DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.columns.html)**
Return a list with columns of dataframe.
```python
df = pd.DataFrame({'col1': [1, 2], 'col2': [3, 4]})
df.columns
['col1','col2']
```
### DATAFRAME.RENAME() - **[DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.rename.html)**
Rename columns or rows. <br>
**OBS.:** The inplace command equals true replaces the datraframe values instead of returning a copy of it.
```python
DataFrame.rename(columns = None, axis = None, inplace=False)

df = pd.DataFrame({'col1': [1, 2], 'col2': [3, 4]})

df
    col1  col2
0     1     2
1     3     4

df.rename(columns = {'col1': 'COL1', 'col2': 'COL2'}, inplace=True)

df
    COL1  COL2
0     1     2
1     3     4

If you want to change and know the name of all columns, it is also possible to change through a list of values

df.columns = ['COL3','COL4']

df
    COL4  COL3
0     1     2
1     3     4

```

















# READING AND WRITING IN CSV AND EXCEL FILE 
If you want to read the files or save the dataframes in more than one worksheet, follow this **[TUTORIAL](https://cursos.alura.com.br/forum/topico-salvar-arquivo-excel-com-varias-abas-145704)**
#### EXCEL - **[READ EXCEL DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.read_excel.html#pandas.read_excel)** **[TO EXCEL DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_excel.html)**
Supports xls, xlsx, xlsm, xlsb, odf, ods and odt file extensions read from a local filesystem or URL. Supports an option to read a single sheet or a list of sheets.
```python
DataFrame.to_excel(excel_path) -> Save a pandas DataFrame into an Excel file.
```
```python
pandas.read_excel(io) -> Read an Excel file into a pandas DataFrame.
```
#### CSV - **[READ CSV DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html)** **[TO CSV DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_csv.html)**
```python
pandas.read_csv(path_or_buf=None, sep=',') -> Read an CSV file into a pandas DataFrame, if the file separators are different from ',' use the 'sep' parameter 

EX:
CSV
COL1;COL2;COL3
data1;data2;data3 
data4;data5;data6
data7;data8;data9

pandas.read_csv(path_or_buf=None, sep=';') 

Dataframe
    COL1  | COL2  | COL3
0   data1 | data2 | data3 
1   data4 | data5 | data6
2   data7 | data8 | data9

```
```python
Dataframe.to_csv(path_or_buf=None) -> Save a pandas DataFrame into an CSV file.
```
**OBS.:** This command like ```DataFrame.to_excel()``` or ```Dataframe.to_csv()``` contains **index=True** parameters by **default**, which results in an excel file with an extra column numbered according to standard indexes from 0 to number of lines -1:
```python
DataFrame.to_excel(excel_path, index=True)

Dataframe
    COL1  | COL2  | COL3
0   data1 | data2 | data3 
1   data4 | data5 | data6
2   data7 | data8 | data9

```
If you don't want it in your excel file use **index=False** and the first column will be considered the data index:
```python
DataFrame.to_excel(excel_path, index=False)

Dataframe

COL1  | COL2  | COL3
data1 | data2 | data3 
data4 | data5 | data6
data7 | data8 | data9

```













# SELECTION (OR SEARCH) DATAFRAME OR SERIES
- **[SELECT COLUMN](#select-column)**
- **[SELECT ROW](#select-row)**
- **[SELECT CELL](#select-cell)**
- **[SELECT BY INDEX](#select-row-by-index)** 
- **[SELECT BY LABEL](#select-by-label-almost-the-same-as-select-by-index---documentation)**
- **[SEARCH BY STRING](#search-by-string---documentation)**

## SELECT COLUMN
This command return a **```<class 'pandas.core.series.Series'>```** of the selected column (**This return dont is a copy**, case alter any row of column, will you alter this value in dataframe too) 
```python
DataFrame['COLUMN']
EX.:
df
    int_col text_col  float_col
0        1    alpha       0.00
1        2     beta       0.25
2        3    gamma       0.50
3        4    delta       0.75
4        5  epsilon       1.00

df['text_col']

    text_col  
0    alpha
1    beta
2    gamma
3    delta
4    epsilon

```
In case you want to have a copy of the column, use:
```python
DataFrame['COLUMN'].copy()
```

## SELECT ROW
This command return **```<class 'pandas.core.series.Series'>```** of the selected row (**This return dont is a copy**, case alter any value of row, will you alter this value in dataframe too) 

### SELECT ROW BY INDEX - **[DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.iloc.html)**
```python
DataFrame.iloc[index]

EX.:
df
    int_col text_col  float_col
0        1    alpha       0.00
1        2     beta       0.25
2        3    gamma       0.50
3        4    delta       0.75
4        5  epsilon       1.00

df.iloc[2]

int_col          3
text_col     gamma
float_col      0.5
```
If you want get the last register, you may substitute the index for -1

```python
EX.:
df.iloc[-1]

int_col            5
text_col     epsilon
float_col        1.0
```

In case you want to have a copy of the row, use:
```python
DataFrame.iloc[index].copy()
```
**OBS.:** The **iloc** function only accepts implicit indexes, that is, according to the example below, if you want to access the **index** of the row or column by the **label**, there will be an error

```python
DataFrame.iloc[index]

EX.:
df
    int_col text_col  float_col
a        1    alpha       0.00
b        2     beta       0.25
c        3    gamma       0.50
d        4    delta       0.75
e        5  epsilon       1.00

df.iloc['a']

ERROR:
TypeError: Cannot index by location index with a non-integer key
```
## SELECT CELL
This command returns the **value** of the selected cell (**This return is not a copy**, if you change the value, you will change this value in the dataframe too)
```python
DataFrame.iloc[index, column]

EX.:
df
    int_col text_col  float_col
0        1    alpha       0.00
1        2     beta       0.25
2        3    gamma       0.50
3        4    delta       0.75
4        5  epsilon       1.00

df.iloc[2,2]

    gamma
    
```

### SELECT BY LABEL (ALMOST THE SAME AS SELECT BY INDEX) - **[DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html)**
**OBS.:** This return dont is a copy, case alter any value of row, will you alter this value in dataframe too.
```python
DataFrame.loc[label]

EX.:
df
    int_col text_col  float_col
a        1    alpha       0.00
b        2     beta       0.25
c        3    gamma       0.50
d        4    delta       0.75
e        5  epsilon       1.00
```
#### SELECT ROW
```python
df.loc['a']

int_col          1
text_col     alpha
float_col      0.00
```
#### SELECT COLUMN
```python
df.loc[:, 'int_col'] -> The ':' operator makes the function of referencing all lines

df
   int_col
a        1
b        2
c        3
d        4
e        5
```
In case you want to have a copy, use:
```python
DataFrame.loc[label].copy()
```
#### SELECT BY CONDITIONS 
```python
df.loc[df['int_col'] > 2]

df
   int_col text_col  float_col
c        3    gamma       0.50
d        4    delta       0.75
e        5  epsilon       1.00
```
**OBS.:** The **loc** function only accepts labels, that is, according to the example below, if you want to access the **label** of the row or column by the **index**, there will be an error

```python
DataFrame.loc[label]

EX.:
df
    int_col text_col  float_col
a        1    alpha       0.00
b        2     beta       0.25
c        3    gamma       0.50
d        4    delta       0.75
e        5  epsilon       1.00

df.loc[0]

ERROR:
raise KeyError(key) from err
KeyError: 0
```

#### SEARCH BY STRING - [DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.Series.str.contains.html)
```python
df
   int_col text_col  float_col
0        1    alpha       0.00
1        2     beta       0.25
2        3    gamma       0.50
3        4    delta       0.75
4        5  epsilon       1.00
5        6   barial       2.10
6        7     batm       3.50


df.loc[df['text_col'].str.contains(f'^ba', case = False)]

   int_col text_col  float_col
5        6   barial        2.1
6        7     batm        3.5
```















# BASIC CHANGES TO COLUMNS VALUES
A way to **change** the **data** in the column **by a constant**
```python
DataFrame['COLUMN'] = constant

EX.:
df
    int_col text_col  float_col
0        1    alpha       0.00
1        2     beta       0.25
2        3    gamma       0.50
3        4    delta       0.75
4        5  epsilon       1.00


df["text_col"] = 'constanst'

df
   int_col   text_col  float_col
0        1  constanst       0.00
1        2  constanst       0.25
2        3  constanst       0.50
3        4  constanst       0.75
4        5  constanst       1.00
```

A way to **change** the **data** in the column **by a list** (the **list** must be the **same length** as the number of values in the **column**)
```python
DataFrame['COLUMN'] = list

df["text_col"] = ['a','b','c','d','e']

df
   int_col text_col  float_col
0        1        a       0.00
1        2        b       0.25
2        3        c       0.50
3        4        d       0.75
4        5        e       1.00
```
**OBS.:** The same operation, can do using a **```<class 'pandas.core.series.Series'>```** as long as it's the same length












# CREATING AND DELETE COLUMNS

A way to **create** a column in the dataframe, by through of a **constant**
```python
DataFrame['NEW COLUMN'] = constant

EX.:
df
    int_col text_col  float_col
0        1    alpha       0.00
1        2     beta       0.25
2        3    gamma       0.50
3        4    delta       0.75
4        5  epsilon       1.00


df["new_col"] = 'constanst'

df
   int_col   text_col  float_col   new_col
0        1   alpha       0.00      constant
1        2   beta        0.25      constant
2        3   gamma       0.50      constant
3        4   delta       0.75      constant
4        5   epsilon     1.00      constant
```
A way to **create** a column in the dataframe, by through of a **list** (the **list** must be the **same length** as the number of values in the **column**)

```python
DataFrame['NEW COLUMN'] = list

EX.:

df["new_col"] = ['a','b','c','d','e']

df
   int_col   text_col  float_col   new_col
0        1   alpha       0.00        a
1        2   beta        0.25        b
2        3   gamma       0.50        c
3        4   delta       0.75        d
4        5   epsilon     1.00        e
```
The **attribution of values** in column too can do through of a **operation or a function**

```python
EX.:

df["new_col"] = df["int_col"] * 1000

df
   int_col   text_col  float_col  NEW_COLUMN
0        1    alpha       0.00        1000
1        2    beta        0.25        2000
2        3    gamma       0.50        3000
3        4    delta       0.75        4000
4        5    epsilon     1.00        5000
```

#### DELETE COLUMN

A way to **delete** a column in the dataframe
```python
del DataFrame['COLUMN']

EX.:
df
    int_col text_col  float_col
0        1    alpha       0.00
1        2     beta       0.25
2        3    gamma       0.50
3        4    delta       0.75
4        5  epsilon       1.00


del df["float_col"]

df
   int_col text_col
0        1    alpha
1        2     beta
2        3    gamma
3        4    delta
4        5  epsilon
```













# DATAFRAME INDEX - **[DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.index.html)**
To retrieve dataframe indices use:
```python
DATAFRAME.index.to_list() OR DATAFRAME.index 
EX.:
df
   int_col   text_col  float_col  NEW_COLUMN
0        1    alpha       0.00        1000
1        2    beta        0.25        2000
2        3    gamma       0.50        3000
3        4    delta       0.75        4000
4        5    epsilon     1.00        5000

df.index.to_list()
[0, 1, 2, 3, 4]

df.index
RangeIndex(start=0, stop=5, step=1) # Default index type for dataframes created with pandas
```










# ADVANCED DATA FILTER
- **[CONDICIONAL SELECTIONS](#condicionals-selections)**
  - **[SELECT COLUMN WITH UNIQUE VALUES (WITHOUT REPEATING THEM)](#select-column-with-unique-values-without-repeating-them)**
  - **[QUERY](#query---documentation)**
  - **[BY LIST](#by-list---documentation)**
  - **[FOR PERFORMACE](#for-performace)**
 
  
This module will be compose by this Dataframe:
```python
df = pd.DataFrame({"int_col": [1, 2, 3, 4, 5, 9, 10, 23, 25, 52, 12, 35, 92, 23],
                   "text_col": ['alpha', 'beta', 'gamma', 'delta', 'epsilon', 'pi',
                               'regex', 'other', 'imaginary', 'star', 'beta', 'gamma', 'pi', 'beta'],
                   "float_col": [0.0, 0.25, 0.5, 0.75, 1.0, 3.14,
                                2, 4.1, 2.7, 8.1, 0.5, 0.75, 1.0, 8.0]})
df
    int_col   text_col  float_col
0         1      alpha       0.00
1         2       beta       0.25
2         3      gamma       0.50
3         4      delta       0.75
4         5    epsilon       1.00
5         9         pi       3.14
6        10      regex       2.00
7        23      other       4.10
8        25  imaginary       2.70
9        52       star       8.10
10       12       beta       0.50
11       35      gamma       0.75
12       92         pi       1.00
13       23       beta       8.00

```


## CONDICIONAL SELECTIONS

#### SELECT COLUMN WITH UNIQUE VALUES (WITHOUT REPEATING THEM) - [DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.Series.unique.html) 
Returns a array of data without repeats:

```python
DataFrame["Column"].unique()

df['text_col'].unique()

['alpha' 'beta' 'gamma' 'delta' 'epsilon' 'pi' 'regex' 'other' 'imaginary'
 'star']
 
Case you want order the values:
sorted(df['text_col'].unique())

['alpha', 'beta', 'delta', 'epsilon', 'gamma', 'imaginary', 'other', 'pi', 'regex', 'star']

```

#### QUERY  - [DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.query.html) 
Return a copy of the Dataframe with the queried data:
```python
DataFrame.query()

EXAMPLE OF ESTRUCTURE QUERY
DataFrame.query('COLUMN == "VALUE_SEARCH"')

DataFrame.query('COLUMN in @list_data') -> if you want to compare if the column contains the values of a list use '@'

EX.:
test_query = df.query('text_col == "beta"')

test_query
    int_col   text_col  float_col
1         2     beta       0.25
10       12     beta       0.50
13       23     beta       8.00
```

**OBS.:** The command dont work with columns with invalid caracters how spaces ('text col'):
```python
df
    int_col   text col  float_col
0         1      alpha       0.00
1         2       beta       0.25
2         3      gamma       0.50
.         .       .          .        
.         .       .          .       
.         .       .          .      
EX.:
test_query = df.query('text col == "beta"')

ERROR
SyntaxError: invalid syntax

TRY THIS:
test_query = df[(df["text col"] == "beta")]

test_query
    int_col   text_col  float_col
1         2     beta       0.25
10       12     beta       0.50
13       23     beta       8.00
```

Case you want reset the index of queried DataFrame use:
```python
test_query = test_query.reset_index()

test_query
   index    int_col  text_col  float_col
0      1        2     beta       0.25
1     10       12     beta       0.50
2     13       23     beta       8.00
```


**OBS.:** If you don't want to keep the old indexes use the following command:
```python
test_query = test_query.reset_index(drop=True)

test_query
   int_col text_col  float_col
0        2     beta       0.25
1       12     beta       0.50
2       23     beta       8.00
```
And case you want alter the DataFrame and not the copy use the parameter **```test_query.reset_index(inplace=True)```**


#### BY LIST - [DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.isin.html) 
```python
DataFrame["COLUMN"].isin(list)


EX.:
list_data = ["beta","imaginary","gamma"]
select = df["text_col"].isin(list_data)

test_query = df[select]

test_query
    int_col   text_col  float_col
1         2       beta       0.25
2         3      gamma       0.50
8        25  imaginary       2.70
10       12       beta       0.50
11       35      gamma       0.75
13       23       beta       8.00
```



#### FOR PERFORMACE
In a Dataframe with a lot of data, **searching with several conditions** at once tends to be very **expensive and slow**, to improve these searches and make them more **efficient it is recommended** to use **separate searches**:

```python
EXPENSIVE:

test_query = df[(df["int_col"] >= 10) & (df["float_col"] > 2)]

test_query
    int_col   text_col  float_col
7        23      other        4.1
8        25  imaginary        2.7
9        52       star        8.1
13       23       beta        8.0

CHEAP:
src1 = df[(df["int_col"] >= 10)]
src2 = src1[src1["float_col"] > 2]

test_query = src2

test_query
    int_col   text_col  float_col
7        23      other        4.1
8        25  imaginary        2.7
9        52       star        8.1
13       23       beta        8.0

```
This type of approach is cheaper because for each 'src' (search) a new DataFrame is generated with fewer lines than the previous one, making the next queries faster because it is a smaller dataframe, which does not happen in the more expensive example where at each condition the same DataFrame is scanned, that is, the query will be made in lines that would not be necessary.






# ADVANCED CHANGE VALUES
- **[APPLY](#apply---documentation)**
- **HONORABLE MENTION**
  - **MAP - [DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.Series.map.html)**
  - **APPLYMAP - [DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.applymap.html)**
  
The dataframe used for this topic:
```python
df
   Destination_1 Destination_2
0         BRAZIL        BRAZIL
1         BRAZIL       URUGUAY
2      ARGENTINA     SINGAPORE
3      ARGENTINA     ARGENTINA
4        MOROCCO      THAILAND
5      INDONESIA          PERU
6            USA       ECUADOR
7         BRAZIL           USA
8          EGYPT       ALGERIA
9          EGYPT         EGYPT
10           USA        CANADA
```
## APLLY - [DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html)
This function changes the values in **DataFrame or Series** according to the **axis** parameter where it defines whether the change operation will be in columns or rows.
<br>**OBS.:** ```axis=0``` for cols and ```axis=1``` for rows
```python
DataFrame.apply(func, axis = 0)
```
#### See the following example for same-line operation:
According to the Dataframe above the developer needs to create a new column **```OUTPUT```** based on the values of columns **```Destination_1```** and **```Destination_2 ``` **, the column **```OUTPUT```** will receive values between True or False, according to the test that returns True when the values of the two columns are equal and False if they are not.
```python
def func(line):
    if line[0] == line[1]:
        return True
    else:
        return False

df['OUTPUT'] = df.apply(func, axis = 1)


df
   Destination_1 Destination_2  OUTPUT
0         BRAZIL        BRAZIL    True
1         BRAZIL       URUGUAY   False
2      ARGENTINA     SINGAPORE   False
3      ARGENTINA     ARGENTINA    True
4        MOROCCO      THAILAND   False
5      INDONESIA          PERU   False
6            USA       ECUADOR   False
7         BRAZIL           USA   False
8          EGYPT       ALGERIA   False
9          EGYPT         EGYPT    True
10           USA        CANADA   False
```
#### See the following example for same-col operation:
According to the Dataframe above the developer wants to replace all column values that do not contain 'BRAZIL' by 'NOT'
```python
def func(line):
    temp = line.values.tolist()
    for x in range(0, len(temp)):
        if temp[x] != 'BRAZIL':
            line[x] = 'NOT'

df.apply(func, axis = 0)


df
   Destination_1 Destination_2
0         BRAZIL        BRAZIL
1         BRAZIL           NOT
2            NOT           NOT
3            NOT           NOT
4            NOT           NOT
5            NOT           NOT
6            NOT           NOT
7         BRAZIL           NOT
8            NOT           NOT
9            NOT           NOT
10           NOT           NOT
```

**OBS.:** The same thing can be done on a specific column:
```python
def func(line):
    if line != 'BRAZIL':
        return 'NOT'
    else:
        return line

df['Destination_1'] = df['Destination_1'].apply(func)


df
   Destination_1 Destination_2
0         BRAZIL        BRAZIL
1         BRAZIL       URUGUAY
2            NOT     SINGAPORE
3            NOT     ARGENTINA
4            NOT      THAILAND
5            NOT          PERU
6            NOT       ECUADOR
7         BRAZIL           USA
8            NOT       ALGERIA
9            NOT         EGYPT
10           NOT        CANADA
```
