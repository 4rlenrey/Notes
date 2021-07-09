# C++11 Notes

<!-- TOC -->

- [C++11 Notes](#c11-notes)
    - [Operators](#operators)
        - [Arithmetic](#arithmetic)
        - [Comparative](#comparative)
        - [Assignment](#assignment)
        - [Logical](#logical)
        - [Access](#access)
    - [Basics](#basics)
        - [Getting started](#getting-started)
        - [Comments](#comments)
    - [Statements and flow control](#statements-and-flow-control)
        - [Conditional statements](#conditional-statements)
        - [Loops](#loops)
    - [Variables](#variables)
        - [Data types](#data-types)
    - [Functions](#functions)
        - [Syntax](#syntax)
        - [Declaration](#declaration)
    - [STL containers](#stl-containers)
        - [Vector](#vector)
        - [Stack](#stack)
        - [List](#list)
        - [Queue](#queue)
        - [Priority_Queue](#priority_queue)
        - [Map](#map)
        - [Pair](#pair)
        - [Set](#set)
    - [Object Oriented Programming](#object-oriented-programming)

<!-- /TOC -->

## Operators
---

### Arithmetic

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
| x *= y   | x = x * y              |
| x ^= y   | x = x ^ y              |
| x &= y   | x = x & y              |
| x \|= y  | x = x \| y             |
| x <<= y  | x = x << y             |
| x >>= y  | x = x >> y             |
| x %= y   | x = x % y              |

### Logical

| Operator | Definition |
| -------- | ---------- |
| !        | not        |
| \|       | or         |
| &&       | and        |

### Access

| Operator | Definition | Example | Description |
| --- | --- | --- | --- |
| * | Pointer dereference | *x | Boi, give me the object from this pointer |
| [ ] | Array subscript | x[y] | Boi, give me the object from y index from array |
| & | Address of/reference to | &x | create a pointer that refers to the object x |
| . | Member | x.y | Use a member y of object x |
| -> | Member pointer | x->y | Use a member y of object x through a pointer |
## Basics
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
## Statements and flow control
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
## Variables
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
## Functions

When you don't want to put everything in `main` function or you want to make some parts of your code reusable you create your own functions.

Let's consider this example 
```cpp
#include <iostream>
using namespace std;
int main()
{
    int x[100] = {0};

    //do some stuff with the array

    //print out the array
    cout << "/n";
    for(int i = 0; i < 100; i++)
    {
        cout << "/t" << x[i];
    }
    cout << "/n";


    //do another stuff with the array

    //print out the array again
    cout << "/n";
    for(int i = 0; i < 100; i++)
    {
        cout << "/t" << x[i];
    }
    cout << "/n";

    return 0;
}
```
I feel like you can see where I'm going with this

Let's wrap this printing thing into a function
```cpp
#include <iostream>
using namespace std;

void print_array(const int &arr[])
{
    cout << "/n";
    for(int i = 0; i < 100; i++)
    {
        cout << "/t" << x[i];
    }
    cout << "/n";
}

int main()
{
    int x[100] = {0};

    //do some stuff with the array

    print_array(x);

    //do another stuff with the array

    print_array(x);

    return 0;
}
```
Looks a bit cleaner huh?

### Syntax

```cpp
return_type name(type_of_first_arg name_of_first_arg)
{
    
}
```

Here is a example of a simple function
```cpp
int add(int x, int y)
{
    return x+y;
}
//usage
w = add(5, 6); //w should be equal to 11
```
### Declaration
You can also declare the existence of a function first and write it later.
Example:
```cpp
#include <iostream>
using namespace std;

void print_array(const int &arr[]); //declaration 

int main()
{
    int x[100] = {0};
    print_array(x);

    return 0;
}

void print_array(const int &arr[]) //writing what it should do
{
    cout << "/n";
    for(int i = 0; i < 100; i++)
    {
        cout << "/t" << x[i];
    }
    cout << "/n";
}
```
You always need to declare that the function exist before using it
## STL containers

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
The ones that I mostly use are:

### Vector

Vector is an amazing container. It's like an array that can change size.
You can declare it in a few different ways.
```cpp
std::vector<type-stored> name(size);
std::vector<type-stored> name;

//example
std::vector<int> vec(10);
```
And you can access its elements in a few different ways
```cpp
name[index] = 0;
name.at(index) = 0;
name.front() = 0;
name.back() = 0;
```
You can do stuff like adding and deleting elements
```cpp
name.push_back(new_element); //adding new element
name.pop_back(); //deleting last element
name.erase(first_i, last_i); //erase elements from first to the last index specified
name.clear(); //removes all the elements
```
It has some methods for iterators like `begin()` and `end()`.

### Stack
STL stack is exactly like this algorithmical stack.

LIFO - Last in first out

```cpp
std::stack<type-stored> name;

//example
std::stack<int> s;
```
It has some basic methods
```cpp
name.push(element); //adds new element on top of a stack
name.pop(); //deletes the top element
name.top(); //returns the top element
name.empty(); //check if it's empty and returns true/false
```

### List

STL list is a implemented version of a linked list data structure.
Instead of storing it's elements in a array way each node contains a direct link to another node. That means that you can not use normal indexes like in array. It has some benefits tho like reduced complexity of deleting a front element.
Eg. Let's consider consider a vector that contains 100000 elements. Deleting the first element would result in changing indexes of 99999 elements. Imagine if you had to delete/add elements in front of this vector quickly. It'd be impossible.

In array it looks like this:
```sh
[0][1][2][3][4]
```
in linked list it looks like
```sh
[start]->[]->[]->[]->[]->[end]
```

Ok, lets stop doing theory :)
```cpp
std::list<type-stored> name;

//example
std::list<int> s;
```
It has some basic methods
```cpp
name.push_front(element); //adds new element in front of the list
name.push_back(element); //adds new element at the back of the list
name.pop_front(); //deletes the front element
name.pop_back(); //deletes the back element
name.front(); //access the front element
name.back(); //access the back element
name.sort(); //sorts the list
name.size(); //returns size of the list
name.remove(); //removes elements with a specific value
name.empty(); //check if it's empty and returns true/false
```
### Queue

FIFO - first in first out

```cpp
std::queue<type-stored> name;

//example
std::queue<int> q;
```
It also has some basic methods
```cpp
name.push(element); //adds new element
name.pop(); //deletes next element
name.front(); //returns the front element
name.size(); //returns size
name.empty(); //check if it's empty and returns true/false
```

### Priority_Queue

Priority queue is used when you need to have a container with quick access to the greatest of the elements. The greatest element is always on top.

```cpp
std::priority_queue<type-stored> name;

//example
std::priority_queue<int> pq;
```
It also has some basic methods
```cpp
name.push(element); //adds new element 
name.pop(); //deletes top element
name.front(); //returns top element
name.size(); //returns size
name.empty(); //check if it's empty and returns true/false
```

### Map

```cpp
std::map<std::string, int> m { {"One_key", 0}, {"YEP_DASSQOOL", 0}, };

m["One_key"] = 22;  // update an existing value
m["Some_Text"] = 0;  // insert a new value
```
Do I have to even say anything else?
This is just so cool. It's like an array, but you can use custom keys instead of boring indexes.

### Pair

```cpp
std::pair<int, int> m;

m.first = 4; //accessing the first object
m.second = 4; //accessing the second object
```

### Set

Sets are similar to priority_queues, because you can specify the order you want your content to be stored in.
It's useful when you need a container that can provide a easy and fast way of checking if a specific value exists.

Like I said, C++ is simple.

## Object Oriented Programming

Let's consider this simple idea:
_What if I wanted to create a simple vector that contains people's information?_

Example
```txt
Person's name: Paul
Person's year of birth: 2003
Person's nationality: Poland
Person's hobby: IT
```
We could create a vector of pairs but it wouldn't look good;
```cpp
std::vector<std::pair<std::pair<std::string, int>, std::pair<std::string, std::string>>>;
//first.first = name
//first.second = age
```
THIS LOOKS AWFUL!

What we could do is creating our type.
We can do that by using `class` or `struct` keyword. Their only difference is that class has all the elements private by default and struct has them public.

I'm gonna be using classes.

Let's now create my own Person type.
```cpp
class Person{

public:
    std::string nationality;
    int year_of_birth;
    std::string name;
    std::string hobby;
}; 
//remember about the semicolon at the end of class definition
```

Now we can create a simple instance of this type in a simple program.

```cpp
#include <iostream>
#include <string>

class Person{
public:
    std::string nationality;
    int year_of_birth;
    std::string name;
    std::string hobby;
}; 

int main()
{
    Person me; //declare object me from type Person
    me.year_of_birth = 2003;
    me.nationality = "Poland";
    me.name = "Paul";
    me.hobby = "IT";

    std::cout << me.name; 
    return 0;
}
```
Should output
```sh
Paul
```

We could also create a vector of this stuff

```cpp
std::vector<Person> v;
```
You have to agree with me that it looks better than the first `std::pair` solution.