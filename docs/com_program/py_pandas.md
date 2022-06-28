Topic: Computing<br>
Sub-Topic: Programming<br>
Date Written: 2019/06/14<br>
Date Edited: 2022/06/28<br>

---

### Pandas Library

Training by Keith Gaili from Youtube.The files needed for this training: <a href="https://github.com/zulfadlizainal/engineer/blob/main/docs/com_program/resource_py/pandas_py/TestPandaData.csv" target="_blank">Link.csv</a>

- [Add Column](/com_program/py_pandas.md?id=Add-Column)<br>

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
