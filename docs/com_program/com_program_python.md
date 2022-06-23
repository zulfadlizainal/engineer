Topic: Computing<br>
Sub-Topic: Programming<br>
Date Written: 2019/06/14<br>
Date Edited: 2022/06/23<br>

---

### Fundamentals

Training by CodeMosh from Youtube.

- [Print Statement](/com_program/com_program_python.md?id=Print-Statement)<br>
- [Variable](/com_program/com_program_python.md?id=Variable)<br>
- [Input](/com_program/com_program_python.md?id=Input)<br>
- [Data Type](/com_program/com_program_python.md?id=Data-Type)<br>

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
