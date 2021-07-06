# C++11 Notes

1.  [Repository overview](README.md)
2.  [CheetSheets](#chapter-1-cheetsheets)
3.  [Basics](#chapter-2-basics)
4.  [Statements and flow control](#chapter-3-statements-and-flow-control)
5.  [Variables and Objects](#chapter-4-variables-and-objects)

## Chapter 1 CheetSheets
---

### Arythmetic Operators

| Operator | Definition                         | Example | Outcome |
|----------|------------------------------------|---------|---------|
| x + y    | addition                           | 3 + 5   | 8       |
| x - y    | substraction                       | 3 - 5   | -2      |
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
|----------|----------------------|---------|---------|
| x == y   | x equal y            | 3 == 5  | false   |
| x != y   | x not equal y        | 3 != 5  | true    |
| x < y    | x less than y        | 3 < 5   | true    |
| x > y    | x more than y        | 3 > 5   | false   |
| x <= y   | x less or equal to y | 3 <= 5  | true    |
| x >= y   | x more or equal to y | 3 >= 5  | false   |

### Assignment Operators

| Operator | Definition             |
|----------|------------------------|
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
|----------|------------|
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

Comments can not be seen by the compiler. They're really usefull for programmers tho.

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
	int x = 2+1; //asigning a value to a variable named x
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

    
    #include <iostream>
    int main() 
    {
    	int x; //declaration without specyfing value
    	std::cin >> x; //getting the value of x from the standard input 
    	x += 2; //adding 2 to the value
    	std::cout << x; 
    	return 0; 
    }
    

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
//it's similar to a lot of else if's but more redable
    
    
//ternary operator
some_variable = (condition) ? value_if_true : value_if_false;
```

### C++ provide 4 types of loops

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

A1: It's really simple. When you have a container and you want to be able to access every single element of it then you can easly do that by using this type of loop. (And using it also makes code more readable)

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

Copyright © 2021 4rlenrey. All Rights Reserved