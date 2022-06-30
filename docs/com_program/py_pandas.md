Topic: Computing<br>
Sub-Topic: Programming<br>
Date Written: 2019/06/14<br>
Date Edited: 2022/06/30<br>

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
- [Filter Row](/com_program/py_pandas?id=Filter-Row)<br>
- [Group By Pivot](/com_program/py_pandas?id=Group-By-Pivot)<br>
- [Group By Stats](/com_program/py_pandas?id=Group-By-Stats)<br>
- [Import CSV](/com_program/py_pandas?id=Import-CSV)<br>
- [Import TXT](/com_program/py_pandas?id=Import-TXT)<br>
- [Import XLS](/com_program/py_pandas?id=Import-XLS)<br>
- [Iterate Row](/com_program/py_pandas?id=Iterate-Row)<br>
- [List To Pandas](/com_program/py_pandas?id=Iterate-Row)<br>
- [Dictionary To Pandas](/com_program/py_pandas?id=Dictionary-To-Pandas)<br>
- [Pivot](/com_program/py_pandas?id=Pivot)<br>
- [Pivot Table](/com_program/py_pandas?id=Pivot-Table)<br>
- [Print First / Last Row](/com_program/py_pandas?id=Prin-First-Last-Row)<br>
- [Read Cell](/com_program/py_pandas?id=Read-Cell)<br>
- [Read Column](/com_program/py_pandas?id=Read-Column)<br>
- [Read Row](/com_program/py_pandas?id=Read-Row)<br>
- [Remove Column](/com_program/py_pandas?id=Remove-Column)<br>
- [Replace Content](/com_program/py_pandas?id=Replace-Content)<br>
- [Reset Index](/com_program/py_pandas?id=Reset-Index)<br>
- [Sorting](/com_program/py_pandas?id=Sorting)<br>
- [Statistics](/com_program/py_pandas?id=Statistics)<br>

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

#### Filter Row

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Filter certain row that contains certain text

u = df.loc[df['Type 1'] == 'Fire']
print(u)

#Filter multiple rows using AND
#Seperate conditions by ()

v = df.loc[(df['Type 1'] == 'Grass') & (df['Type 2'] == 'Poison')]
print(v)

#Filter multiple rows using OR
#Seperate conditions by ()

w = df.loc[(df['Type 1'] == 'Grass') | (df['Type 2'] == 'Poison')]
print(w)

#Filter multiple rows with > < conditions
#Seperate conditions by ()

x = df.loc[(df['Type 1'] == 'Grass') & (df['Type 2'] == 'Poison') & (df['HP'] > 70)]
print(x)

```

---

#### Group By Pivot

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Groupby (Similar Like Pivot)

x = df.groupby(['Type 1']).count()['HP']
print(x)

#Groupby multiple category

x = df.groupby(['Type 1', 'Type 2']).count()['HP']
print(x)

```

---

#### Group By Stats

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Similar like doing pivot in excel

x = df.groupby(['Type 1']).mean()
print(x)

#Sort after group

y = df.groupby(['Type 1']).mean().sort_values('Defense', ascending = False)
print(y)

#Sum, Mean, Count, Min, Max

xsum = df.groupby(['Type 1']).sum()
print(xsum)

xmean = df.groupby(['Type 1']).mean()
print(xmean)

xcount = df.groupby(['Type 1']).count()
print(xcount)

xmin = df.groupby(['Type 1']).min()
print(xmin)

xmax = df.groupby(['Type 1']).max()
print(xmax)

```

---

#### Import CSV

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

print(df)

```

---

#### Import TXT

```python

import pandas as pd

df = pd.read_csv('TestPandaData.txt',delimiter = '\t') #seperate by tab/coma/semicolon

print(df)

```

---

#### Import XLS

```python

import pandas as pd

df = pd.read_excel('TestPandaData.xlsx')

print(df)

```

---

#### Iterate Row

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Go down row by row

for index, row in df.iterrows():
    print(index,row)

#Go down row by row for specific column

for index, row in df.iterrows():
    print(index,row['Name'])

```

---

#### List To Pandas

```python

import pandas as pd

#List

names=['Bob','Jessica','Mary','John','Tyler']
weights=[76,51,60,93,67]

#Use list + zip function to tie both list

nameweights=list(zip(names,weights))
print(nameweights)

#Change List to Pandas Dataframe

df=pd.DataFrame(nameweights)
print("__________________")
print(df)

#Change Column Name

df.columns=["Names","Weights"]
print("__________________")
print(df)

#Sort based on column

sorteddf = df.sort_values("Weights",ascending=False)
print("__________________")
print(sorteddf)

#Print first N row using  head subfunction

print("__________________")
print(sorteddf.head(3))

#Print last N row using  tail subfunction

print("__________________")
print(sorteddf.tail(3))

#Extract Maximum value in a column

print("__________________")
print(df["Weights"].max())

#Transpose Table - Use COmmand T

transdf=df.T
print("__________________")
print(transdf)

#Remove Row

remrowdf=df.drop(df.index[0])
print("__________________")
print(remrowdf)


#Add Row

newrow=["Van",73]
df.loc[5]=newrow
print("__________________")
print(df)

#Export Dataframe to CSV

df.to_csv("Name&Weights.csv",index=False)
print("Done")

#Export Dataframe to Excel

df.to_excel("Name&Weights_2.xlsx",sheet_name="testing", index=False, header=False)
print("Done")

#Import Dataframe from CSV

df1=pd.read_csv("housing_train.csv")
print(df1)

```

---

#### Dictionary To Pandas

```python

import pandas as pd

#Create Data Set with dictionary


d = {'Tokyo': 1000, 'Osaka': 1300, 'Yokohama': 900, 'Nagoya': 1100,
     'Sendai': 450, 'Sapporo': None}

#Series" can convert a data set to a dictonary format

cities=pd.Series(d)
print(cities)

```

---

#### Pivot

```python

import pandas as pd

df = pd.read_csv('TestPandaPivot.csv')

#index = rows, columns = columns, values = category

x = df.pivot(index = 'date', columns = 'city')
print(x)

#If only want to filter certain category, add values

y = df.pivot(index = 'city', columns = 'date', values = 'humidity')
print(y)

```

---

#### Pivot Table

```python

import pandas as pd

df = pd.read_csv('TestPandaPivot.csv')

#Create a pivot Table

x = df.pivot_table(index = 'city', columns = 'date')
print(x)

#Aggregate Statistics (Use aggfunc)

y = df.pivot_table(index = 'city', aggfunc = 'sum')
print(y)

```

---

#### Print First / Last Row

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

print(df.head(3)) #print first 3 row

print(df.tail(3)) #print last 3 row

```

---

#### Read Cell

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Read specific location

x = df.iloc[2,1]
print(x)

```

---

#### Read Column

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Read Headers

x = df.columns
print(x)

#read Each columns

x = df['Name']
#x = df.Name
print(x)

#read Each columns: First 5 rows

x = df['Name'][0:5]
print(x)

#read multiple columns (Double Bracket)

x = df[['Name','Type 1','HP']]
print(x)


```

---

#### Read Row

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#read each row (Use iloc: means Index Location)

x = df.iloc[5]
print(x)

#read multiple row

x = df.iloc[0:5]
print(x)

```

---

#### Remove Column

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Remove column (Need to assign new variable)

x = df.drop(columns=['HP'])
print(x)

#Remove column and overwrite in current dataframe (Good! no need to assign new variable and save memory)

df.drop(columns=['HP'], inplace = true)
print(df)

```

---

#### Replace Content

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Replace content in a row
#Cannot replace if rename to other variable

df.loc[df['Type 1'] == 'Fire', 'Type 1'] = 'Flamer'

print(df)

```

---

#### Reset Index

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Filter certain row that contains certain text

u = df.loc[df['Type 1'] == 'Fire']
print(u)

#After filtering index value mantain the same
#For additional processing, might be confusing

#We can reset index to 0,1,2,3... by..

u = u.reset_index() #this method keeps the old index column
print(u)

#To remove old index column, use this method

u = u.reset_index(drop = True)
print(u)

```

---

#### Sorting

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#sort by alphabatical

x = df.sort_values('Name')
print(x)

#sort ascending

x = df.sort_values('Speed', ascending = True)
print(x)

#sort decending

x = df.sort_values('HP', ascending = False)
print(x)

#sort multiple column

x = df.sort_values(['Type 1','HP'], ascending = [True,False])
print(x)

```

---

#### Statistics

```python

import pandas as pd

df = pd.read_csv('TestPandaData.csv')

#Use describe() to get basic stats of the data

x = df.describe()

print(x)

```

---