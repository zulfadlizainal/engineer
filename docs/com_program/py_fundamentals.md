Topic: Computing<br>
Sub-Topic: Programming<br>
Date Written: 2019/06/14<br>
Date Edited: 2022/06/28<br>

---

### Fundamentals

Training by CodeMosh from Youtube.

- [Print Statement](/com_program/py_fundamentals.md?id=Print-Statement)<br>
- [Variable](/com_program/py_fundamentals.md?id=Variable)<br>
- [Input](/com_program/py_fundamentals.md?id=Input)<br>
- [Data Type](/com_program/py_fundamentals.md?id=Data-Type)<br>
- [Strings](/com_program/py_fundamentals.md?id=Strings)<br>
- [Formatted String](/com_program/py_fundamentals.md?id=Formatted-String)<br>
- [Replace String](/com_program/py_fundamentals.md?id=Replace-String)<br>
- [Arithmethic](/com_program/py_fundamentals.md?id=Arithmethic)<br>
- [Rounding](/com_program/py_fundamentals.md?id=Rounding)<br>
- [Library](/com_program/py_fundamentals.md?id=Library)<br>
- [If Statement](/com_program/py_fundamentals.md?id=If-Statement)<br>
- [Logic](/com_program/py_fundamentals.md?id=Logic)<br>
- [Comparison](/com_program/py_fundamentals.md?id=Comparison)<br>
- [While Loop](/com_program/py_fundamentals.md?id=While-Loop)<br>
- [For Loop](/com_program/py_fundamentals.md?id=For-Loop)<br>
- [Nested Loop](/com_program/py_fundamentals.md?id=Nested-Loop)<br>
- [List](/com_program/py_fundamentals.md?id=List)<br>
- [2D List](/com_program/py_fundamentals.md?id=_2D-List)<br>
- [List Method](/com_program/py_fundamentals.md?id=List-Method)<br>
- [Tupples](/com_program/py_fundamentals.md?id=Tupples)<br>
- [Unpacking](/com_program/py_fundamentals.md?id=Unpacking)<br>
- [Dictionary](/com_program/py_fundamentals.md?id=Dictionary)<br>
- [Emoji Converter](/com_program/py_fundamentals.md?id=Emoji-Converter)<br>
- [Functions](/com_program/py_fundamentals.md?id=Functions)<br>
- [Error Handling](/com_program/py_fundamentals.md?id=Error-Handling)<br>
- [Classes](/com_program/py_fundamentals.md?id=Classes)<br>
- [__init__ Constructor](/com_program/py_fundamentals.md?id=init-Constructor)<br>
- [Class Example](/com_program/py_fundamentals.md?id=Class-Example)<br>
- [Class Inheritances](/com_program/py_fundamentals.md?id=Class-Inheritances)<br>
- [Modules](/com_program/py_fundamentals.md?id=Modules)<br>
- [Packages](/com_program/py_fundamentals.md?id=Packages)<br>

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

#### Replace String

```python

course = 'Python for Beginners'
print(course.replace('Beginners', 'Absolute Beginners'))

#---Tips---

#replace() function is case sensitive

#Example 1 - Replace a letter

course = 'Python for Beginners'
print(course.replace('P', 'J'))

```

---

#### Arithmethic

```python

print(10 / 3)             #Divide and got float
print(10 // 3)            #Divide and got integer
print(10 % 3)             #Modulus operator - return the remainder
print(10 ** 3)            #Power of

#Example 1 - Increement a number (Hard way)

x = 10
x = x + 3
print(x)

#Example 2 - Augmented assignment (Short cut)

x = 10
x += 3                    #add
print(x)

y = 10
y -= 3                    #subtract
print(y)


#---Tips---

#Order of operation (Math): Bracket (),  Power (**), Multiply or Division (* or /), Add or Subtract (+ or -)

```

---

#### Rounding

```python

x = 2.9
print(round(x))             #round to nearest integer

x = -2.9
print(abs(x))               #return +ve values

```

---

#### Library

```python

#Once we import library, we can access all func() using dot(.) operator

import math

print(math.ceil(2.9))
print(math.floor(2.9))

```

---

#### If Statement

```python

#Make decision based on condition

#Example 1 - if

is_hot = True                       #Boolean operator

if is_hot:
    print('Its a hot day')          #If condition met, execute this line

print('Enjoy your day')


is_hot = False                      #Boolean operator

if is_hot:
    print('Its a hot day')          #If condition met, excute this line

print('Enjoy your day')


#Example 2 - else

is_hot = True                       #Boolean operator

if is_hot:
    print('Its a hot day')          #If condition met, execute this line
    print('Drink a lot of water')
else:
    print('Its a cold day')
    print('Wear warm clothes')      #If condition not met, execute this line

print('Enjoy your day')


#Example 3 - elif (many conditions)

is_hot = False                       #Define condition
is_cold = True                       #Define condition

if is_hot:
    print('Its a hot day')          #If condition met, execute this line
    print('Drink a lot of water')
elif is_cold:
    print('Its a cold day')
    print('Wear warm clothes')      #If condition not met, execute this line
else:
    print('Its a lovely day')

print('Enjoy your day')


#Example 4 - if elif else using operations

price = 1000000

buyer_credit = input('Buyer Credit Status (Good/Poor): ')

if buyer_credit == 'Good':
    print('Downpayment (10%): $', 10/100*price)
elif buyer_credit == 'Poor':
    print('Downpayment (20%): $', 20/100*price)
else:
    print('Input Error')

```

---

#### Logic

```python

#Use logical operations (and, or, not)

#Example 1 - and

has_high_income = True
has_good_credit = True

if has_high_income and has_good_credit:
    print('Elegible for loan')
else:
    print('Not eligible for loan')


#Example 2 - or

has_high_income = True
has_good_credit = False

if has_high_income or has_good_credit:
    print('Elegible for loan')
else:
    print('Not eligible for loan')


#Example 3 - not

has_high_income = True
has_criminal_record = False

if has_high_income and not has_criminal_record:
    print('Eligible for loan')

```

---

#### Comparison

```python

#Use comparison metric

temperature = 30

if temperature > 30:
    print("It's a hot day.")
else:
    print("It's not a hot day.")


#Example 1 - Comparison integer

name = input('What is your name? : ')
name = len(name)

if name < 3:
    print('Name must be at least 3 charater long')
elif name > 50:
    print('Name can be maximum of 50 characters')
else:
    print('Name looks good')


#Example 2 - Comparison string

weight = input('What is your weight: ')
weight = float(weight)

unit = input('Is this in kilos (kg) or pounds (lbs): ')

if unit == 'kg':
    weight_lbs = weight*2.205
    print(f'Your weight is {weight_lbs} lbs')
elif unit == 'lbs':
    weight_kg = weight/2.205
    print(f'Your weight is {weight_kg} kg')
else:
    print('Unit Error')


#---Tips---

#Many Boolean Operatos (>=, <=, >, <, ==)

#Double == is only for conditions.. variable use single =


```

---

#### While Loop

```python

i = 1

while i <= 5:
    print(i)
    i += 1

print('Done')

#Example 1

i = 1

while i <= 5:
    print('*' * i)
    i += 1

print('Done')


#Example 2 - Guessing Game (Guess a secret number in with limit of only 3 attempts)

import random

secret_num = random.randint(1,10)
guess_start = 1
guess_max = 3

while guess_start <= 3:
    guess = int(input('Guess your number: '))
    guess_start += 1
    if guess == secret_num:
        print('Your guess is correct')
        break
else:
    print('Sorry you lose.')


#Example 3 - Car Game (While loop using String) - My answer

loop = True                                                         #Empty String
started = False

while loop == True:                                                 #Can simplify by only using - while True:

    action = input("Input Command (Type 'Help' for info): ")
    action = action.upper()                                         #Make the input always upper so that no matter how user input it will be ok for the loop

    if action == 'START':
        if started == True:
            print('Car already started..')
        else:
            started = True
            print('Engine start, ready to go')


    elif action == 'STOP':
        if started == False:
            print('Car already stopped..')
        else:
            started = False
            print('Engine stop')

    elif action == 'HELP':
        print('''
        Start - To start the car
        Stop - To stop the car
        Quit - To quit the program
        ''')

    elif action == 'QUIT':
        break

    else:
        print('I dont know this command')



#---Tips---

#Double == is only for conditions.. variable use single =

```

---

#### For Loop

```python

#For loop: Iterates over a collection

#Format: for <variable> in <collection> -> Means it will iterate a variable in a collection

#---Tips---

# for <variable> in <collection>. variable will hold the value of the collections, itterates every loop



#Example 1 - Iterates over string

for item in 'Python':
    print(item)


#Example 2 - Iterates over List of Strings

for item in ['Zul', 'Abu', 'Ali']:
    print(item)


#Example 3 - Iterates over List of Int

for item in [1, 2, 3, 4, 5, 6]:
    print(item)


#Example 4 - Iterates over a range

for item in range(10):                  #from 0 to 9
    print(item)

for item in range(5, 10):               #from 5 to 9
    print(item)

for item in range(5, 10, 2):            #from 5 to 9 with step
    print(item)


#Example 5 - Summation using for loop

prices = [10, 20, 30]
sum = 0

for total in prices:
    sum = sum + total

print(f'Sum: {sum}')

```

---

#### Nested Loop

```python

#Nested Looping

for x in range(4):                          #Outer loop
    for y in range(3):                      #Inner loop
        print(f'({x},{y})')

#Example 1 - Draw F using nested Looping

numbers = [5, 2, 5, 2, 2]

for x in numbers:
    output = ''                             #Empty string
    for y in range(x):
        output = output + 'x'
    print(output)

print('''

''')

#Example 2 - Draw L using nested Looping

numbers = [2, 2, 2, 2, 5]

for x in numbers:
    output = ''                             #Empty string
    for y in range(x):
        output = output + 'x'
    print(output)

```

---

#### List

```python

#Define List

names = ['Abu', 'Ali', 'Atan', 'Samad', 'Meon']
print(names)

#Access List using index

names = ['Abu', 'Ali', 'Atan', 'Samad', 'Meon']
print(names[0])                                 #First item
print(names[2])                                 #3rd item
print(names[-1])                                #Item from the back
print(names[2:])                                #Start from X Index to end
print(names[2:4])                               #Range of index (But not include last define index - python rules)
print(names[:])                                 #All Item

#Modify index in a List

names = ['Abu', 'Ali', 'Atan', 'Samad', 'Meon']
names[0] = 'Bakar'
print(names)


#Example 1 - Find largest number in a List

number = [5, 7, 3, 12, 5, 6, 7, 8, 9, 10]
count = number[0]

for max in number:
    if max > count:
        count = max

print(count)

```

---

#### 2D List

```python

#2D List is a list within a List
#Can consider 2D list as an array/matrix

matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(matrix)

#Accessing 2D list

matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

print(matrix[0])                            #Accessing the first layer List
print(matrix[0][1])                         #Accessing value in 2nd layer matrix

#Modify 2D list

matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

print(matrix[0])                            #Accessing the first layer List
print(matrix[0][1])                         #Accessing value in 2nd layer matrix

matrix[0][1] = 20
print(matrix)



#Example 1 - Using Nested loop to access all item in list

matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

for list in matrix:                         #Accessing the 1st layer List
    for value in list:                      #Accessing the content of the list
        print(value)

```

---

#### List Method

```python

#if put '.' after variable = it is called as Method

#append

numbers = [5, 2, 1, 7, 4]
numbers.append(20)                  #It will add number 20 at the end of the list
print(numbers)

#insert

numbers = [5, 2, 1, 7, 4]
numbers.insert(0, 10)              #It will insert number 10 at location 0
print(numbers)

#remove - Remove specific values in a list

numbers = [5, 2, 1, 7, 4]
numbers.remove(5)                  #It will remove 5 from the list
print(numbers)

#clear - Clear all items in a list

numbers = [5, 2, 1, 7, 4]
numbers.clear()                    #It will clear all values inside the list
print(numbers)

#pop - Remove last number from a list

numbers = [5, 2, 1, 7, 4]
numbers.pop()                      #It will clear all values inside the list
print(numbers)

#index - Return index of certain values in a list

numbers = [5, 2, 1, 7, 4]
print(numbers.index(5))

#Check existence of values in a list

numbers = [5, 2, 1, 7, 4]
print(50 in numbers)               #Generate a boolean

#count  - Count values in a list

numbers = [5, 2, 1, 5, 7, 4]
print(numbers.count(5))            #Count

#sort ascending - sort all items in a list

numbers = [5, 2, 1, 7, 4]
numbers.sort()                     #sort ascending
print(numbers)

#sort decending - sort all items in a list

numbers = [5, 2, 1, 7, 4]
numbers.sort()                     #sort ascending
numbers.reverse()
print(numbers)

#copy

numbers = [5, 2, 1, 7, 4]
numbers2 = numbers.copy()           #copy
numbers.append(10)
print(numbers)
print(numbers2)

#Excercise 1 - Remove Duplicates on a list

numbers = [2, 2, 4, 6, 3, 4, 6, 1]
uniques = []

for num in numbers:
    if num not in uniques:
        uniques.append(num)

print(uniques)

```

---

#### Tupples

```python

#Tupples is equal to List
#However, we cannot modify Tupples
#List using [], Tupples using ()

#Define Tupples

numbers = (1, 2, 3)

#Read index

numbers = (1, 2, 3)
print(numbers[0])

```

---

#### Unpacking

```python

#Unpacked a value in a Tupple/List into seperate variable

#Old method - Tupple

coordinates = (1, 2, 3)
x = coordinates[0]
y = coordinates[1]
z = coordinates[2]
print(x, y, z)

#Unpacking method - Tupple

coordinates = (1, 2, 3)
x, y, z = coordinates
print(x, y, z)

#Old method - List

coordinates = [1, 2, 3]
x = coordinates[0]
y = coordinates[1]
z = coordinates[2]
print(x, y, z)

#Unpacking method - List

coordinates = [1, 2, 3]
x, y, z = coordinates
print(x, y, z)

```

---

#### Dictionary

```python

#Setting a key-values pair
#To define Dictionary - use curly brackets {}
#Content of dictionary could be anything - String, Int, Float, Boolean, List etc

#Define dictionary

customer = {
    "Name": "Zulfadli",
    "Age": 30,
    "is_verified": True
}

#Access dictionary use []

print(customer["Name"])
print(customer["Age"])
print(customer["is_verified"])

#If called key in the dictionary that doesnt exist, error will pop out

#get - Method to access value (If Key not available, it will return None)

print(customer.get("Birthdate"))

#get - If the value is None & want to replace one with Default values

print(customer.get("Birthdate", "31 Dec 1988"))

#Adding key in defined dictionary

customer["Birthdate"] = "31 Dec 1988"
print(customer["Birthdate"])

#Excercise - Iterate Value in a string and access Dictionary

phone = input("Phone No: ")
ch_map = {
    "1": "One",
    "2": "Two",
    "3": "Three",
    "4": "Four",
    "5": "Five",
    "6": "Six",
    "7": "Seven",
    "8": "Eight",
    "9": "Nine",
}

output = ""             #Define empty string

for ch in phone:
    output += ch_map.get(ch, "!") + " "

print(output)

```

---

#### Emoji Converter

```python

# Define input message

message = input('> ')

# Split the input word based on spaces

words = message.split(' ')  # Split method will create a list of seperated word

# Define dictionary of emojis

emojis = {
    ':(': '😢',
    ':)': '😀'
}

# Loop word, and if find any word similar to dictionary: use that word. otherwise replace with original word

# Define a string output
output = ''

for word in words:
    output += emojis.get(word, word) + " "

print(output)

```

---

#### Functions

```python

# Functions is a set of specific task
# Purpose is to easy mantain the code and seperate file into small chunks of file

# Use keyword def to define a funtion

# Exampe 1


def greet_user():
    print('Hi There')
    print('Welcome Aboard')


# Call our functions
greet_user()

# Example 2

# It is better if the function can receive parameters to perform some task


# Define parameter (Parameter is defined inside Functions)
def greet_user2(name):
    print(f'Hi {name}')


# Call functions with argument (Argument is the input that we provide)
greet_user2('Zul')
greet_user2('Atan')
greet_user2('Abu')

# One of the benefit is to reuse this functions over and over again without re-writing them.
# Once we create functions with parameter, we obligated to supply arguments


# Example 3 (Multi parameter functions, position restricted)
def greet_user3(firstname, lastname):
    print(f'Hi there {firstname} {lastname}')


# This argument is a positional argument. It will follow the order when it is passed to the funtions
greet_user3('Zulfadli', 'Zainal')


# Example 4 (Keywords Argument)

# To be more specific, keyword argument can be used
# In this case, position doesnt really matter
# Keyword argument is really good way to improve the readability of the code
# Dont mix positional arguments and keyword arguments - Error will occur


def greet_user4(firstname, lastname):
    print(f'Hi there {firstname} {lastname}')


# Define the argument together with parameters
greet_user4(lastname='Zainal', firstname='Zulfadli')


# Example 5 (Return Statement)

# To return something back to the functions
# If there is no return in the fuction, but we still print the function - Python by default will return None


def square(number):
    return number*number


x = square(5)
print(x)

```

---

#### Error Handling

```python

# Example 1

# Normally when we write codes, we need certain type of input to be passed
# However user sometimes input wrong input (For example: User input string instead of integer)

age = int(input('Age: '))
print(age)

# How to handle this? Use Try / Except Function -> Go to Example 2


# Example 2 (It will handle the error without crashing the program and having to start over)

try:
    age = int(input('Age: '))
    print(age)
except ValueError:  # Depends on the type of error message that you get
    print('Invalid Value')


# Example 3 (Different error have different handling)

try:
    age = int(input('Age: '))
    income = 20000
    risk = income/age
    print(age)
except ValueError:  # Depends on the type of error message that you get
    print('Invalid Value')
except ZeroDivisionError:
    print('Age cannot be Zero')

```

---

#### Classes

```python

# Define Class
# In variable and function we use small letters and if more than 1 word, we use _
# In class, we use Capital letter in beginning of each word
# Class is like a net Type (Int, String, etc)

class Point:
    def move(self):  # Self is needed for functions/method inside a class
        print('move')

    def draw(self):
        print('draw')  # Self is needed for functions/method inside a class


# Class is a blueprint to define and object

# To define object ->

point1 = Point()

# Calling a method inside a class ->

point1.draw()

# Can also define attributes based on the pobject ->

point1.x = 10
point1.y = 20
print(point1.x)

# Conclusion

# Inside Class -> Define Functions
# Object can be defined based on class
# Every objects can have their own attributes

```

---

#### __init__ Constructor

```python

# Instead of define attributes outside the class, it can be done inside the class by using Class Constructors (__init__)

# Define Class


class Point:
    def __init__(self, x, y):  # Define Init
        self.x = x
        self.y = y

    def move(self):
        print('move')

    def draw(self):
        print('draw')


# Define Object with attributes
# Attributes will be linked in methods/functions inside class

point = Point(10, 20)
print(point.x)


# Attributes can be changed late
# Init can be used to initialize default value

point.x = 200
print(point.x)

```

---

#### Class Example

```python

# Define Class


class Person:
    def __init__(self, name):
        self.name = name

    def talk(self):
        print(f'Hi, I am {self.name}')


# Define Object with attributes
john = Person("John Smith")
john.talk()


# Define another object with attributes
bob = Person('Bobby')
bob.talk()


# This is the concept of object oriented programming

```

---

#### Class Inheritances

```python

# In programming, there is this common rule of DRY (Dont repeat yourself)
# If you need to repeat the same line of code, this is bad
# Because if have mistakes, we need to correct all of them.


# Example 1: Bad Class (Repeat same method inside different class)

class Anjing:
    def walk(self):
        print('walk')


class Kucing:
    def walk(self):
        print('walk')


# Example 2: Inheritances (To solve previous problem)

# Define a class that contain common method

class Mammal:
    def walk(self):
        print('walk')


class Cat(Mammal):  # Input Class with inheritances
    pass  # Class cannot be empty, so put pass inside a class


class Dog(Mammal):  # Input Class with inheritances
    pass  # Class cannot be empty, so put pass inside a class


dog1 = Dog()
dog1.walk()

```

---

#### Modules

File Structure:

<br>
<img src="\com_program\img_py\com_program_py_modules.png" width=20% height=20% />
<br>

> main.py

```python

# Modules work like importing library
# Better organize the files

# Import the whole library

from Functions import lbs_to_kg
import Functions

x = Functions.lbs_to_kg(100)        # Need to call the library + method
print(x)


# Import a function from the library


x = lbs_to_kg(100)          # Only call the function name
print(x)

```

> modules.py

```python

def lbs_to_kg(weight):
    return weight * 0.45


def kg_to_lbs(weight):
    return weight / 0.45

```

---

#### Packages

File Structure:

<br>
<img src="\com_program\img_py\com_program_py_packages.png" width=20% height=20% />
<br>

> main.py

```python

# Packages is like a folder full of Modules - Easy to mantain
# Its like a big library
# Python knows it is a packages if we have empty __init__.py in the folder
# Then inside the folder, we can put many modules (usually different kind of functions) and we can call from main

import package.module1
# Import specific module

package.module1.calc_shipping()

# Import specific function inside a module (Best)

from package.module1 import calc_shipping
calc_shipping()

# Import specific modules

from package import module1
module1.calc_shipping()

```

> __init__.py

```python



```

> module1.py

```python

def calc_shipping():
    print('calc_shipping')


```

---