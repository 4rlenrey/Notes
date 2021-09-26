<!-- {% raw %} -->

# Programming

<!-- TOC -->

- [Programming](#programming)
	- [First steps](#first-steps)
		- [Machine language](#machine-language)
		- [High-level language](#high-level-language)
	- [Version control](#version-control)
		- [Repository](#repository)

<!-- /TOC -->

## First steps

Long time ago a guy named Alan Turing made a machine that was able to crack Enigma's ciphertext.
Even tho it's not similar to modern computers, in my opinion it's the perfect example of what you can accomplish with programming.
The idea for this machine was really simple but also complex. Mr. Alan wanted to make a laborious process of cryptoanalysis automated.

Now it didn't change too much. We still have a lot of manual repetitive jobs and we are constantly trying to make it done automatically by a machine.

Machine is just a lot of electrical pieces. Some can even say it's just a calculator. 
You need to make it so that the machine is doing the stuff it needs to do. Because machine isn't self aware or anything you need to program it.

Now we actually do not have to create a whole machine. We can just take a programable one and make it perform some tasks by programming it.

### Machine language

If we have a programable device then we need to have a programming language for that machine.
It most likely is just a instruction set with different instructions written in binary notation, so you are able to perform some actions whenever you need.

### High-level language

Writing in binary would probably be hard. That's why some smart people made different assemblers and then different compilers.
Compilers do a simple thing. They translate some sort of programming language code to Assembly code. Assembly code then is assembled to machine/object codes by assemblers.

It's cool because instead of having to write assembly code that might look like this:

<!-- cSpell:disable -->

```assembly
	.file	"hello_world.c"
	.text
	.section	.rodata
.LC0:
	.string	"Boring notes huh? "
.LC1:
	.string	"Check out C++11 it's\302\240cool "
	.text
	.globl	main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	pushq	%rbp
	.cfi_def_cfa_offset 16
	.cfi_offset 6, -16
	movq	%rsp, %rbp
	.cfi_def_cfa_register 6
	leaq	.LC0(%rip), %rdi
	call	puts@PLT
	leaq	.LC1(%rip), %rdi
	call	puts@PLT
	movl	$0, %eax
	popq	%rbp
	.cfi_def_cfa 7, 8
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.ident	"GCC: (Debian 8.3.0-6) 8.3.0"
	.section	.note.GNU-stack,"",@progbits
```
<!-- cSpell:enable -->

I can just write this:

```c
#include <stdio.h>
int main() {
   printf("Boring notes huh? \n");
   printf("Check out C++11 it's cool \n");
   return 0;
}
```

And use a *gcc* compiler to convert it to this assembly code.
(GCC Does not actually convert your c code to assembly by default. It compiles it to machine code. To do the conversion you can use the *`-S`* flag when compiling,)

It looks a lot more readable for me. Especially because I know C.

## Version control

When you're creating something you're almost constantly changing something.
This process of tinkering can lead to all sorts of problems and often it can break a whole app.
With version control software you can easily commit versions of your code and when something breaks you can return to the older version.

Here I'm going to be covering the tool named *`git`* and created by the famous Linus Torvalds and Junio C Hamano. It's used almost everywhere. I am using it while making these notes.

Because I prefer using cli version of git I'm going to be covering it here.

### Repository

First step to use git is to initialize a repository in some directory.
This directory should be your project's directory.

First we have to install git.

To do that on debian-based linux you can simply type:

```sh
$ sudo apt-get install git
```

Now we can create a directory for out project and then enter it:
```sh
$ mkdir my_project
$ cd my_project
```
We can then initialize this git repo.

```sh
$ git init
```

Now when we type:

```sh
$ ls -a
```

It'll print:

```
.git
```

That means that git created some hidden directory that contains all the info required for version control.
Now you can add some source files to it and then you can commit them.

You can commit all of them by simply doing

```
$ git add .
$ git commit -m "message about what you've changed"
```

This `add` instruction stages all the changes and this `commit` instruction commits them.

You can commit only some files:

```
$ git add example.txt
$ git commit -m "small documentation fix"
```

If you want to restore a version few commits back you can do
```
$ git reset --hard HEAD~2
```
You can use other numbers instead of this `2` depending how much commits do you want to cancel.

<!-- {% endraw %} -->
