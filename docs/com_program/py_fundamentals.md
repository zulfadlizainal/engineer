Topic: Computing<br>
Sub-Topic: Programming<br>
Date Written: 2019/06/14<br>
Date Edited: 2022/06/24<br>

---

### Fundamentals

Training by CodeMosh from Youtube.

- [Print Statement](/com_program/py_fundamentals.md?id=Print-Statement)<br>
- [Variable](/com_program/py_fundamentals.md?id=Variable)<br>
- [Input](/com_program/py_fundamentals.md?id=Input)<br>
- [Data Type](/com_program/py_fundamentals.md?id=Data-Type)<br>
- [Strings](/com_program/py_fundamentals.md?id=Strings)<br>
- [Formatted String](/com_program/py_fundamentals.md?id=FormattedString)<br>

#### Print Statement

```python

print('Zulfadli') #Print String
print('*' * 10) #Print String repeatedly

```

#### Variable

```python

price = 10
print(price) #Print Variable

#Update Variable
price = 20
print(price) #Variable will be replaced

#Data Type
price = 10              #Int
rating = 4.9            #Float
name = 'Mosh'           #String
is_published = True     #Boolean

#Example 1

name = 'John Smith'
age = 20
patient_type = 'New'
print(name, age, patient_type)

#---Tips---

#Python is case sensitive language
#Make every variable low case because some parameer in Python using higher case (Boolean)

```

#### Input

```python

#Use input function

name = input('What is your name? ')
print('Hi ' + name)

#Example 1

name = input('What is your name? ')
colour = input('What is your favourite colour? ')
print(name + ' likes ' + colour)

```

#### Data Type

```python

birth_year = input('Birth year: ')
age = 2019 - int(birth_year)                  #Convert string to integer
print('Your age is ', age, ' years old.')


#Example 1 - Print Data Type

birth_year = input('Birth year: ')
print(type(birth_year))                       #Print Data Type

age = 2019 - int(birth_year)                  #Convert string to integer
print(type(age))                              #Print Data Type

print('Your age is ', age, ' years old.')


#Example 2 - Get input and do opertions

weight_pound = input('What is your weight? (lbs) :')
weight_kg = int(weight_pound) / 2.205
print('Your weight is ', weight_kg, ' kg.')

#---Tips---

#Converting data type from string to different types using below functions

# 1. int()   -> Convert string to integer
# 2. float() -> Convert string to float
# 3. bool()  -> Convert string to Boolean

#When use input functions, python always accept value as string, so if want to perform operation, always convert to int of float.

```

---

#### Strings

```python

#Example 1 - Incase need to use ' in a string, need to use double quote

course = "Python's Course for Beginners"
print(course)

#Or vice versa

course = 'Pythons Course for "Beginners"'
print(course)


#Example 2 - For multiline string, use triple quote

print('''

Hi Zul,

Thanks for learning python.

I will practice 2 hours a day.

Regards,
Zul

''')


#Example 3 - Extract value from String

course = 'Python Course for Beginners'
print(course[0])                                #Return first letter from the strings

course = 'Python Course for Beginners'
print(course[-1])                                #Return last letter from the strings

course = 'Python Course for Beginners'
print(course[0:3])                               #Return range of letter from the strings

course = 'Pythons Course for Beginners'
print(course[:3])                                #Return range of letter from the strings, assume index [0] is the beginning

course = 'Pythons Course for Beginners'
print(course[:])                                 #Return range of letter from the strings, assume index [0] is the beginning and index [-1] as end

#---Tips---

# [0:3] Python will always exclude the last range define in index, in this case python will only return index [0], [1], [2]. [3] will not be returned.


```

---

#### Formatted String

```python

#Example 1 - Concanated string (Long way)

first = 'John'
last = 'Smith'
message  = first + ' [' + last + '] is a coder.'        #concatenate string + variable
print(message)

#Example 2 - Formatted string (Easy way)

first = 'John'
last = 'Smith'
msg = f'{first} [{last}] is a coder.'                   #input variable intu formatted strings
print(message)

```

---