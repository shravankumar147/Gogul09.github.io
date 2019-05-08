---
layout: post-doc
category: software
class: Programming Languages
title: Python Learning Notes
description: Understand the syntax, modules and how to's of Python programming language which is heavily used in today's technology industry.
author: Gogul Ilango
permalink: /software/python-learning-notes
image: https://drive.google.com/uc?id=1-OEoUjX1r1V-Nx6kJIwUmEVt44rZnJxk
---

<div id="awesomeSideNav" class="sidenav">
    <a href="javascript:void(0)" class="closebtn" onclick="closeSideNav()">&times;</a>
    <h3><a href="#basics">Basics</a></h3>
    <ul>
        <li><a href="#hello-world">Hello World</a></li>
        <li><a href="#data-types">Data types</a></li>
        <li><a href="#multiple-variable-assignments">Multiple variable assignments</a></li>
        <li><a href="#math-operations">Math operations</a></li>
        <li><a href="#logical-operations">Logical operations</a></li>
        <li><a href="#conditions">Conditions</a></li>
        <li><a href="#loops">Loops</a></li>
        <li><a href="#string-operations">Strings</a></li>
        <li><a href="#lists">List</a></li>
        <li><a href="#tuples">Tuple</a></li>
        <li><a href="#dictionaries">Dictionary</a></li>
        <li><a href="#set">Set</a></li>
        <li><a href="#functions_1">Functions</a></li>
        <li><a href="#regular-expressions">Regular Expressions</a></li>
    </ul>
    <h3><a href="#intermediate">Intermediate</a></h3>
    <ul>
        <li><a href="#comprehensions">Comprehensions</a></li>
    </ul>
    <h3><a href="#modules">Modules</a></h3>
    <ul>
        <li><a href="#os-module">OS module</a></li>
    </ul>
    <h3><a href="#oop">OOP</a></h3>
    <ul>
        <li><a href="#classes">Classes</a></li>
        <li><a href="#class-variables">Class Variables</a></li>
    </ul>
    <h3><a href="#how-tos">How to's</a></h3>
    <ul>
        <li><a href="#how-to-read-file-line-by-line">How to read file line-by-line?</a></li>
        <li><a href="#how-to-write-file-line-by-line">How to write file line-by-line?</a></li>
        <li><a href="#how-to-load-json-file">How to load json file?</a></li>
        <li><a href="#how-to-check-if-list-is-empty">How to check if list is empty?</a></li>
        <li><a href="#how-to-access-index-in-for-loop">How to access index in for loop?</a></li>
        <li><a href="#how-to-sort-a-dictionary-by-key-alphabetically">How to sort a dictionary by key alphabetically?</a></li>
    </ul>
</div>

<div class="sidebar_tracker" id="sidebar_tracker">
  <button onclick="closeSidebar('sidebar_tracker_content')">X</button>
  <p onclick="showSidebar('sidebar_tracker_content')">Contents</p>
  <ul id="sidebar_tracker_content">
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_1" href="#basics">Basics</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_2" href="#modules">Modules</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_3" href="#oop">OOP</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_4" href="#how-tos">How To's</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_5" href="#resources">Resources</a></li>
  </ul>
</div>
 
In this page, you will find the **syntax**, **modules** and most common **how to's** of Python programming language. This might be helpful for you to find python syntax and code quickly in a single web page. Click on any of the contents in the sidebar to view the python code.

<div class="note">
<p><b>Note:</b> If you are new to programming, learning Python is the best way to start. Because, Python is easier to learn than any other programming language out there as it is concise, expressive, productive, has larger community, has rich set of libraries, frameworks and requires less time to write code.</p>
<ul>
    <li><a href="https://medium.com/@trungluongquang/why-python-is-popular-despite-being-super-slow-83a8320412a9" target="_blank">Why Python is Popular Despite Being (Super) Slow</a></li>
    <li><a href="https://www.kdnuggets.com/2017/07/6-reasons-python-suddenly-super-popular.html" target="_blank">6 Reasons Why Python Is Suddenly Super Popular</a></li>
    <li><a href="https://www.zarantech.com/blog/surprising-facts-python-gaining-popularity-among-developers/" target="_blank">Surprising Facts Why Python is gaining more popularity among Developers</a></li>
</ul>
</div>

<h3 class="centered-heading" id="basics"><span>Basics</span></h3>

<h3 class="code-head" id="hello-world">Hello World<span>code</span></h3>

```python
print("Hello World")
# prints "Hello World"
# above line is a comment
'''
This is a multi-line
comment in python
'''
```

<h3 class="code-head" id="data-types">Data types<span>code</span></h3>

```python
# declare an integer
a = 12
print a       # prints "12"
print type(a) # prints <type 'int'>

# declare a float
b = 1.7
print b       # prints "1.7"
print type(b) # prints <type 'float'>

# declare a string
c = "Python"
print c       # prints "Python"
print type(c) # prints <type 'str'>

# declare a boolean
d = True
print d       # prints "True"
print type(d) # prints <type 'bool'>
```

<h3 class="code-head" id="multiple-variable-assignments">Multiple variable assignments<span>code</span></h3>

```python
# assign values to multiple variables in a single line
a, b, c = 1, 2, 3

# assign values with different data types to multiple variables in a single line
a, b, c = 1, 3.5, "hello"

print type(a) # prints <type 'int'>
print type(b) # prints <type 'float'>
print type(c) # prints <type 'str'>
```

<h3 class="code-head" id="math-operations">Math operations<span>code</span></h3>

```python
a = 10

print a + 1  # Addition: prints "11"
print a - 1  # Subtraction: prints "9"
print a * 2  # Multiplication: prints "20"
print a / 2  # Division: prints "5"
print a  2 # Exponentiation: prints "100"
```

<h3 class="code-head" id="logical-operations">Logical operations<span>code</span></h3>

```python
# declare some boolean variables
x = True
y = False

print x and y  # prints "False"
print x or y   # prints "True"
print not x    # prints "False"
print x & y    # prints "False"
```

<h3 class="code-head" id="conditions">Conditions<span>code</span></h3>

```python
# if-elif-else statements

import random
a = [50, 100, 200, 300]

# pick a random number from the list "a"
b = random.choice(a)

# the conditionals
if (b < 100):
    print("Number - " + str(a) + " is less than 100")
elif (b >= 100 and b < 200):
    print("Number - " + str(b) + " is greater than or equal to 100 but less than 200")
else:
    print("Number -" + str(b) + " is greater than or equal to 200")

# for me it prints
# Number - 100 is greater than or equal to 100 but less than 200
```

<h3 class="code-head" id="loops">Loops<span>code</span></h3>

```python
# while loop
c = 0
while (c < 10):
    print (c,  end='')
    c += 1

# prints 0123456789

# for loop
numbers = [1, 2, 4]
for x in numbers:
    print x

# prints 1
#        2
#        4

x = 5
for c in range(x):
    print (c)

# prints 0
#        1
#        2
#        3
#        4
```

<h3 class="code-head" id="strings">Strings<span>code</span></h3>

```python
# declare two strings
a = "Python"
b = " is awesome!"

print len(a)                        # Length of the string: prints "6"
print len(b)                        # prints "12"
print a + b                         # String concatenation: prints "Python is awesome!"
print a, b                          # prints "Python  is awesome!"
print "{}{}".format(a, b)           # prints "Python is awesome!"
print "%s%s" % (a, b)               # sprintf style formatting: prints "Python is awesome!"
print a.upper()                     # converts all characters to uppercase: prints "PYTHON"
print a.lower()                     # converts all characters to lowercase: prints "python"
print b.strip()                     # removes trailing and leading whitespaces: prints "is awesome!"
print b.replace("awesome", "great") # replace a substring with a new string: prints " is great!"
```

<h3 class="code-head" id="lists">Lists<span>code</span></h3>

```python
# declare a list
l = [1,2,3,4,5]

# length of list
print len(l)      # prints "5"

# indexing
print l[0]        # prints "1"
print l[1]        # prints "2"
print l[len(l)-1] # prints "5"
print l[-1]       # negative indexing: prints "5"

# insert and remove
l.append(6)        # inserts "6" at last
print l            # prints "[1,2,3,4,5,6]"
item = l.pop()     # removes last element and returns that element
print item         # prints "6"
l.append("string") # adds different data type too
print l            # prints "[1,2,3,4,5,'string']"
l.pop()            # removes last string element

# slicing list
print l[1:2]       # prints "2"
print l[1:3]       # prints "2,3"
print l[0:]        # prints "[1,2,3,4,5,'string']"
print l[0:-1]      # prints "[1,2,3,4,5]"
print l[:]         # prints "[1,2,3,4,5,'string']"

# loop over the list
for item in l:
    print item     # prints each item in list one by one

# enumerate over the list
for i, item in enumerate(l):
    print "{}-{}".format(i, item) # prints each item with its index


# squaring elements in a list
for item in l:
    if item%2 == 0:
        print item2      # square each even number in the list

# above can be achieved using a list comprehension too! (one-line)
print [x2 for x in l if x%2==0]

# sort the list
b = [5, 7, 2, 4, 9]

# ascending order
b.sort()
print b  # prints [2, 4, 5, 7, 9]

# descending order
b.sort(reverse=True)
print b # prints [9, 7, 5, 4, 2]

# reverse the list (notice this is not descending order sort)
a = ["dhoni", "sachin", "warner", "abd"]
a.reverse()
print a # prints ['abd', 'warner', 'sachin', 'dhoni']

# count of object in list
a = [66, 55, 44, 22, 11, 55, 22] 
print a.count(22) # prints 2
```

<h3 class="code-head" id="tuples">Tuples<span>code</span></h3>

```python
# declare a tuple
t = (500, 200)

print type(t)    # prints "<type 'tuple'>"
print t[1]       # prints 200

# tuple of tuples
tt = ((200,100), t)

print tt         # prints "((200, 100), (500, 200))"
print tt[1]      # prints "(500, 200)"

# loop over tuple
for item in t:
    print item   # prints each item in the tuple


# built-in tuple commands
print len(t) # prints the length of tuple which is 2
print max(t) # prints the max-valued element which is 500
print min(t) # prints the min-valued element which is 200

# convert list to tuple
l = [400, 800, 1200]
l_to_t = tuple(l)

print type(l_to_t) # prints <class 'tuple'>
```

<h3 class="code-head" id="dictionaries">Dictionaries<span>code</span></h3>

```python
# declare a dictionary
d = {"1" : "Pikachu", "2": "Charmander", "3": "Squirtle"}

print type(d)    # prints "<type 'dict'>"
print d["1"]     # prints "Pikachu"

# loop over dictionary
for key in d:
    print key    # prints each key in d
    print d[key] # prints value of each key in d (unsorted)
```

<h3 class="code-head" id="functions_1">Functions<span>code</span></h3>


```python
def squared(x):
    return x*x

print squared(2)   # prints "4"
```

<div class="code-head" id="regular-expressions">
    <span title="click to see re rules" id="btn-re-python" onclick="boxHandler(this.id)">re rules    
    </span>
    <div class="rule-box" id="box-re-python">
        <p><b>Identifiers</b></p>
        <div style="text-align: center; width: 100%">
            <table>
                <tr>
                    <td>\d</td>
                    <td>any number</td>
                </tr>
                <tr>
                    <td>\D</td>
                    <td>anything but a number</td>
                </tr>
                <tr>
                    <td>\s</td>
                    <td>space</td>
                </tr>
                <tr>
                    <td>\S</td>
                    <td>anything but a space</td>
                </tr>
                <tr>
                    <td>\w</td>
                    <td>any character</td>
                </tr>
                <tr>
                    <td>\W</td>
                    <td>anything but a character</td>
                </tr>
                <tr>
                    <td>.</td>
                    <td>any character, except for a newline</td>
                </tr>
                <tr>
                    <td>\b</td>
                    <td>the whitespace around words</td>
                </tr>
                <tr>
                    <td>\.</td>
                    <td>a period</td>
                </tr>
            </table>
        </div>
        <p><b>Modifiers</b></p>
        <div style="text-align: center; width: 100%">
            <table>
                <tr>
                    <td>{1,3}</td>
                    <td>expecting 1-3 digits ~ \d{1,3}</td>
                </tr>
                <tr>
                    <td>+</td>
                    <td>match 1 or more</td>
                </tr>
                <tr>
                    <td>?</td>
                    <td>match 0 or 1</td>
                </tr>
                <tr>
                    <td>*</td>
                    <td>match 0 or more</td>
                </tr>
                <tr>
                    <td>$</td>
                    <td>match the end of a string</td>
                </tr>
                <tr>
                    <td>^</td>
                    <td>match the start of a string</td>
                </tr>
                <tr>
                    <td>|</td>
                    <td>either or (\d{1-3} | \w{5-6})</td>
                </tr>
                <tr>
                    <td>[]</td>
                    <td>range or variance</td>
                </tr>
                <tr>
                    <td>{x}</td>
                    <td>expecting "x" amount (of digits)</td>
                </tr>
            </table>
        </div>
        <p><b>White Space Characters</b></p>
        <div style="text-align: center; width: 100%">
            <table>
                <tr>
                    <td>\n</td>
                    <td>new line</td>
                </tr>
                <tr>
                    <td>\s</td>
                    <td>space</td>
                </tr>
                <tr>
                    <td>\t</td>
                    <td>tab</td>
                </tr>
                <tr>
                    <td>\e</td>
                    <td>escape</td>
                </tr>
                <tr>
                    <td>\f</td>
                    <td>form feed</td>
                </tr>
                <tr>
                    <td>\r</td>
                    <td>return</td>
                </tr>
            </table>
        </div>
    </div>
Regular Expressions</div>


```python
import re 

# multi-line string example
str = '''
Rahul is 19 years old, and Ashok is 24 years old.
Manoj is 65, and his grandfather, Naveen, is 77.
'''

# findall()
ages  = re.findall(r'\d{1,3}', str)
names = re.findall(r'[A-Z][a-z]*', str) 

print ages  # prints ['Rahul', 'Ashok', 'Manoj', 'Naveen']
print names # prints ['19', '24', '65', '77']

# split()
str = "This is an example string"
splitted = re.split(r'\s*', str)
print splitted # prints ['This', 'is', 'an', 'example', 'string']

# match()
str = "Dogs are braver than Cats"
matches = re.match(r'[A-Z][a-z]*', str)
print matches.group() # prints "Dogs"

# search()
str = "For data science help, reach support@datacamp.com"
searches = re.search(r'([\w\.-]+)@([\w\.-]+)', str)
print searches.group()  # prints support@datacamp.com
print searches.group(1) # prints support
print searches.group(2) # prints datacamp.com
```

<!-- --------------------------------------------------------------------- -->

<h3 class="centered-heading" id="intermediate"><span>Intermediate</span></h3>

<h3 class="code-head" id="comprehensions">Comprehensions<span>code</span></h3>

```python
nums = [1, 2, 3, 4, 5, 6, 7]

# traditional for loop
l = []
for n in nums:
    l.append(n)
print(l) # prints '[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]'

# meet list comprehension
l = [n for n in nums]
print(l) # prints '[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]'

# get square of each number
l = [n*n for n in nums]
print(l) # prints '[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]'

# same thing achieved using 'map' + 'lambda'
# 'map' means running everything in the list for a certain function
# 'lambda' means an anonymous function
l = map(lambda n: n*n, nums)
for x in l:
    print(x) 

# prints 
# 1
# 4
# 9
# 16
# 25
# 36
# 49
# 64
# 81
# 100

# using 'if' in list comprehension
l = [n for n in nums if n%2 == 0]
print(l) # prints '[2, 4, 6, 8, 10]'

# returning tuples with two for loops in list comprehension
l = []
for letter in "ab":
    for num in range(2):
        l.append((letter, num))
print(l) # prints '[('a', 0), ('a', 1), ('b', 0), ('b', 1)]'

# same thing using list comp
l = [(letter, num) for letter in "ab" for num in range(2)]
print(l) # prints '[('a', 0), ('a', 1), ('b', 0), ('b', 1)]'
```


<!-- --------------------------------------------------------------------- -->


<h3 class="centered-heading" id="modules"><span>Modules</span></h3>

<h3 class="code-head" id="os-module">OS module<span>code</span></h3>

```python
# os module is a powerful module in python
import os

# get current working directory
print(os.getcwd()) # prints 'G:\\workspace\\Python'

# change current working directory
os.chdir("G:\\workspace\\python\\learning")
print(os.getcwd()) # prints 'G:\\workspace\\python\\learning'

# list directories in the current working directory
print(os.listdir()) # prints ['built-ins', 'Lists', 'numpy', 'strings']

# create a directory in the current working directory
os.mkdir("dicts")
os.makedirs("dicts/nested-dicts")

# remove a directory in the current working directory
os.rmdir("dicts")
os.removedirs("dicts/nested-dicts")

# rename a file or directory
os.rename("Lists", "lists")

# stats of a file or directory
os.stat("lists")
# prints 'os.stat_result(st_mode=16895, st_ino=281474977861215, st_dev=4143122855, st_nlink=1, st_uid=0, st_gid=0, st_size=0, st_atime=1480252546, st_mtime=1480252546, st_ctime=1480252090)'

# traverse a directory tree
for dirpath, dirnames, filenames in os.walk("G:\\workspace\\python\\learning"):
    print("Current Path: ", dirpath)
    print("Directories: ", dirnames)
    print("Files: ", filenames)
    print()

'''
prints 
Current Path:  G:\workspace\python\learning
Directories:  ['Built-ins', 'lists', 'NumPy', 'Strings']
Files:  []

Current Path:  G:\workspace\python\learning\Built-ins
Directories:  []
Files:  ['evalu.py', 'input.py', 'zipped.py']

Current Path:  G:\workspace\python\learning\lists
Directories:  []
Files:  ['list_01.py', 'tuple_01.py']

Current Path:  G:\workspace\python\learning\NumPy
Directories:  []
Files:  ['ceilr.py', 'concatenate.py', 'eye_identity.py', 'flatten.py', 'math.py', 'mean_var_std.py', 'min_max.py', 'rev_array.py', 'sum_prod.py', 'zeros_ones.py']

Current Path:  G:\workspace\python\learning\Strings
Directories:  []
Files:  ['formatting.py']
'''

# check if a file exist
print(os.path.isfile("G:\\workspace\\python\\learning\\Strings\\formatting.py"))
# prints 'True'

# check if a directory exist
print(os.path.exists("G:\\workspace\\python\\learning\\Strings"))
print(os.path.isdir("G:\\workspace\\python\\learning\\Strings"))
# both prints 'True'

# accessing environment variable
print(os.environ.get("HOME"))
# prints 'C:\\Users\\Gogul Ilango'
```

<!-- --------------------------------------------------------------------- -->

<h3 class="centered-heading" id="oop"><span>OOP</span></h3>

<h3 class="code-head" id="classes">Classes<span>code</span></h3>

```python
# create a class
class Customer(object):

    # init method is a must
    def __init__(self, name, age):
        self.name = name
        self.age  = age

    # a simple print method
    def print_customer(self):
        print ("Customer: {}, Age: {}".format(self.name, self.age))

# define an instance
a = Customer("Gogul", "24")
a.print_customer() # prints "Customer: Gogul, Age: 24"
```

<h3 class="code-head" id="class-variables">Class Variables<span>code</span></h3>

```python
class Customer(object):

    # this is a class variable
    raise_amount = 1.05
    num_of_custs = 0

    def __init__(self, name, age, pay):
        self.name = name
        self.age  = age
        self.pay  = pay

        Customer.num_of_custs += 1

    def apply_raise(self):
        print ("Customer {} new pay is {}".format(self.name, float(self.pay) * self.raise_amount))

if __name__ == '__main__':
    # class variable not updated
    a = Customer("Gogul", "24", "5000")
    a.apply_raise() # prints Customer Gogul new pay is 5250.0

    # class variable updated
    b = Customer("Mahadevan", "25", "6000")
    b.raise_amount = 2.05
    b.apply_raise() # Customer Mahadevan new pay is 12299.999999999998

    # print dict of an instance
    print (a.__dict__) # prints {'name': 'Gogul', 'age': '24', 'pay': '5000'}

    # There are 2 customers
    print ("There are {} customers".format(Customer.num_of_custs))
```

<!-- --------------------------------------------------------------------- -->

<h3 class="centered-heading" id="how-tos"><span>How to's</span></h3>

<h3 class="code-head" id="how-to-read-file-line-by-line">How to read file line-by-line?<span>code</span></h3>

```python
filename = "entry_1.txt"
with open(filename) as f:
    data = f.readlines()

# remove whitespaces at end of each line
data = [x.strip() for x in data] 
```

<h3 class="code-head" id="how-to-write-file-line-by-line">How to write file line-by-line?<span>code</span></h3>

```python
l = ["pikachu", "charmander", "pidgeotto"]
fout = open("entry2.txt", "w")
for x in l:
    fout.write(x)
fout.close()
```

<h3 class="code-head" id="how-to-load-json-file">How to load json file?<span>code</span></h3>

```python
import json

file_input = "data.json"
with open(file_input) as data_file:    
    data = json.load(datafile)
```

<h3 class="code-head" id="how-to-check-if-list-is-empty">How to check if list is empty?<span>code</span></h3>

```python
# method 1 
if not myList:
    print "list is empty"

# method 2
if len(myList) == 0:
    print "list is empty"
```

<h3 class="code-head" id="how-to-access-index-in-for-loop">How to access index in for loop?<span>code</span></h3>

```python
myList = ["a", "b", "c"]

# method 1
for idx, l in enumerate(myList):
    print str(idx) + "-" + l

# method 2
idx = 0
for l in myList:
    print str(idx) + "-" + l
    idx += 1

# both methods print
# 0-a 
# 1-b
# 2-c
```

<h3 class="code-head" id="how-to-sort-a-dictionary-by-key-alphabetically">How to sort a dictionary by key alphabetically?<span>code</span></h3>

```python
a = {}
a["India"] = "Dhoni"
a["SouthAfrica"] = "ABD"
a["Australia"] = "Smith"

for key in sorted(a.keys(), key=lambda x:x.lower()):
    print ("{0} - {1}".format(key, a[key]))

# prints 
# Australia - Smith
# India - Dhoni
# SouthAfrica - ABD
```

<h3 class="centered-heading" id="resources"><span>Resources</span></h3>

* [Python Programming](https://gogul09.github.io/software/python-programming){:target="_blank"}