# ACESSO À PORTA SERIAL

# SUMÁRIO
- **[INTRODUÇÃO](#introdução)**
- **[INFORMATION ABOUT DATAFRAME](#information-about-dataframe)**
- **[READING AND WRITING IN CSV AND EXCEL FILE](#reading-and-writing-in-csv-and-excel-file)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
 



# INTRODUÇÃO
Neste Módulo, tem como objetivo resumir os conceitos de Calculo II.
**Ele será resumido em topicos simples com base em alguns conceitos e formulas baseados no que o professor passou em sala e em breve oque consta no Conteúdo digital.**

# INFORMATION ABOUT DATAFRAME
- **[DATAFRAME.INFO()](#dataframeinfo)**

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

