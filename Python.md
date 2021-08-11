<!-- {% raw %} -->

# Python

<!-- TOC -->

- [Python](#python)
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

<!-- /TOC -->

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

`elif` is basically working just like else if.

### Loops


<!-- {% endraw %} -->
