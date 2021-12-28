<!-- {% raw %} -->

# PHP

<!-- TOC -->

- [PHP](#php)
	- [What is it.](#what-is-it)
	- [Basics](#basics)
		- [Comments](#comments)
		- [Syntax](#syntax)

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

<!-- {% endraw %} -->
