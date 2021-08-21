<!-- {% raw %} -->

# Programming

<!-- TOC -->

- [Programming](#programming)
	- [First steps](#first-steps)
		- [Machine language](#machine-language)
		- [High-level language](#high-level-language)
	- [Design patterns](#design-patterns)

<!-- /TOC -->

## First steps
---

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

It looks a lot more readable for me. Especially because I know C.

## Design patterns
---

Content here

<!-- {% endraw %} -->
