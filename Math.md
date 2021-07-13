
# Math

<!-- TOC -->

- [Math](#math)
    - [Uh huh?](#uh-huh)
    - [Primes](#primes)
        - [What is a prime](#what-is-a-prime)
        - [Coprime numbers](#coprime-numbers)
    - [Carmichael function](#carmichael-function)

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
	unsigned long long w = 0;
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
			if(std::pow(c, m)%x == 1)
				coprimes_count++;
		}
	}
	return m;
}
```
One of the problems with C++ implementation of it is that this `std::pow(c, m)%x` is very memory inefficient.
It's because you somehow need to store the whole powers of c to the power of m and then you can do the modulo on it.
The more elegant way of doing it would be to create our own function `power_with_modulo`


