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
- [Histogram Plot](/com_program/py_matplotlib?id=Histogram-Plot)<br>
- [Scatter Plot](/com_program/py_matplotlib?id=Scatter-Plot)<br>
- [Stack Plot](/com_program/py_matplotlib?id=Stack-Plot)<br>
- [Pie Plot](/com_program/py_matplotlib?id=Pie-Plot)<br>

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

#### Bar Plot

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

#### Histogram Plot

```python

import matplotlib.pyplot as plt

population_ages = [22, 55, 32, 56, 23, 67, 12, 98, 32, 54, 65, 67, 23, 124]
bins = [0, 20, 40, 60, 80, 100, 120, 140, 160]

#Histograms

plt.hist(population_ages, bins, histtype = "bar", rwidth = 0.9)

plt.xlabel("X_Title")
plt.ylabel("Y_Title")
plt.title("Bar Graph")
plt.legend()

plt.show()

```

Result:

<br>
<img src="\com_program\img_py\com_program_py_histplot.png" width=50% height=50% />
<br>

---

#### Scatter Plot

```python

import matplotlib.pyplot as plt

x = [2, 4, 6, 8, 10]
y = [6, 7, 8, 2, 4]
z = [3, 15, 2, 19, 20]

plt.scatter(x, y, label = 'skitscat', color = 'k', marker = '*', s = 500) #s = Size
plt.scatter(x, z, label = 'skitscat', color = 'r', marker = 'o', s = 100) #s = Size

plt.xlabel("X_Title")
plt.ylabel("Y_Title")
plt.title("Bar Graph")
plt.legend()

plt.show()

```

Result:

<br>
<img src="\com_program\img_py\com_program_py_scatplot.png" width=50% height=50% />
<br>

---

#### Stack Plot

```python

import matplotlib.pyplot as plt

days = [1, 2, 3, 4, 5]

sleeping = [7, 8, 6, 11, 7]
eating = [2, 3, 4, 3, 2]
working = [7, 8, 7, 2, 2]
playing = [8, 5, 7, 8, 13]

plt.stackplot(days, sleeping, eating, working, playing, colors = ['m', 'c', 'r', 'b'])
#x_axis = days
#y_axis = sleeping, eating, working, playing

#In Matplotlib Stack plot, we cannot label element of the data.
#Because of that, when we call plt.legend(), the legend will not come out
#To overcome this: create a fake plot as below so we can call plt.legend()

plt.plot([], [], label = 'Sleeping', color = 'm', linewidth = 5)
plt.plot([], [], label = 'Eating', color = 'c', linewidth = 5)
plt.plot([], [], label = 'Working', color = 'r', linewidth = 5)
plt.plot([], [], label = 'Playing', color = 'b', linewidth = 5)

plt.xlabel("X_Title")
plt.ylabel("Y_Title")
plt.title("Bar Graph")
plt.legend()

plt.show()

```

Result:

<br>
<img src="\com_program\img_py\com_program_py_stackplot.png" width=50% height=50% />
<br>

---

#### Pie Plot

```python

import matplotlib.pyplot as plt

#Able to define settings before plotting
slices = [7, 2, 2, 13]
activities = ['Sleeping', 'Eating', 'Working', 'Playing']
cols = ['c', 'm', 'r', 'k']

#Start angle in pie Charts can be defined
#Pie plot start drawing counterclockwise - from the right

#plt.pie(slices, labels = activities, colors = cols, startangle = 0)
plt.pie(slices, labels = activities, colors = cols, startangle = 270)

plt.title("Bar Graph")
plt.legend()

plt.show()

```

Result:

<br>
<img src="\com_program\img_py\com_program_py_pieplot.png" width=50% height=50% />
<br>

---