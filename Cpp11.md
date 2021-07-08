# C++11 Notes

<!-- TOC -->

- [C++11 Notes](#c11-notes)
    - [Chapter 1 CheetSheets](#chapter-1-cheetsheets)
        - [Arithmetic Operators](#arithmetic-operators)
        - [Comparative Operators](#comparative-operators)
        - [Assignment Operators](#assignment-operators)
        - [Logical Operators](#logical-operators)
    - [Chapter 2 Basics](#chapter-2-basics)
        - [Getting started](#getting-started)
        - [Comments](#comments)
    - [Chapter 3 Statements and flow control](#chapter-3-statements-and-flow-control)
        - [Conditional statements](#conditional-statements)
        - [Loops](#loops)
    - [Chapter 4 Variables and Objects](#chapter-4-variables-and-objects)
        - [Data types](#data-types)

<!-- /TOC -->

## Chapter 1 CheetSheets
---

### Arithmetic Operators

| Operator | Definition                         | Example | Outcome |
| -------- | ---------------------------------- | ------- | ------- |
| x + y    | addition                           | 3 + 5   | 8       |
| x - y    | subtraction                       | 3 - 5   | -2      |
| x / y    | division                           | 4 / 2   | 2       |
| x * y    | multiplication                     | 3 * 5   | 15      |
| x % y    | modulo                             | 5 % 3   | 2       |
| x & y    | bitwise AND                        | 5 & 3   | 1       |
| ~x       | bitwise NOT                        | ~3      | -4      |
| x \| y   | bitwise OR                         | 5 \| 3  | 7       |
| x ^ y    | bitwise XOR                        | 5 ^ 3   | 6       |
| +x       | Unary plus                         | +'w'    | 119     |
| -x       | Unary minus                        | -5      | -5      |
| x << y   | bitwise left shift (x * pow(2, y)) | 5 << 3  | 40      |
| x >> y   | bitwise right shift                | 5 >> 3  | 0       |

### Comparative Operators

| Operator | Definition           | Example | Outcome |
| -------- | -------------------- | ------- | ------- |
| x == y   | x equal y            | 3 == 5  | false   |
| x != y   | x not equal y        | 3 != 5  | true    |
| x < y    | x less than y        | 3 < 5   | true    |
| x > y    | x more than y        | 3 > 5   | false   |
| x <= y   | x less or equal to y | 3 <= 5  | true    |
| x >= y   | x more or equal to y | 3 >= 5  | false   |

### Assignment Operators

| Operator | Definition             |
| -------- | ---------------------- |
| x = y    | x now has a value of y |
| x += y   | x = x + y              |
| x -= y   | x = x - y              |
| x /= y   | x = x / y              |
| x *= y   | x = x * y              |
| x ^= y   | x = x ^ y              |
| x &= y   | x = x & y              |
| x \|= y  | x = x \| y             |
| x <<= y  | x = x << y             |
| x >>= y  | x = x >> y             |
| x %= y   | x = x % y              |

### Logical Operators

| Operator | Definition |
| -------- | ---------- |
| !        | not        |
| \|       | or         |
| &&       | and        |
## Chapter 2 Basics
---
### Getting started

_Lots of people hate C++ and honestly, I can~'t~ understand why._  
To be able to use/run your basic C++ code you have to go through some steps;

1.  Compiling your source files to object files _file1.cpp, file2.cpp -> file1.o, file2.o_
2.  Consolidating all object files into an executable _file1.o, file2.o -> notavirus.exe_

### Comments

Comments can not be seen by the compiler. They're really useful for programmers tho.

```cpp
// this is a single line comment
    
/* this is the start of the multi-line comment 
text
some more text
even more text to make you understand
this is the end of the multi-line comment */

/*You can put multiline comments before the instruction because they have a specified ending*/SOME-INSTRUCTION;
```    
    

Here is a basic example of a one of the simplest c++ programs:

```cpp    
int main() //main function
{
	int x = 2+1; //assigning a value to a variable named x
	return 0; //returning an exit code (0 is success, everything else indicates an error)
}
```

It does not do a lot. Just adds two numbers and saves them in a variable named x. You don't need to include any libraries because it uses only core elements of c++. If you wanted to print out a value of this x variable then you'd need to use a library.

```cpp    
#include <iostream> //standard library for working with output/input
int main() 
{
	int x = 2+1;
	std::cout << x; //printing out this x variable 
	return 0; 
}
```

The output for this simple program would be:
```sh
3
```
You can also input some data from a user. Let's make a program that takes a number and then prints a bigger one.

```cpp    
#include <iostream>
int main() 
{
	int x; //declaration without specyfing value
	std::cin >> x; //getting the value of x from the standard input 
	x += 2; //adding 2 to the value
	std::cout << x; 
	return 0; 
}
```

For input like this:
```sh
3
```
The output would be:
```sh
5
```
## Chapter 3 Statements and flow control
---

### Conditional statements

If you want to do something if a condition is met then you have a lot of options in c++. These are your options:

```cpp
//if statement
if(condition)
{
	do_stuff;
} else if(condition) {
	do_stuff;
} else{
	do stuff;
}
//you do not need to use all of above; You can use only if or only if/else or ifelse if
    
    
// switch statement
switch(some-variable)
{
    case one-value:
    do_stuff;
    	break;
    
    case another-value:
    do_stuff;
    	break;
    
    default:
    do_stuff_if_didnt_meet_any_cases;
    	break;
} 
//it's similar to a lot of else if's but more readable
    
    
//ternary operator
some_variable = (condition) ? value_if_true : value_if_false;
```

### Loops

```cpp    
//for loop
for(start_instruction; continuation_condition; step_instruction)
{
	do_stuff;
}
    
    
//while loop
while(continuation_condition)
{
	do_stuff;
}
    
    
//do-while loop
do
{
	do_stuff;
}while(continuation_condition);
    
    
//foreach loop 
for(declaration : container)
{
	do_stuff;
}
```

You might be asking yourself 2 questions:

Q1: What's the difference between while and do-while loop;

A1: Basically there is a possibility that the instructions in a while loop won't be used even once if at the first iteration the condition is false. Do-while loop on the other hand gives us the functionality of running the instructions in it at least once, even if the condition required is false. (But honestly I never use do-while loops)

Q2: What is going on with this range-based loop

A1: It's really simple. When you have a container and you want to be able to access every single element of it then you can easily do that by using this type of loop. (And using it also makes code more readable)

Let's check how would these loops be used in practice:

```cpp 
#include <iostream>
int main()
{
    //we'll need some for of container for range-based loop
    int x[4] = {0,1,2,3}; 
    int y = -5;
    int w = 2;
    for(int o : x)
    {
    	std::cout<< o << " "; 
    }
    std::cout<<"\n"; 
    	
    for(int i = 0; i < w; i++)
    {
    	std::cout<< i << " "; 
    }
    std::cout<<"\n"; 
    
    while(y < 0)
    {
    	std::cout<< y << " ";
    	y++; 
    }
    
    return 0;
}
```

The output for this program would be:
```sh
0 1 2 3 
0 1 
-5 -4 -3 -2 -1 
```
## Chapter 4 Variables and Objects
---
Like in any other language you can declare the existence of variables. You can do that just like that:
```cpp
std::string s; 
```
Yes! It's that easy. We've declared a string type of variable named `s` and now we can store some data in it.

```cpp
std::string s = "We're declaring string var and giving this text as it's value";
``` 

### Data types
C++ gives us some datatypes by default. These are some that I use:
(Size is in bytes)

| Type   | What does it store                                   | Size |
| ------ | ---------------------------------------------------- | ---- |
| int    | number in range from -2,147,483,648 to 2,147,483,647 | 4    |
| char   | characters with ASCII number values from 0 to 255    | 1    |
| double | floating point numbers                               | 4    |
| float  | Same as in double; It's just bigger                  | 8    |

You can upgrade your variables by using these keywords right before specyfing type  (mostly for better memory management):

| Keyword       | What does it do                             |
| ------------- | ------------------------------------------- |
| **signed**    | It lets this boi use some negative numbers  |
| **unsigned**  | It makes your boi use only positive numbers |
| **long**      | bigger variable more numbers to use         |
| **long long** | bigger variable more numbers to use         |
| **short**     | smaller variable less numbers to use        |

Using this magic looks like this:

```cpp
short int v = 10;
```

You might be asking yourself a question.
What if I wanted to use 5 numbers?
Would declaring them look like this?:
```cpp
int number1 = 1;
int number2 = 7;
int number3 = 3;
int number4 = 4;
int number5 = 2;
```
NO! You can create an array;
```cpp
int numbers[5] = {0}; //declaration type name[size];
//Added this = {0} thing to make it have all zeros

//remember that arrays start with 0
//so here you can do:
numbers[0] = 1;
numbers[1] = 7;
numbers[2] = 3;
numbers[3] = 4;
numbers[4] = 2;
```
This is a 1-dimensional array. It looks like this:
```sh
[1][7][3][4][2]
```
Arrays can be n-dimensional
It you wanted to have something like this:
```sh
[0][0][0][0][0]
[0][0][0][0][0]
[0][0][0][0][0]
[0][0][0][0][0]
[1][0][0][0][0]
```
You would want to do this:
```cpp
int a[5][5];

//syntax for when you want to access elements from the array;
a[4][0] = 1;
```
You can assign numbers while declaring to an array like this:
```cpp
int x[4] = {1, 2, 4, 0};
```
It'll look like:
```
[1][2][4][0]
```
And 2 dimensional
```cpp
int a[2][3] = {{5, 2, 3}, {4, 2, 8}};
```
Would look like:
```sh
[5][2][3]
[4][2][8]
```
This simple program
```cpp
#include <iostream>
int main()
{
    int a[2][3] = {{5, 2, 3}, {4, 2, 8}};
    std::cout << a[0][2];
    return 0;
}
```
Would print out this
```sh
3
```
Sadly, one of the problems related to arrays is that you can't really add any new elements after declaration.
That can be solved by using STL containers.
Using/declaring them looks like this:

```cpp
#include<vector>
#include<string>

int main()
{
    std::string x = "Container for text strings";
    std::vector<int> v = {3,5,1};
    return 0;
}
```

To use a container you usually need to `#include` it.
STL provides different types of containers. 


Like I said, C++ is simple.

