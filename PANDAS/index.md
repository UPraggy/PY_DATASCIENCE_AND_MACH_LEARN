# ACESSO À PORTA SERIAL

# SUMÁRIO
- **[INTRODUCTION](#introduction)**
- **[CREATE DATAFRAME](#create-dataframe)**
- **[INFORMATION ABOUT DATAFRAME AND EDITS](#information-about-dataframe-and-edits)**
- **[READING AND WRITING IN CSV AND EXCEL FILE](#reading-and-writing-in-csv-and-excel-file)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
 



# INTRODUCTION
This module aims to summarize codes that can help in data science using pandas, some function parameters will be, because this module intends to be simple and synthesized, for more information follow the documentation link for each function.
# CREATE DATAFRAME
The best way to create a dataframe is using dictionaries, where the keys will be the columns and the values the rows.<br>
**OBS.:** For each value of the "list" within the dictionary a line will be created with that value, that is, as in the example below, the first values of **'number_order', | 'client' | 'value'**, will compose the first line: **1 | x | 120**
```python
d = {'number_order' : [1, 2, 3, 4, 5, 6],
'client' : ['x', 'y', 'z', 'd', 'e', 'f'],
'value' : ['120', '187.74', '188.7', '300', '563.2', '198.0']
}
df = pd.DataFrame(data = d)

   number_order |  client  |  value
0        1      |     x    |   120
1        2      |     y    |   187.74
2        3      |     z    |   188.7
3        4      |     d    |   300
4        5      |     e    |   563.2
5        6      |     f    |   198.0
```

# INFORMATION ABOUT DATAFRAME AND EDITS
- **[DATAFRAME.INFO()](#dataframeinfo)**
- **[DATAFRAME.SHAPE](#dataframeshape)**
- **[DATAFRAME.COLUMNS](#dataframecolumns)**
- **[DATAFRAME.RENAME()](#dataframerename)**

### DATAFRAME.INFO()
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
### DATAFRAME.SHAPE
Return a tuple representing the dimensionality of the DataFrame.
```python
df = pd.DataFrame({'col1': [1, 2], 'col2': [3, 4]})
df.shape
(2, 2)
```
### DATAFRAME.COLUMNS
Return a list with columns of dataframe.
```python
df = pd.DataFrame({'col1': [1, 2], 'col2': [3, 4]})
df.columns
['col1','col2']
```
### DATAFRAME.RENAME()
Rename columns or rows. **[DOCUMENTATION](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.rename.html)**<br>
**OBS.:** The inplace command equals true replaces the datraframe values instead of returning a copy of it.
```python
DataFrame.rename(columns = None, axis = None, inplace=False)

df = pd.DataFrame({'col1': [1, 2], 'col2': [3, 4]})
    col1  col2
0     1     2
1     3     4

df.rename(columns = {'col1': 'COL1', 'col2': 'COL2'}, inplace=True)
    COL1  COL2
0     1     2
1     3     4

If you want to change and know the name of all columns, it is also possible to change through a list of values

df.columns = ['COL3','COL4']
    COL4  COL3
0     1     2
1     3     4

```








# READING AND WRITING IN CSV AND EXCEL FILE
If you want to read the files or save the dataframes in more than one worksheet, follow this **[TUTORIAL](https://cursos.alura.com.br/forum/topico-salvar-arquivo-excel-com-varias-abas-145704)**
#### EXCEL
Supports xls, xlsx, xlsm, xlsb, odf, ods and odt file extensions read from a local filesystem or URL. Supports an option to read a single sheet or a list of sheets.
```python
DataFrame.to_excel(excel_path) -> Save a pandas DataFrame into an Excel file.
```
```python
DataFrame.read_excel(io) -> Read an Excel file into a pandas DataFrame.
```
#### CSV
```python
DataFrame.read_csv(path_or_buf=None, sep=',') -> Read an CSV file into a pandas DataFrame, if the file separators are different from ',' use the 'sep' parameter 
EX:
CSV
COL1;COL2;COL3
data1;data2;data3 
data4;data5;data6
data7;data8;data9

Dataframe
    COL1  | COL2  | COL3
0   data1 | data2 | data3 
1   data4 | data5 | data6
2   data7 | data8 | data9

```
```python
DataFrame.to_csv(path_or_buf=None) -> Save a pandas DataFrame into an CSV file.
```

