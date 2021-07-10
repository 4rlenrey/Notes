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
        - [Whitespaces](#whitespaces)
    - [Statements and flow control](#statements-and-flow-control)
        - [Conditional statements](#conditional-statements)
        - [Loops](#loops)
    - [Variables](#variables)
        - [Data types](#data-types)
        - [Arrays](#arrays)
        - [Scope](#scope)
        - [Pointers](#pointers)
        - [Dynamic memory allocation](#dynamic-memory-allocation)
    - [Functions](#functions)
        - [Syntax](#syntax)
        - [Declaration](#declaration)
        - [Overloading](#overloading)
        - [Templates](#templates)
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
        - [Access keywords](#access-keywords)
        - [Constructor and Destructor](#constructor-and-destructor)
        - [Inheritance](#inheritance)

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

### Whitespaces

C++ does not care so much about whitespaces unlike python does. 
You can do that here:
```cpp
#include <iostream>
int main() 
{int x; std::cin >> x; x += 2; std::cout << x; return 0; }
```
Yes, It's a working script ;)

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

### Arrays

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

### Scope
Let's consider this example:
```cpp
int main()
{ //scope level 1
    
    int x = 1;
    if(x == 1)
    { //scope level 2

        int y = x + 3;
        y = 2+3;
    
    
    }// Delete all variables from this scope (y)
    else
    { //new scope level 2

        int y = x + 100;
        int f = x + 100;
        int g = x + 100;
    }// Delete all variables from this scope (y, f, g)
    
//you cannot use y here because it's been deleted
}
```

Basically all variables can only be accessed in the same or the upper scope that they've been created.

### Pointers

To simply visualize pointers you're gonna have to look at this code for a second.
```cpp
#include <iostream>
int main()
{
    int m = 5; //we initialize a variable with a value of 5 

    int *k = &m; //we initialize a pointer variable to point to this m variable
    std::cout << k;
    return 0;
}
```
This program is going to output:
```sh
0x7ffe7b827b74
```
But let's run it one more time:
```sh
0x7fff556de9f4
```
It's different!

That's because when we initialized this variable our program picked available part of RAM (Not used by any other program or system).
Because our system is constantly allocating and deallocating some parts of memory, 
there's a really small chance for you to have the same part of memory used twice.

But why are those pointer useful and how do you even use them?

Let's first establish how would you get a value of a part of memory your pointer points to.
```cpp
#include <iostream>
int main()
{
    int m = 5;
    int *k = &m; 
    std::cout << *k; //now we are outputting not the memory location but what's in there
    return 0;
}
```
The output now is:
```sh
5
```
You can think of a pointer as the number of your house.
Courier does not need to know what's in your house to deliver your package.
Just like you do not need to pass the 100mb string to your function. You can pass a pointer to it.

### Dynamic memory allocation

Like I was saying: _Courier does not need to know what's in your house to deliver your package.
Just like you do not need to pass the 100mb string to your function. You can pass a pointer to it._

Creating a variable like I did it before:
```cpp
int x = 9;
```
Would put this variable on a function stack.
There are a few disadvantages of that.

 - Your variable will be deleted when the function returns;
 - Your stack size is limited so your variables have a specific size limit.

You can change that by creating a variable with the `new` keyword. It'll instead of creating a variable on stack, create it on heap.

It'd look like this.
```cpp
int *x = new int; //create a pointer to newly allocated int-type of memory
std::string *x = new std::string;
int *arr = new int [5]; //create a pointer to dynamically allocated array with size of 5 elements
```

REMEMBER TO LATER DELETE ALLOCATED MEMORY!!!.
```cpp
delete x; //x should be a pointer to dynamically allocated variable

delete []arr; //arr should be a pointer to dynamically allocated array
```


## Functions
---

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

### Overloading

You can overload functions
```cpp
int add(int a, int b);
int add(double a, double b); 
int add(int a, int b, int c); 

int main()
{
    int x = add(4, 5, 6); //compiler will recognize which one to choose by types of arguments
}
```
This would work, even tho this functions have the same name.
All of them have different data coming into them.

You can overload functions by different types and different amounts of arguments.
Compiler will recognize which one you want to use.

### Templates

You might be asking yourself now: _What if I wanted to have a simple print class for different types?_

**Bad answer:**
You can use function overloading and do something like this:
```cpp
void print(int x)
{
    std::cout << x;
}
void print(string x)
{
    std::cout << x;
}
void print(double x)
{
    std::cout << x;
}
void print(some_type x)
{
    std::cout << x;
}
```
**Good answer:**
You can use templates:
```cpp
template <typename T> //where T can be any type of variable
void print(T x)
{
    std::cout << x;
}
```
Let's try this out:
```cpp
#include <iostream>

template <typename T> //where T can be any type of variable
void print(T x)
{
    std::cout << x << "\n";
}
int main()
{
    int x = 0;
    std::string w = "tttttt";
    print(x);
    print(w);
}
```
The output is:
```sh
0
tttttt
```
Again, pretty cool huh?

## STL containers
---
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
---
Let's consider this simple idea:
_What if I wanted to create a simple vector that contains people's information?_

Example of one person's info:
```txt
Person's name: Paul
Person's year of birth: 2003
Person's nationality: Poland
Person's hobby: IT
```

We could create a vector of pair of pairs;
```cpp
std::vector<std::pair<std::pair<std::string, int>, std::pair<std::string, std::string>>>;
//first.first = name
//first.second = age
```
THIS LOOKS AWFUL!

What we could better do is create our own type.
We can do that by using `class` or `struct` keyword. Their only difference is that class has all the elements private by default and struct has them public.

I'm gonna be using classes because classes are the c++ standard way of doing this.

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

 - parameters = variables inside class
 - methods = functions inside class


### Access keywords

What about this `public` thingy?

I'd say that it's pretty easy.
Class has its own members. Like `name` in the example above.

All class members are private by default but like in the example above you can do `public:` keyword and all members **under it** will be public.

There are three possible access types. 

- Public - _members are accessible for everything_

- Private - _members are only accessible within the class defining them and by friends of their class_

- Protected - _like in private but also in classes that inherit from that class_

So this
```cpp
class Animal{
    int max_age;
public:
    void set_max_age(int max_age);
};

int main()
{
    Animal cat;
    cat.max_age = 3; //would give an error
}
```
Would give an error because `int max_age` is private by default and can only be accessed by other members from the class.

You can see that I've created a simple function declaration within a function.
Yes, this is possible.

That's how you can actually do this without changing the access type of this max_age member.

```cpp
class Animal{
    int max_age;
public:
    void set_max_age(int max_age);
};

void Animal::set_max_age(int max_age)
{
    this->max_age = max_age;
}

int main()
{
    Animal cat;
    cat.set_max_age(3); //we are invoking this public method
}
```
### Constructor and Destructor

Is there a possibility of creating a method invoked on Creation/deletion of a object from my class?

Yes, there is.

Those methods are called:

 - constructor = method called when creating an object. Can be used for setting some initial data.

 - destructor = method called when deleting an object. Can be used for deleting allocated memory etc.

How do you use them?
 
It's simple
```cpp
#include <iostream>
class Cat{
    int age;
public:
    Cat(); //Constructor
    Cat(int age); //Constructor overload 
    ~Cat(); //Destructor
};

Cat::Cat() //constructor when no value provided 
{
    this->age = 0;
    std::cout << "woooooo, I'm being constructed ;) " << "My age is " << this->age << "\n";
}

Cat::Cat(int age) //constructor overload when age value provided
{
    this->age = age;
    std::cout << "woooooo, I'm being constructed ;) " << "My age is " << this->age << "\n";
}

Cat::~Cat() // destructor   
{
    std::cout << "woooooo, I'm being deleted ;) " << "My age was " << this->age << "\n" ;
}

int main()
{
    Cat ron; //constructor invoked
    Cat don(5); //constructor invoked (passed a value to it)
} //destructors invoked because the objects are deleted
```

This program will output this:
```txt
woooooo, I'm being constructed ;) My age is 0
woooooo, I'm being constructed ;) My age is 5
woooooo, I'm being deleted ;) My age was 5
woooooo, I'm being deleted ;) My age was 0
```
Note that I've never invoked any functions manually.
Pretty cool huh?

### Inheritance

You might be asking yourself another question now.
What if I wanted to create a base class like `Animal` and then create subclasses like
`cat` and `dog` based on this `Animal` class.

Lets create a base `Animal` class first.
```cpp
class Animal{
public:
    std::string sound;
    int age;
    void make_sound();
};
```
Then we can create cat class that inherits from this Animal class.
