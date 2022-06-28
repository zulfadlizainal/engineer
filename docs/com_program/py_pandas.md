Topic: Computing<br>
Sub-Topic: Programming<br>
Date Written: 2019/06/14<br>
Date Edited: 2022/06/28<br>

---

### Pandas Library

Training by Keith Gaili from Youtube.The files needed for this training: <a href="https://github.com/KeithGalli/pandas/blob/master/pokemon_data.csv" target="_blank">Link.csv</a>

- [Add Column](/com_program/py_pandas?id=Add-Column)<br>
- [Add Content](/com_program/py_pandas?id=Add-Content)<br>
- [Arrange Column](/com_program/py_pandas?id=Arrange-Column)<br>
- [Export CSV](/com_program/py_pandas?id=Export-CSV)<br>
- [Export TXT](/com_program/py_pandas?id=Export-TXT)<br>
- [Export XLS](/com_program/py_pandas?id=Export-XLS)<br>
- [Filter Content](/com_program/py_pandas?id=Filter-Content)<br>

---

#### Add Column

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Add new column

df['Total'] = df['HP'] + df['Attack']

#Add new column using iloc
# : means all row
# axis = 1 means horizontally, axis = 0 means vertically

df['Total 2'] = df.iloc[:, 4:10].sum(axis = 1)

print(df)

```

---

#### Add Content

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#If certain column meet condition, put value to other columns
#Cannot add if rename to other variable

df.loc[df['HP'] > 50, ['Generation', 'Legendary' ]] = 'Test Value'

print(df)

```

---

#### Arrange Column

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Arrange Columns
# - index means colums from back
# if inside list only have 1 parameter it wil consider as string, so put bracket to make a list
# Last number in list bracket is always number that we dont want to include

cols = list(df.columns) #Convert columns to list
df = df[cols[0:4] + [cols[-1]] + cols[4:12]] #put bracket if parameter is only 1

print(df)

```

---

#### Export CSV

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

print(df)

#Save to csv

df.to_csv('TestExport.csv')

#Remove Index column while exporting

df.to_csv('TestExport.csv',index = False)

```

---

#### Export TXT

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

print(df)

#Save to Txt

df.to_csv('TestExport.txt')

#Remove Index column while exporting

df.to_csv('TestExport.txt', index = False, sep = '\t')


```

---

#### Export XLS

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

print(df)

#Save to Excel

df.to_excel('TestExport.xlsx')

#Remove Index column while exporting

df.to_excel('TestExport.xlsx',index = False)

```

---

#### Filter Content

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Filter Row that contains specific strings

x = df.loc[df['Name'].str.contains('Mega')]
print(x)

#Filter Row that NOT contains specific strings
#add  ~ syntax

y = df.loc[~df['Name'].str.contains('Mega')]
print(y)

```

---