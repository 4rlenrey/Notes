
# Math

<!-- TOC -->

- [Math](#math)
    - [Uh huh?](#uh-huh)
    - [Primes](#primes)
        - [What is a prime](#what-is-a-prime)
        - [Coprime numbers](#coprime-numbers)
    - [Carmichael function](#carmichael-function)
        - [Modular exponentiation](#modular-exponentiation)
            - [Memory-efficient method](#memory-efficient-method)
            - [Even more efficient method:](#even-more-efficient-method)

<!-- /TOC -->

## Uh huh?
---

I was supposed not to make a markdown math file. But yeah, didnt know where to put some of the stuff I needed to understand/learn in cryptography.


## Primes

### What is a prime
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
	long long w = 0;
	std::vector<int> coprimes;
	
	for(int i = 1; i <= x; i++)
	{
		if(greatest_common_divisor(i, x) == 1)
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
			if(std::pow(c, m)%x == 1) //pow should be changed to a memory-efficient function that supports modulo
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

