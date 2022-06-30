Topic: Computing<br>
Sub-Topic: Programming<br>
Date Written: 2019/06/14<br>
Date Edited: 2022/06/30<br>

---

### Matplotlib Library

Training by Sentdex from Youtube.

- [Line Plot](/com_program/py_matplotlib?id=Line-Plot)<br>
- [Title and Label](/com_program/py_matplotlib?id=Title-and-Label)<br>
- [Legend](/com_program/py_matplotlib?id=Legend)<br>
- [Bar Plot](/com_program/py_matplotlib?id=Bar-Plot)<br>

---

#### Line Plot

```python

import matplotlib.pyplot as plt

x = [1, 2, 3]
y = [5, 7, 4]

plt.plot(x, y)           #Drawing in background

plt.show()              #Actually show the graph to the user

```

Result:

<br>
<img src="\com_program\img_py\com_program_py_lineplot.png" width=50% height=50% />
<br>

---

#### Title and Label

```python

import matplotlib.pyplot as plt

x = [1, 2, 3]
y = [5, 7, 4]

# Plot with Label & Titles

plt.plot(x, y)  # Drawing in background

plt.xlabel("X_Title")
plt.ylabel("Y_Title")
plt.title("Graph Title")

plt.show()  # Actually show the graph to the user

# Add Subtitles

plt.plot(x, y)  # Drawing in background

plt.xlabel("X_Title")
plt.ylabel("Y_Title")
plt.title("Graph Title\nGraph Subtitles")  # Add Subtitles using \n

plt.show()  # Actually show the graph to the user

```

Result:

<br>
<img src="\com_program\img_py\com_program_py_titlelabel.png" width=50% height=50% />
<br>

<br>
<img src="\com_program\img_py\com_program_py_titlelabel2.png" width=50% height=50% />
<br>

---

#### Legend

```python

import matplotlib.pyplot as plt

x = [1, 2, 3]
y = [5, 7, 4]

x2 = [1, 2, 3]
y2 = [10, 25, 30]

# Plot with Label & Titles

plt.plot(x, y, label="First Line")  # Drawing in background
plt.plot(x2, y2, label="Second Line")

plt.xlabel("X_Title")
plt.ylabel("Y_Title")
plt.title("Graph Title\nGraph Subtitles")
plt.legend()

plt.show()  # Actually show the graph to the user

```

Result:

<br>
<img src="\com_program\img_py\com_program_py_legend.png" width=50% height=50% />
<br>

---

#### X

```python

import matplotlib.pyplot as plt

x = [2, 4, 6, 8, 10]
y = [6, 7, 8, 2, 4]

x2 = [1, 3, 5, 7, 9]
y2 = [100, 50, 30, 60, 17]

#Normal Bar Charts

plt.bar(x, y, label = "Bar 1", color = "red")
plt.bar(x2, y2, label = "Bar 2", color = "cyan")

plt.xlabel("X_Title")
plt.ylabel("Y_Title")
plt.title("Bar Graph")
plt.legend()

plt.show()              #Actually show the graph to the user

```

Result:

<br>
<img src="\com_program\img_py\com_program_py_barplot.png" width=50% height=50% />
<br>

---