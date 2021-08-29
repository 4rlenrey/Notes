<!-- {% raw %} -->

# Python

<!-- TOC -->

- [Python](#python)
	- [Operators](#operators)
		- [Arithmetic](#arithmetic)
		- [Comparative](#comparative)
		- [Assignment](#assignment)
		- [Logical](#logical)
		- [Membership](#membership)
	- [Basics](#basics)
		- [Getting started](#getting-started)
		- [Syntax](#syntax)
		- [Comments](#comments)
	- [Variables](#variables)
		- [Usage](#usage)
		- [Assigning multiple values](#assigning-multiple-values)
		- [Data types](#data-types)
	- [Statements and flow control](#statements-and-flow-control)
		- [Conditional statements](#conditional-statements)
		- [Loops](#loops)
	- [Functions](#functions)
		- [Basic functions](#basic-functions)
		- [Special arguments](#special-arguments)
		- [Lambda](#lambda)
	- [Containers](#containers)
		- [Lists](#lists)
		- [Tuples](#tuples)
		- [Sets](#sets)
		- [Dictionaries](#dictionaries)
	- [OOP](#oop)
		- [Class and Object](#class-and-object)
		- [Constructor](#constructor)
		- [Methods](#methods)

<!-- /TOC -->

## Operators

### Arithmetic

| Operator | Definition                         | Example | Outcome |
| -------- | ---------------------------------- | ------- | ------- |
| x + y    | addition                           | 3 + 5   | 8       |
| x - y    | subtraction                        | 3 - 5   | -2      |
| x / y    | division                           | 5 / 2   | 2.5     |
| x * y    | multiplication                     | 3 * 5   | 15      |
| x % y    | modulo                             | 5 % 3   | 2       |
| x ** y   | Exponentiation                     | 5 ** 3  | 125     |
| x // y   | Floor division                     | 5 // 2  | 2       |
| x & y    | bitwise AND                        | 5 & 3   | 1       |
| ~x       | bitwise NOT                        | ~3      | -4      |
| x \| y   | bitwise OR                         | 5 \| 3  | 7       |
| x ^ y    | bitwise XOR                        | 5 ^ 3   | 6       |
| x << y   | bitwise left shift                 | 5 << 3  | 40      |
| x >> y   | bitwise right shift                | 5 >> 3  | 0       |

### Comparative

| Operator | Definition           | Example | Outcome |
| -------- | -------------------- | ------- | ------- |
| x == y   | x equal y            | 3 == 5  | false   |
| x != y   | x not equal y        | 3 != 5  | true    |
| x < y    | x less than y        | 3 < 5   | true    |
| x > y    | x more than y        | 3 > 5   | false   |
| x <= y   | x less or equal to y | 3 <= 5  | true    |
| x >= y   | x more or equal to y | 3 >= 5  | false   |

### Assignment

| Operator | Definition             |
| -------- | ---------------------- |
| x = y    | x now has a value of y |
| x += y   | x = x + y              |
| x -= y   | x = x - y              |
| x /= y   | x = x / y              |
| x //= y  | x = x // y             |
| x **= y  | x = x ** y             |
| x *= y   | x = x * y              |
| x ^= y   | x = x ^ y              |
| x &= y   | x = x & y              |
| x \|= y  | x = x \| y             |
| x <<= y  | x = x << y             |
| x >>= y  | x = x >> y             |
| x %= y   | x = x % y              |

### Logical

| Operator | Example     |
| -------- | ----------- |
| not      | not(x < 4)  |
| or       | x=2 or x=1  |
| and      | x=1 and y=1 |

### Membership

| Operator | Example     | Description             |
| -------- | ----------- | ----------------------- |
| in       | x in y      | true if x is in y       |
| is       | x is y      | true if x is equal to y |

## Basics
---

Python is a dynamically typed and garbage collected language. That means that You don't have to worry about the data types and you don't have to worry about memory allocation.

Good thing to note is that it's not a compiled type of programming language. It's a interpreted one.
That means that you need an interpreter to run it.
(There's a way to compile python programs tho but I don't think that I know anyone who does that)
Python's Interpreter is build on C.

_In this note I'm gonna focus on python3_

### Getting started

Let's suppose we have a `main.py` file that contains this code:
```py
print("Probably one of the worst script to exist")
print(4+6)
```
To run it we would have to use this python interpreter.

So to do that I'd have to write this command in my terminal.

```sh
python3 main.py
```
That would give me the output:
```
Probably one of the worst script to exist
10
```
So it works!

Basically to print stuff we just need to use a print command:
```py
print(stuff_to_print)
```
And if we wanted to get some input for the command line we can use `input()`

You don't need to have a main function here (unlike in c++) but it's advised to do so.
It's actually important because of the import problem.(I'll talk about it later)

So this is how it should look like when you're declaring a main function
```py
#function declaration
def main():
    print("This is a main function lol")

#This is working like "if this is the main file opened then invoke this main function"
if __name__ == "__main__":
    main()
```
### Syntax

Because Mr. Guido wanted to make this language readable Python is more about indentation than brackets, semicolons etc.

Indentation here is similar using brackets in c++

For example. In C++ we this is how if statement looked like:
```cpp
if(condition)
{
	do_something;
}
```
And this is how it looks in python
```py
if condition:
	do_something
```
(Indentation in python code was necessary unlike in c++ one)

Some people think that it's more readable. Honestly I'm not one of those people but yeah.

Notice how there's no such thing as semicolon in there. That's because in python you have to have one instruction for one line.
In c++ you can do this:
```cpp
x = 3; y = 5; w = x + y;
```
And it would work.

In python you have to do it like this:
```py
x = 3
y = 5
w = x + y
```

### Comments

Like in probably every single good programming language there are two types of comments.

Single line comment:
```py
#This is a comment
x = 5 #This is also a comment
print(x) #another comment
```

Multiline comment:
```py
"""
This is a comment that
uses multiple lines
Yeah, it's not bad
But still I like c++ more
"""
print("something")
``` 

## Variables
---

Because it's a dynamically typed language you don't have to specify the type of the variable you're using.

### Usage

Let's assign a value of `3` to a variable `x`
```py
x = 3
```
Yes, it's that easy.

You can also do something like this:
```py
x = 3
print(x)
x = "This is a string"
print(x)
```
And the output is:
```
3
This is a string
```
Like I said, it's all easy at the start.

Also It might be worth noting:
_Python does not care if you use single or double quotes_

So this:
```py
x = "Some text"
```
Is the same as this:
```py
x = 'Some text'
```
Sometimes you might want to specify what type are you passing into a variable. 
It looks like this:
```py
x = int(3) #this is going to be an integer
x = str(3) #this is going to be a string
```
You can also check what type is this variable currently using:
```py
x = "Something to make it look professional"
print(type)
```
It would output:
```
<class 'str'>
```
So we know it's a string.

### Assigning multiple values

That's what some languages are missing

Look how cool it is:
```py
a, b = ["a", "b"]
print(a, b)

c = d = 5
print(c, d)

e, f = 5, 7
print(e, f)
```
And the output should be:
```
a b
5 5
5 7
```

### Data types

Python gives you those basic datatypes:

| Type | What even is it | 
| --- | --- |
| int | number |
| float | floating point number |
| str | chain of characters (text) | 
| bool | boolean (true or false) | 

Datatypes in python aren't as important as in c++ in my opinion.

## Statements and flow control

In python like in almost any other language you have a possibility to control flow.

### Conditional statements

Similarly to c++ we have comparative operators:

| Operator | Definition           | Example | Outcome |
| -------- | -------------------- | ------- | ------- |
| x == y   | x equal y            | 3 == 5  | false   |
| x != y   | x not equal y        | 3 != 5  | true    |
| x < y    | x less than y        | 3 < 5   | true    |
| x > y    | x more than y        | 3 > 5   | false   |
| x <= y   | x less or equal to y | 3 <= 5  | true    |
| x >= y   | x more or equal to y | 3 >= 5  | false   |

So we can use them in our conditional statements.

The most common one might be `if`.

you can use it lke this:
```py
if condition:
	do_something
```

And here's some example:
```py
if x < y:
	print("x is smaller than y")
```

You can also use *`or`* and *`and`* statements

Example of using *`and`*:
```py
if x < y and x > 0:
	print("x is positive and smaller than y") 
```
Example of using *`or`*:
```py
if x < y or x < z:
	print("x is smaller than y or z")
```
There's also possibility of using such things as *`elif`* and *`else`*

Example:
```py
if x < y:
	print("x is smaller than y")
elif x < z:
	print("x is smaller than z")
else:
	print("x is bigger than both y and z")
```

`elif` is basically working just like `else if`.

### Loops

There are two types of loops.

While loop looks like this:
```py
while condition:
	do_something
```
Usage of this thing might look like this:
```py
while x > 0:
	print(x)
	x = x - 1
```
The value of `x` will be decreasing until x is equal or smaller than 0.

There's also a for loop:
```py
for x in some_range:
	do_something
```
Here you can do something like this:
```py
animals = ["Cat","Dog","Wolf"]
for animal in animals:
	print(animal)
```
The output is going to look like:
```
Cat
Dog
Wolf
```
Also you can use python range (numbers from a specific range):
```py
#printing numbers from 0 to 10
for i in range(0, 10):
	print(i) 
```
## Functions

Like in any other language, here you can declare your own functions.

### Basic functions

It looks like this:
```py
#definition
def name(arg1, arg2):
	do_something
	return something
#invoking 
name(3, "test")
```
And now a simple example of using a function:
```py 
def add_5(x):
	return x+5

y = add_5(5)
print(y)
```

the output is:
```
10
```

### Special arguments

You can set default arguments like this:
```py
#Set y default's value to 5
def add(x, y = 5):
	return x + y
print(add(5))
print(add(5, 10))
```
Output:
```
10
15
```
You can also use keyword arguments
It works in a way so that you don't need to provide them in a specific order.
You can just assign values to names.

```py
def divide(base, divider):
	return base//divider
x = divide(divider=5, base=10)
print(x)
```
Output:
```
2
```

### Lambda

Syntax for lambda function here is pretty easy.

```py
lambda arguments : what_to_return
```

This is my example of how you can use it:

```py
modpow = lambda x, y, z, : (x**y%z) 
print(modpow(52, 21, 63))
```
output would be 
```
55
```

because **52<sup>21</sup>mod63 = 55**

As you can see it's pleasant

## Containers

You can store something in them.
Python provides a bit of default containers those being:

You can check if a element is in the container using the **`in`** keyword.
```py
if 3 in numbers_container:
	print("It's in there")
```

### Lists

Similar to c++'s vector. Declaring it looks like this:
```py
name = [some_item, another_item] #filled on init
another_one = [] #empty one
```
you can access it's elements like this (note that its indexes start at 0)
```py
x = name[index]
```
Example:
```py
x = [1, 5, 6, 3]
print(x[1])
```
Output:
```
5
```
You can access the last item by doing 
```
x[-1] = some_value
```
And also you can access a range of items by doing
```py
print(x[start:end])
```
example:
```py
x = [1, 2, 3, 4, 5, 6]
print(x[1:4])
```
Output:
```
[2, 3, 4]
```
Start or end of this range does not need to be specified.
Example
```py
x = [1, 2, 3, 4, 5, 6]
print(x[1:])
```
Output:
```
[2, 3, 4, 5, 6]
```

You can change values by accessing the items
```py
x = [1, 5, 6, 3]
x[0] = 4
#now it looks like [4. 5. 6. 3]
```
You can also add items using the **append** or **insert** keyword.
The main difference between them is that **insert** lets you specify at which index this variable
should be added at. **Append** tho lets you add this element at the end of this list.

example:
```py
x = [3, 5, 5, "test"]
x.append(0)
print(x)
x.insert(2, "something_at_index_2")
print(x)
```
Output:
```
[3, 5, 5, 'test', 0]
[3, 5, 'something_at_index_2', 5, 'test', 0]
```

If you need to delete elements from this container then you can use these methods:

**remove(item)** - To delete specific item

**pop()** - To delete item at the end of the list

**pop(index)** - To delete item at this specific index

**clear()** - To clear the whole list

example:
```py
x = [1, 2, 3, 4, 5, 6]
x.remove(1) 
print(x)
x.pop()
print(x)
x.pop(2)
print(x)
x.clear()
print(x)
```
Output:
```
[2, 3, 4, 5, 6]
[2, 3, 4, 5]
[2, 3, 5]
[]
```

### Tuples

Those are like lists but once created they don't allow you to change anything

This is a simple example of creating a tuple:
```py
x = (2, 3,) #Notice the comma the the end
```
Honestly I don't use them.

### Sets

Similar to list but don't allow duplicate items and you can't change any of those items.

This is a simple example of creating a set:
```py
x = {2, 3}
```
Just like in list you add and remove items

It's mostly used to check if an item occurs in it

### Dictionaries

Key-Value container.
Declaration looks like this:
```py
x = {
	"MyAge" : 3,
	"MyEyes" : "Blue",
	3 : False
}
```
Let's try to print it:
```py
print(x)
```
Output:
```
{'MyAge': 3, 'MyEyes': 'Blue', 3: False}
```
Nice.

We can access/change/delete it's items just like we did in lists but instead of indexes we access those items by key (this left thingy)

For example let's print value of our previously added dict and then add a new one:
```py
print(x[3])
x["SomeNewKey"] = 10
print(x)
```
Output:
```
False
{'MyAge': 3, 'MyEyes': 'Blue', 3: False, 'SomeNewKey': 10}
```

## OOP

Just like in c++ we have classes and objects.
Class is like this metal form for making a cookie and object is a cookie.

### Class and Object

You can simply define a class like this:
```py
class Hooman:
	name = "Default"
```

And now we can create a object x from a class **`Hooman`**

```py
x = Hooman()
```

We can now check and change it's attribute **`name`**

```py
print(x.name)
x.name = "Paul"
print(x.name)
```

The output should look like this:

```
Default
Paul
```

It's cool.

### Constructor

Constructor is a method invoked on start.
It can be used to take some initial values or something.

It looks like this:

```py
class Hooman:
	name = "Default"
	def __init__(self, age): 	# Constructor 
		self.age = age
```

And now when creating this object you'd have to provide this age variable:

```py
x = Hooman(4)
print(x.age)
```

And the output should be 

```
4
```

### Methods

Methods are essentially just some functions inside a class.

```py
class Hooman:
	name = "Default"
	
	def __init__(self, age): 	# Constructor
		self.age = age

	def speak(self):			# Method 
		print(f"My name is {self.name} and my age is {self.age}")
```
And now let's create an object and test this method:

```py
x = Hooman(3)
x.name = "Paul"
x.speak()
```

This is the output:

```
My name is Paul and my age is 3
```

<!-- {% endraw %} -->