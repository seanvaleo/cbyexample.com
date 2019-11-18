# C by Example

C is a general-purpose, procedural computer programming language designed by Dennis Ritchie. This guide intends to showcase some of the language's features in a user-friendly, progressive format.

Check out the list of examples below to get started.

  * [Hello World](#hello-world)
  * [Types](#types)
  * [Comments](#comments)
  * [Switch](#switch)
  * [Array](#array)
  * [Strings](#strings)
  * [Functions](#functions)
  * [For Loops](#for-loops)
  * [While Loops](#while-loops)
  * [Goto](#goto)
  * [Integer Promotion](#integer-promotion)
  * [Constants](#constants)
  * [Program Arguments](#program-arguments)
  * [Dependencies](#dependencies)
  * [Storage Class Specifiers](#storage-class-specifiers)
  * [Type Qualifiers](#type-qualifiers)
  * [Inline Functions](#inline-functions)
  * [Conditional If](#conditional-if)
  * [Arithmetic Operators](#arithmetic-operators)
  * [Ternary Operator](#ternary-operator)
  * [Address Resolution Operator](#address-resolution-operator)
  * [Dereference Operator](#dereference-operator)
  * [Pointers](#pointers)
  * [Pointer Arithmetic](#pointer-arithmetic)
  * [Threads](#threads)
  * [Structs](#structs)
  * [Atomic](#atomic)
  * [Union](#union)
  * [Input / Output](#input-/-output)
  * [Bitwise Operations](#bitwise-operations)
  * [Typedef](#typedef)
  * [Enumerations](#enumerations)
  * [Variadic Functions](#variadic-functions)
  * [Heap Allocation](#heap-allocation)
  * [Assertions](#assertions)
  * [Project Structure](#project-structure)

## Hello World

```c
#include <stdio.h>

int main() {
	printf("Hello World!\n");
	return 0;
}
```
```
output: Hello World!
```

## Types 

```c

```

## Comments

```c
/*
 * Multi-line comments are written like this.
 */

// Single-line comments are written like this
```

## Switch
Jump to a matching value. Usually cleaner to write than an if/else tree, and faster under the hood.
```c
int x = 2;
switch(x) {
	case 1:
	printf("One")
	break; // you must break the search or it will fall through to the next match.
	case 2:
	printf("Two")
	break;
	default: // if no match is found
	break;
}
```
```
output: 2
```

## Array

```c

```

## Strings

```c

```

## Functions

```c
// double the number passed in as 'x', returning the new value to the function caller.
int double_number_a(int x) {
	return 2 * x;
}

// double the number pointed to by 'x', storing the result in the original variable.
void double_number_b(int* x) {
	x *= 2;
}

int main() {
	int num = 5;
	printf("%d\n", double_number_a(num));
	printf("%d\n", num);
	double_number_b(&num);
	printf("%d\n", num);
}
```
```
output: 10
        5
        10
```

## For Loops

```c
for(int i = 1; i <= 3; i++) {
	printf("%d\n", i);
}
```
```
output: 1
        2
        3
```

## While Loops

```c
int x = 1;
while(x <= 3) {
	printf("%d\n", x++);
}
```
```
output: 1
        2
        3
```

## Goto

```c

```

## Integer Promotion

```c

```

## Constants

```c

```

## Program Arguments

```c
int main(int argc, char* argv) {
	for(int i = 0; i < argc; i++) {
		printf("%s", argv[i]);
	}
	return 0;
}
```
```
input: ./program arg1 arg2
```
```
output: program
        arg1
        arg2
```

## Dependencies
In file main.c:
```c
#include <stdio.h> // include a dependency from the system library
#include "prog.h" // include a local dependency from a relative path
```
In file prog.h:
```c
#ifndef PROG_H // only process the below if it hasn't already been processed in the current compilation.
#define PROG_H

// file contents here

#endif
```

## Storage Class Specifiers

```c

```

## Type Qualifiers

```c

```

## Inline Functions

```c

```

## Conditional If

```c

```

## Arithmetic Operators

```c

```

## Ternary Operator

```c

```

## Address Resolution Operator

```c

```

## Dereference Operator

```c

```

## Pointers

```c

```

## Pointer Arithmetic

```c

```

## Threads

```c

```

## Structs

```c

```

## Atomic

```c

```

## Union

```c

```

## Input / Output

```c

```

## Bitwise Operations

```c

```

## Typedef

```c

```

## Enumerations

```c

```

## Variadic Functions

```c

```

## Heap Allocation

```c

```

## Assertions

```c

```

## Project Structure
```c

```


Copyright Sean Valeo &copy; 2019 | [Source](https://github.com/seanvaleo/cbyexample "Source") | [Contributors](https://github.com/seanvaleo/cbyexample/blob/master/CONTRIBUTORS.txt "Contributors")

