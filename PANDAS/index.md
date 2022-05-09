# ACESSO À PORTA SERIAL

# SUMÁRIO
- **[INTRODUÇÃO](#introdução)**
- **[INFORMAÇÕES SOBRE O DATAFRAME](#informa)**
- **[READING AND WRITING IN CSV AND EXCEL FILE](#reading-and-writing-in-csv-and-excel-file)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
- **[DERIVADA](#derivada)**
 



# INTRODUÇÃO
Neste Módulo, tem como objetivo resumir os conceitos de Calculo II.
**Ele será resumido em topicos simples com base em alguns conceitos e formulas baseados no que o professor passou em sala e em breve oque consta no Conteúdo digital.**

# LIMITES
**[DERIVADA](#derivada)**
**[DERIVADA](#derivada)**

```python

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
```python
DataFrame.read_csv(path_or_buf=None, sep=',') -> Save a pandas DataFrame into an csv file, if the file separators are different from ',' use the 'sep' parameter 
EX:
CSV
COL1; COL2;COL3
data1;data2;data3 
data4;data5;data6
data7;data8;data9

Dataframe
    COL1  | COL2  | COL3
0   data1 | data2 | data3 
1   data4 | data5 | data6
2   data7 | data8 | data9


```
