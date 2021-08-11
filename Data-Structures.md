<!-- {% raw %} -->

# Data structures
<!-- TOC -->

- [Data structures](#data-structures)
	- [What even is data structure?](#what-even-is-data-structure)
	- [Stack](#stack)
	- [Queue](#queue)
	- [Matrix](#matrix)
		- [Multiplying each element](#multiplying-each-element)
		- [Adding two matrices](#adding-two-matrices)
		- [Rotating](#rotating)

<!-- /TOC -->

## What even is data structure?
---

Data structure is a way of organizing the data so that it can be used efficiently.

## Stack
---

Stack follows the FILO/LIFO order.

 - FILO - First in, last out.
 - LIFO - Last in, first out. 

This is a simple diagram of a stack.

![Diagram](Assets/Data1.png)

You can see, that the first element inserted there will be the last out.
This is my simple and not secure implementation of a stack in C++:
```cpp
template <class T>
class RlenStack{
    int size = 0;
    int max_size = 0;
    T *arr = NULL;
public:
    RlenStack(int max_size){ this->arr = new T[max_size]; this->max_size = max_size;} //allocate memory
    void push(T element){if(size<max_size-1) this->size++; arr[size-1] = element; } //add to array
    void pop(){if(size)this->size--;} //decrease size
    T top(){ if(size)return arr[size-1]; } //get the top element from array
    int get_size(){ return size; } //return size
    ~RlenStack(){ delete []arr; } //free memory
};
```
Possible usage:
```cpp
RlenStack<int> s(100); //declaration where 100 is the max amount of elements stored
s.push(4); //adding element
s.pop(); //removing element
int x = s.top(); //getting top element
```

After some improvements suggested by w1ndex this is my second implementation
```cpp
template <class T>
class RlenStack{
    int size = 0;
    int max_size = 2;
    T *arr = NULL;
public:
    RlenStack(){this->arr = new T[2];} //allocate memory
    void push(T element)
    {
        if(size<max_size-1) 
        {
            this->size++; 
            arr[size-1] = element;
        }
        else //reallocation of the main array 
        {
            max_size *=2; 
            T *new_arr = new T[max_size];
            for(int i = 0; i < size; i++) 
                new_arr[i] = arr[i];
            delete []arr;
            arr = new_arr;
            new_arr = NULL;
        }
    }
    void pop(){if(size)this->size--;} //decrease size
    T top(){ if(size)return arr[size-1]; } //get the top element from array
    int get_size(){ return size; } //return size
    ~RlenStack(){ delete []arr; } //free memory
};
```
and the usage might be:
```cpp
int main()
{
	RlenStack<int> *r = new RlenStack<int>;
	r->push(4);
	delete r;
}
```

## Queue

Queue follows the FIFO order (first in first out).

This is a simple diagram of a queue.

![Diagram](Assets/Data2.png)

So um, I'm just gonna implement that in c++.
```cpp
template <class T>
class RlenQueue{
    int back_i = 0;
    int front_i = 0;
    int max_size = 0;
    T *arr = NULL;
public:
    RlenQueue(int max_size){ this->arr = new T[max_size]; this->max_size = max_size;} 
    void push(T element){arr[front_i] = element; if(front_i < max_size-1)front_i++; else front_i = 0;}
    void pop(){if(back_i<max_size-1)back_i++;else back_i = 0;}
    T front(){return arr[back_i];}
    int get_size(){ return back_i < front_i ? front_i - back_i : max_size-1-back_i+front_i; }
    ~RlenQueue(){ delete []arr; }
};
```
This driver code:
```cpp
int main()
{
	RlenQueue<int>q(10);
	for(int i = 1; i <= 6; i++)
		q.push(i);
	std::cout << q.front() << "\n";
	q.pop();
	std::cout << q.front() << "\n";
	q.push(2);
}
```
would output:
```sh
1
2
```
So it works :D

## Matrix

Matrix is a rectangular array of numbers.
Those are some examples of matrix.

![Diagram](Assets/Data3.png)

### Multiplying each element

Let's consider this matrix `int t[3][4]`:
```
[1][1][2][3]
[6][5][4][3]
[7][8][9][9]
```
If we wanted to multiply all the elements by `6` we would have to do this:
```cpp
for(int i = 0; i < 3; i ++) //there are three rows
    for(int j = 0; j < 4; j++) //4 elements each
        t[i][j] = t[i][j]*6;
```

### Adding two matrices

Let's consider this two matrices `int t[3][4]` and `int w[3][4]`:
```
[1][1][2][3]
[6][5][4][3]
[7][8][9][9]

[7][8][9][9]
[1][1][2][3]
[6][5][4][3]
```
What if we wanted to add `w` to `t` and store the sum in `int c[3][4]`.

It would look like this:
```cpp
for(int i = 0; i < 3; i ++) //there are three rows
    for(int j = 0; j < 4; j++) //4 elements each
        c[i][j] = w[i][j] + t[i][j];
```

### Rotating

You spin me right round! round round! Like a rocket baby right round! round round! 

We want to make this `matrix[3][4]`:
```
[7][8][9][9]
[1][1][2][3]
[6][5][4][3]
```
Look like this:
```
[9][3][3]
[9][2][4]
[8][1][5]
[7][1][6]
```
The algorithm for that is easy.

This is my simple implementation of it
```cpp
int matrix[3][4] = {{7,8,9,9},{1,1,2,3},{6,5,4,3}}; //previous matrix

int new_matrix[4][3]; //rotated matrix

for(int j = 3; j >= 0; j--) //go through all the columns from right to left
    for(int i = 0; i < 3; i++) //from top to bottom
    {
        new_matrix[3-j][i] = matrix[i][j]; 
    }

//printing out the array
for(int i = 0; i < 4; i++)
{
	std::cout << "\n";
	for(int j = 0; j < 3; j++)
	{
		std::cout << new_matrix[i][j] << " ";
	}
}
```
The output should be:
```
9 3 3 
9 2 4 
8 1 5 
7 1 6
```
And that's right :).

<!-- {% endraw %} -->
