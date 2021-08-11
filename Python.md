<!-- {% raw %} -->

# Python

<!-- TOC -->

- [Python](#python)
	- [Basics](#basics)
		- [Getting started](#getting-started)
		- [Syntax](#syntax)
		- [Comments](#comments)
	- [Variables](#variables)

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

For example let's assign a value of `3` to a variable `x`
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


<!-- {% endraw %} -->
