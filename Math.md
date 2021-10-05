<!-- {% raw %} -->

# Math

<!-- TOC -->

- [Math](#math)
	- [Primes](#primes)
		- [Coprime numbers](#coprime-numbers)
	- [Carmichael function](#carmichael-function)
		- [Modular exponentiation](#modular-exponentiation)
			- [Memory-efficient method](#memory-efficient-method)
			- [Even more efficient method:](#even-more-efficient-method)
	- [Mathematical logic](#mathematical-logic)
		- [Logical sentences](#logical-sentences)
	- [Probability](#probability)
		- [Rule of multiplication](#rule-of-multiplication)
		- [Power of a set](#power-of-a-set)
		- [Permutations](#permutations)
		- [Factorial](#factorial)
		- [Variations](#variations)
			- [With repetitions:](#with-repetitions)
			- [Without repetitions:](#without-repetitions)
		- [Combinations](#combinations)

<!-- /TOC -->

## Primes

A number is prime when it can only be divided by one and itself.

Example: **3**, **5**, **7**

### Coprime numbers

Two numbers are coprime if their only common divisor is one.

Example: **14** and **25** _The only common divisor they have is one._

## Carmichael function

---

This function associates to every **positive** integer **x** a positive integer **&lambda;(x)**. Defined as the smallest possible integer **m** where:

**a<sup>m</sup>&Congruent;1 (mod x)**
for all **a** such as that **gcd(a, n) = 1**

Basically you need to find all the numbers that are less than **x** and that the greatest common divisor of them and **x** is **1** and you need to store them in a group.

Later you need to find the number **m** in a way that every number from this group fulfills this **a<sup>m</sup>&Congruent;1 (mod x)**
where a is a single number from this group, m is the number we are looking for, and x is the initial value we've provided.

This is my implementation of this function in C++:

```cpp
int carmichael(int x)
{
	if(x == 1)return 1;
	int m = 0, coprimes_count = 0;
	std::vector<int> coprimes;

	for(int i = 1; i <= x; i++)
	{
		if(std::gcd(i, x) == 1)
		{
			coprimes.push_back(i);
		}
	}
	while(coprimes_count != coprimes.size())
	{
		coprimes_count = 0;
		m++;
		for(const auto &c : coprimes)
		{
			if(rlen_pow(c, m, x) == 1) //custom modpow function
				coprimes_count++;
		}
	}
	return m;
}
```

One of the problems with C++ implementation of it is that this `std::pow(c, m)%x` is very memory inefficient.
It's because you somehow need to store the whole powers of c to the power of m and then you can do the modulo on it.
The more elegant way of doing it would be to create our own function `power_with_modulo`

### Modular exponentiation

You can do it in two ways:

#### Memory-efficient method

There's this math identity from modular arithmetic:

**(x*y) mod z = [(x mod z) * (y mod z)] mod z**

So let's use it for exponentiation:

```
x^3 = x * x * x

(x^3) mod z = [([(x mod z)(x mod z)] mod z) * (x mod z)] mod z
(x^4) mod z = [((x^3) mod z) * (x mod z)] mod z
(x^5) mod z = [((x^4) mod z) * (x mod z)] mod z
```

Yeah, to easily count the value of `x^30 mod z` we would have to first count `x^2 mod z` and then multiply it by `x mod z` and do `mod z` out of it to finally reach the power of 30

Example:

_Let's count `7^9 mod 50`_

```
1).  7^1 mod 50 = 7
2).  7^2 mod 50 = [(7^1 mod 50) * (7 mod 50)] mod 50 = 49
3).  7^3 mod 50 = [(7^2 mod 50) * (7 mod 50)] mod 50 = 43
4).  7^4 mod 50 = [(43 mod 50) * (7 mod 50)] mod 50 = 1
5).  7^5 mod 50 = [(1 mod 50) * (7 mod 50)] mod 50 = 7
6).  7^6 mod 50 = [(7 mod 50) * (7 mod 50)] mod 50 = 49
7).  7^7 mod 50 = [(49 mod 50) * (7 mod 50)] mod 50 = 43
8).  7^8 mod 50 = [(43 mod 50) * (7 mod 50)] mod 50 = 1
9).  7^9 mod 50 = [(1 mod 50) * (7 mod 50)] mod 50 = 7
```

We've successfully counted 7^9 mod 50 without having to count 7^9 (that being 40353607)

Now let's try to implement it in C++.

```cpp
int rlen_modpow(int base, int exp, int modulus)
{
    base %= modulus;
	int result = base;
	for(int i = 2; i <= exp; i++)
		result = (result % modulus * base) % modulus;
    return result;
}
```

#### Even more efficient method:

This is basically the same, but the main difference is that it uses exponentiation by squaring. I've covered that in my Algorithms notes.

This is how it'd look like:

```cpp
long rlen_pow(long base, int exponent, int modulus)
{
	long result = 1;
	while(exponent > 0)
	{
		if(exponent & 1) //check the last bit of exponent if it's set
		{
			result *= base % modulus; //result should be now multiplied by the corresponding power for a specific bit
		}
		base *= base % modulus; //make the base a bigger power
		exponent >>= 1; //shift bitwise to right to make the penultimate bit the last bit to later check it
	}
	return result;
}
```

## Mathematical logic

In here you basically worry about expressions that we can assign two possible values **`True`** and **`False`** also seen as **`1`** and **`0`**

True = 1

False = 0

### Logical sentences

Let's consider these sentences:

1. Sentence: "2 is an even number"

   - Value: 1

2. Sentence: "2 is an odd number"
   - Value: 0

They're simple because we can easily assign these logical values to them.
That's because they're built out of one logical statement.

And now let's consider these:

1. Sentence: "x is an even number when it's not odd"

   - Value: 1

2. Sentence: "2 is an odd number and 3 is an odd number"
   - Value: 0

It's harder to assign a binary value to it because it's built out of more than one logical statement.

## Probability

Title says it all.

### Rule of multiplication

When you're counting all the possibilities this rule is going to be really helpful.

For example:

How many different three letters length long strings can you generate (that use only capital letters)?

First, we have to note that those letters might repeat.

Because we have 24 letters in our alphabet, we can solve this task simply by just doing it this way:

24 _ 24 _ 24 = 13824

Simple explanation of it would be:

Those strings consist of three chars: `1`+`2`+`3`

- You can replace `1` with every single letter (There are 24)
- You can replace `2` with every single letter (There are 24)
- You can replace `3` with every single letter (There are 24)

That's why it's 24<sup>3</sup>.

### Power of a set

Let's consider this set.

A = {a,b,c,d}

It has 4 elements.
Because of that, it's power is equal to 4.


### Permutations

Let's think about this situation:

You have 6 people and you want to know how many possible arrangements of them there are.
For better imagination let's also think about 6 chairs.

1 chair - 1 person
2 chair - 2 person
3 chair - 3 person
4 chair - 4 person
5 chair - 5 person

This is one arrangement.

Now you can switch two people and you get another arrangement.

To count all the possibilities you cannot do 6<sup>6</sup>.
That's because one person can't occupy 6 chairs at the same time ;)

We can still use multiplication rule:

6 _(Everyone can sit at the first table)_ * 5 _(One person is sitting so now you can choose between 4)_ * 4 * 3 * 2 * 1 = 720

I'll write it again without my comments:

6 * 5 * 4 * 3 * 2 * 1 = 720

### Factorial

Formula looks like this:

n! = n * (n-1) * (n-2) * ... * 1

It's basically what I did seconds ago in this permutations section.

### Variations

Let's consider this set of characters:
A = {A,B,C,D,E,F,G,H,I}

Power of this `A` set is equal to 9

And now we want to create 4-letter strings out of them.

#### With repetitions:

To do that with repetitions we can just simply use the multiplication method: 

9 * 9 * 9 * 9 = 6561

#### Without repetitions:

Here we can still use multiplication method:

9 * 8 * 7 * 6 = 3024

That's the formula for it:

n - power of A
k - variation size

x = (n!)/(n-k)!

So permutations are different from variations because permutations are the same size as set the're made out of.

Variations can have specified size.


### Combinations

A combination is a k-element subset of a n-element set. (Note that {1,2} is the same subset as {2, 1})

If you'd have this set:

A = {A, B, C, D} _(n = 4)_

All the combinations would be: 

One element: _(k = 1)_
- {A}, {B}, {C}, {D}

Two elements: _(k = 2)_ 
- {AB}, {AC}, {AD}, {BC}, {BD}, {CD}

Three elements: _(k = 3)_
- {ABC}, {ABD}, {ABC}, {BCD}

Four elements: _(k = 4)_
- {ABCD}

The formula for counting how many combinations there are:

n!/k!*(n-k)!


<!-- {% endraw %} -->
