<!-- {% raw %} -->

# PHP

<!-- TOC -->

- [PHP](#php)
	- [What is it.](#what-is-it)
	- [Basics](#basics)
		- [Operators](#operators)
		- [Arithmetic](#arithmetic)
		- [Comparative](#comparative)
		- [Comments](#comments)
		- [Syntax](#syntax)
	- [Variables](#variables)
		- [Output](#output)
		- [Data types](#data-types)
		- [Casting](#casting)
		- [Strings](#strings)
	- [Flow control](#flow-control)
		- [Conditional](#conditional)
		- [Loops](#loops)
		- [Functions](#functions)

<!-- /TOC -->

## What is it.

It's a scripting language. It was designed to help with web pages having dynamic content.

Unlike Javascript it's not client side.

## Basics

Because it's server-side you need a server to use it.

If you're like me and you're using Debian, you should be able to easily install and use some HTTP server such as Apache or nginx.

Tho php 5.4 introduced a built-in development server so if you don't need to go production, you can just use it for the moment.

To use it I can just simply type:

```sh
php -S localhost:8000
```

Where `localhost` is my hostname and `8000` is the port I'll be using.

Now we can create a simple `index.php` file that contains:

```php
<?php
echo "Hello World";
?>
```

Now, when we go to `http://localhost:8000/` with our web browser, we can see a simple page that only has `Hello World`

One of the main reasons why PHP exists is to make dynamic HTML pages. That's why you can use php with HTML.

You can test it by modifying this `index.php` document.

```php
<!DOCTYPE html>
<html>
<head>
	<title>My dynamic site</title>
</head>
<body>
	<h1><?php echo "Hello world!"; ?></h1>
</body>
</html>
```

After visiting it on browser you can expect this document:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My dynamic site</title>
  </head>
  <body>
    <h1>Hello world!</h1>
  </body>
</html>
```

As you can see, there's no sign of php. There's only a `Hello world!` string

### Operators

Operators are almost identical to c++ ones.

### Arithmetic

| Operator | Definition                          | Example | Outcome |
| -------- | ----------------------------------- | ------- | ------- |
| $x + $y  | addition                            | 3 + 5   | 8       |
| $x - $y  | subtraction                         | 3 - 5   | -2      |
| $x / $y  | division                            | 4 / 2   | 2       |
| $x \* $y | multiplication                      | 3 \* 5  | 15      |
| $x % $y  | modulo                              | 5 % 3   | 2       |
| $x << $y | bitwise left shift (x \* pow(2, y)) | 5 << 3  | 40      |
| $x >> $y | bitwise right shift                 | 5 >> 3  | 0       |

### Comparative

| Operator | Definition           | Example | Outcome |
| -------- | -------------------- | ------- | ------- |
| $x == $y | x equal y            | 3 == 5  | false   |
| $x != $y | x not equal y        | 3 != 5  | true    |
| $x < $y  | x less than y        | 3 < 5   | true    |
| $x > $y  | x more than y        | 3 > 5   | false   |
| $x <= $y | x less or equal to y | 3 <= 5  | true    |
| $x >= $y | x more or equal to y | 3 >= 5  | false   |

### Comments

Unlike C++ and python, PHP supports both `#` and `//` single-line comments.
It also supports multiline comments with this syntax:

```php
<?php
echo "some code";
/*
Some
Multiline comment
*/
?>
```

### Syntax

A PHP script starts with `<?php` and ends with `?>`.

Statements end with a semicolon. `;`

Also, unlike those rookie languages PHP's keywords are not case sensitive.
That means, you can write something like this and it'll work:

```php
<?php
eChO "some text ";
ECHO "so you ";
echo "can see it works ";
?>
```

Output:

```txt
some text so you can see it works
```

That's pretty damn cool if you ask me.

## Variables

Similarly to python, variables in PHP are not hard-typed.
They start with the `$` sign, Then name.

Example:

```php
<?php
$variable_name = "Some value ";
echo $variable_name;
$variable_name = 4;
echo $variable_name;
?>
```

Output:

```txt
Some value 4
```

It's pretty easy.

Like in other languages, there are different variable scopes:

- static
- local
- global

```php
<?php
$variable_name = 3; // static variable, will throw an error when invoked in a function without the $GLOBALS['variable_name'] thing

echo $variable_name; // can be used here

function test_function() {
  $local_var = 5; // local scope
  global $global; // global scope, can't be created with =
  $GLOBALS['global'] = 5;

  $GLOBALS['global'] = $GLOBALS['variable_name'] + 5;
  echo " ", $GLOBALS['global'];
}

test_function();

?>
```

Output:

```txt
3 8
```

There's also this `static` keyword. It "saves" your local variable for when your function is invoked next time.

Example

```php
<?php
function without_keyword(){
	$x = 3;
	echo $x, " ";
	$x = $x + 3;
}

without_keyword();
without_keyword();

function with_keyword(){
	static $x = 3;
	echo $x, " ";
	$x = $x + 3;
}

with_keyword();
with_keyword();

?>
```

Output:

```txt
3 3 3 6
```

Everything makes sense _I hope_.

Also, cool thing is that you can actually store a variable name in a variable.
For example:

```php
<?php
$x = "test";
$y = "x";

echo $y, " ", $$y;

?>
```

Output:

```txt
x test
```

### Output

PHP provides mainly two ways of outputting data.

You can use `echo` and `print`

The main difference between them is that echo can take more than one argument. And print has a return value (unlike echo).

### Data types

You basically have a few data types:

1. String
2. int
3. float
4. Object
5. Bool
6. Resource
7. Array
8. NULL

If you want to get a type of a variable you just do:

```php
<?php
$var = array("x","y","z");
var_dump($var);
?>
```

Output:

```txt
array(3) { [0]=> string(1) "x" [1]=> string(1) "y" [2]=> string(1) "z" }
```

### Casting

To cast a variable you need to use a similar syntax to c++; For example, let's cast a float number to int.

```php
<?php
$x = 3.2;
$y = (int)$x;
echo $y;
?>
```

Output:

```txt
3
```

### Strings

PHP strings support a these methods:

1. `strlen("some string");`

   Outputs length of this string

2. `str_word_count("another string argument");`

   Outputs how many words does this string contain.

3. `str_replace("To replace", "replacement", "This is To replace");`

   Replaces part of a string _(Here the output would be: "This is replacement")_

4. `strrev("string to reverse")`

   Reverses a string

5. `strpos("string with words", "with");`

   Searches for a position of a specific text (Second argument)

## Flow control

Something to control your program's flow

### Conditional

There's `if` and `else` and `elseif`

It works like in c++.

```php
if(condition){
  some_code_if_true();
} elseif(another_condition){
  some_code_if_another_condition_true();
} else {
  some_code_if_false();
}
```

There's also c++'s switch.

```php
switch (some_var){
  case some_value:
    code_if_some_value();
    break;
  case another_value:
    code_if_another_value();
    break;
  default:
    code_if_none_value();
    break;
}
```

### Loops

There are different loops. 

Every one of them other than foreach is just like in c++ 


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
for($array as $value)
{
	do_stuff;
}
```

There are two keywords related to loops. `break` and `continue`.
`break` breaks out of a loop and `continue` skips one loop iteration

### Functions

In PHP functions are not really hard to create. 

```php
function name($name_of_arg)
{
    code;

    return $something;
}
```

This `return` keyword is not really necessary.



<!-- {% endraw %} -->
