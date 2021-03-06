<!-- {% raw %} -->

# Data structures

<!-- TOC -->

- [Data structures](#data-structures)
  - [What even is data structure?](#what-even-is-data-structure)
  - [Stack](#stack)
  - [Queue](#queue)
  - [Matrix](#matrix)
  - [Linked list](#linked-list)
  - [Binary tree](#binary-tree)
  - [Graph](#graph)

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

Multiplying each element:

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

Adding two matrices:

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

Rotating:

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

## Linked list

![Diagram](Assets/Data5.png)

Like the name suggests it's a data structure with dynamic memory usage.
You can easily add and remove items from it. That's because every node has a pointer to the next node (Or to NULL).

Unlike in traditional arrays here you don't assign any type of indexes.
If you want to access it's tenth or seventh element you need to manually iterate through seven elements. That's a cost for being smart :(

To implement it we need to implement a simple class for a single node.

```cpp
class rlen_node{
public:
	rlen_node(int data){this->data = data; this->next = NULL;} //constructor
	rlen_node* next;
	int data;
};
```

Now we can try to implement some simple functions to add/remove nodes.

```cpp
void add_node(rlen_node* head, int data)
{
	while(head->next != NULL) //go until found tail (node not connected to anything)
		head = head->next;
	head->next = new rlen_node(data);
}

void delete_front(rlen_node* head)
{
	while(head->next->next != NULL)
		head = head->next;

	if(head->next == NULL)
		delete head;
	else
	{
		delete head->next;
		head->next = NULL;
	}
}
void delete_at_index(rlen_node* head, int index)
{
	int depth = 0;
	while(head->next != NULL && depth < index-1)
	{
		depth++;
		head = head->next;
	}
	if(depth == index-1)
	{
		if(head->next->next != NULL)
		{
			rlen_node* x = head->next->next;
			delete head->next;
			head->next = x;
		}
		else
		{
			delete head->next;
			head->next = NULL;
		}
	}
	else
		std::cerr << "Could not find any node at that index\n";
}

void delete_list(rlen_node* head)
{
	while(head->next != NULL)
	{
		delete_front(head);
	}
	delete head;
}

void print_list(rlen_node* head)
{
	std::cout << head->data << " -> ";
	while(head->next != NULL) //go until found tail (node not connected to anything)
	{
		head = head->next;
		std::cout << head->data << " -> ";
	}
	std::cout << "NULL\n";
}
```

With this driver code:

```cpp
int main()
{
	rlen_node *head = new rlen_node(1);
	print_list(head);
	add_node(head, 2);
	add_node(head, 3);
	add_node(head, 4);
	add_node(head, 5);
	print_list(head);
	delete_front(head);
	delete_front(head);
	print_list(head);
	add_node(head, 4);
	add_node(head, 5);
	print_list(head);
	delete_at_index(head, 3);
	print_list(head);
	delete_list(head);
}
```

The output is:

```sh
1 -> NULL
1 -> 2 -> 3 -> 4 -> 5 -> NULL
1 -> 2 -> 3 -> NULL
1 -> 2 -> 3 -> 4 -> 5 -> NULL
1 -> 2 -> 3 -> 5 -> NULL
```

Which is good.

## Binary tree

This is what a binary tree looks like:

![Diagram](Assets/Data4.png)

To implement it in C++ we would have to first define a structure.

```cpp
struct rlen_node
{
    int key;
    rlen_node *left;
    rlen_node *right;
};
```

It contains only an integer **key** variable and two pointers.

Those two pointers are there to point to newly added leaves (Or to NULL if there's nothing).

Now we can implement functions to add and delete leaves.

```cpp
void delete_tree(rlen_node *leaf)
{
    if (leaf != NULL)
    {
        delete_tree(leaf->left); // recursion to get rid of all the leaves on the left
        delete_tree(leaf->right);  // on the right too
        delete leaf;
    }
}

void add_node(int key, rlen_node *leaf)
{
    if (key < leaf->key) // if smaller go to the left
    {
        if (leaf->left == NULL)
        {
            leaf->left = new rlen_node;
            leaf->left->key = key;
            leaf->left->left = NULL;
            leaf->left->right = NULL;
        }
        else
            add_node(key, leaf->left);
    }
    else // otherwise to the right
    {
        if (leaf->right == NULL)
        {
            leaf->right = new Rlen_node;
            leaf->right->key = key;
            leaf->right->left = NULL;
            leaf->right->right = NULL;
        }
        else
            add_node(key, leaf->right);
    }
}
```

## Graph

Graph is essentially a set of vertices and a set of edges.

1. Graph order - how many vertices are there
1. Graph size - how many edges are there

This is a simple example of a graph:

![Diagram](Assets/Data6.png)

There are 5 vertices and 7 edges.

This is a planar graph because it's made in a way that no edges are overlapping each other.

This graph also is a not directed graph because there aren't any directed edges.

A simple example of a directed graph would be this:

![Diagram](Assets/Data7.png)

We can see there that this E2 edge is a loop.

If we wanted to go from _V4_ to _V1_ we would have to take this path:

_V4_ -> _V3_ -> _V1_

If we wanted to go from _V1_ to _V4_ we would have to take this path:

_V1_ -> _V2_ -> _V3_ -> _V4_

Notice how this time we weren't able to avoid going through _V2_

There's also a thing called edge weight. It's just a value describing an edge.
It's useful when you combine graph with real-life examples. _(Roads aren't always the same size)_

You might be asking yourself a question.

Maybe even a few of those.

Why?! How?! Where?!

Honestly I don't care enough to respond to all three of those but I'll try to respond to at least one.

How does it even work in practice?

It's not that simple.
There are multiple ways implement a graph.

We can implement a _*Adjacency matrix*_ to represent edges.

The philosophy behind it is simple.

For this graph:

![Diagram](Assets/Data7.png)

The Adjacency matrix would look like this:

```sh
[0][1][0][0] //because v1 is connected to v2
[0][0][1][0] //because v2 is connected to v3
[1][0][0][1] //because v3 is connected to v1 and v4
[0][0][1][1] //because v4 is connected to v3 and v4 (loop)
```

That means that if you have a graph with _m_ vertices the adjacency matrix is going to contain _m<sup>2</sup>_ bool values. Every bool value indicates if there's an edge between those i and j indexes in an array.

If this graph was not directed then the adjacency matrix would look like this:

```sh
[0][1][1][0] //because v1 is connected to v2 and v3
[1][0][1][0] //because v2 is connected to v1 and v3
[1][1][0][1] //because v3 is connected to v1 and v2 and v4
[0][0][1][1] //because v4 is connected to v3 and v4 (loop)
```

There's also a _probably_ better way of saving those edges.

Now we are going to be creating adjacency lists.

For every single node. We'll create a list of nodes that this node is connected to.

![Diagram](Assets/Data7.png)

For this graph the adjacency lists would look like this:

```sh
1: [2]
2: [3]
3: [1][4]
4: [3][4]
```

If we had _m_ edges then It'd take _m_ memory

<!-- {% endraw %} -->
