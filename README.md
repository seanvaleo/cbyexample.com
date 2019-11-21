<p style="text-align: center;">
<img src="assets/img/logo.png">
</p>

C and C++ are general-purpose computer programming languages. They are closely related but with significant differences.
This guide intends to showcase some of the features and differences of both languages in a user-friendly, progressive format.
This is not a substitution for in-depth study, but should serve well as an introduction or a refresher.

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
  * [Program Arguments](#program-arguments)
  * [Includes](#includes)
  * [Modules](#modules)
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
  * [Preprocessor](#preprocessor)
  * [Compound Assignment](#compound-assignment)
  * [Range](#range)
  * [Namespaces](#namespaces)
  * [Classes](#classes)
  * [Class Methods](#class-methods)
  * [Constructors / Destructors](#constructors-/-destructors)
  * [Virtual Functions](#virtual-functions)
  * [Friend Functions](#friend-functions)
  * [Encapsulation](#encapsulation)
  * [Inheritance](#inheritance)
  * [Overloading](#overloading)
  * [Templates](#templates)
  * [Project Structure](#project-structure)

## Hello World
#### C17
```c
#include <stdio.h>

int main() {
	printf("Hello World!\n");
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	cout << "Hello World!" << endl;
	return 0;
}
```
```
output: Hello World!
```

## Types 
#### C17
```c
#include <stdbool.h>  //for bool

int main() {
	int a; // Integer
	int b = 1; // You can initialize a variable when you declare it.
	unsigned int c; // Unsigned integers only store positive numbers. As a result, they have a higher positive range.
	short d; // Short integer
	long e; // Long integer
	float f; // Floating point integer
	double g; // Double-precision floating point integer
	bool h; // Boolean TRUE or FALSE
	char i; // Character
	void j; // No type
	return 0;
}
```
#### C++20
```cpp
int main() {
	int a; // Integer
	int b = 1; // You can initialize a variable when you declare it.
	unsigned int c; // Unsigned integers only store positive numbers. As a result, they have a higher positive range.
	short d; // Short integer
	long e; // Long integer
	float f; // Floating point integer
	double g; // Double-precision floating point integer
	bool h; // Boolean TRUE or FALSE
	char i; // Character
	void j; // No type
	auto k = 1; // Automatically infer type. Not a type in itself.
	return 0;
}
```

## Comments
#### C17, C++20
```c
/*
 * Multi-line comments are written like this.
 */

// Single-line comments are written like this.
```

## Switch
Jump to a matching value. Usually cleaner to write than an if/else tree, and faster under the hood.
#### C17
```c
#include <stdio.h>

int main() {
	int x = 2;
	switch(x) {
		case 1:
		printf("One")
		break; // You must break the search or it will fall through to the next match.
		case 2:
		printf("Two")
		break;
		default: // If no match is found.
		break;
	}
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	int x = 2;
	switch(x) {
		case 1:
		cout << "One" << endl;
		break; // You must break the search or it will fall through to the next match.
		case 2:
		cout << "Two" << endl;
		break;
		default: // If no match is found.
		break;
	}
	return 0;
}
```
```
output: Two
```

## Array
#### C17
```c
#include <stdio.h>

int main() {
	int my_array[5];
	int my_array_b[] = {0,1,2,3,4}; // You can init the array with it's elements. Size can be detected automatically here.

	for(size_t i = 0; i < sizeof(my_array); i++) {
		my_array[i] = i;
	}

	printf("%d\n", my_array[2]);
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	int my_array[5];
	int my_array_b[] = {0,1,2,3,4}; // You can init the array with it's elements. Size can be detected automatically here.

	for(size_t i = 0; i < sizeof(my_array); i++) {
		my_array[i] = i;
	}

	cout << my_array[2] << endl;
	return 0;
}
```
```
output: 2
```

## Strings
#### C17
In C, a string is an array of characters, terminated with the '\0' character.

```c
#include <stdio.h>

int main() {
	char greeting_a[6] = {'H','e','l','l','o','\0'};
	char greeting_b[] = "Hello";
	char* greeting_c = "Hello";
	return 0;
}
```
#### C++20
```cpp
#include <string>
using namespace std;

int main() {
	string str1 = "Hello";
	auto str1 = "Hello";
	return 0;
}
```

## Functions
#### C17
```c
#include <stdio.h>

// Double the number passed in as 'x', returning the new value to the function caller.
int double_number_a(int x) {
	return 2 * x;
}

// Double the number pointed to by 'x', storing the result in the original variable.
void double_number_b(int* x) {
	*x *= 2;
}

int main() {
	int num = 5;
	printf("%d\n", double_number_a(num));
	printf("%d\n", num);
	double_number_b(&num);
	printf("%d\n", num);
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

// Double the number passed in as 'x', returning the new value to the function caller.
int double_number_a(int x) {
	return 2 * x;
}

// Double the number pointed to by 'x', storing the result in the original variable.
void double_number_b(int* x) {
	*x *= 2;
}

int main() {
	auto num = 5;
	cout << double_number_a(num) << endl;
	cout << num << endl;
	double_number_b(&num);
	cout << num << endl;
	return 0;
}
```
```
output: 10
        5
        10
```

## For Loops
#### C17
```c
#include <stdio.h>

int main() {
	for(int i = 1; i <= 3; i++) {
		printf("%d\n", i);
	}
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	for (auto i = 1; i <= 3; i++) {
		cout << i << endl;
	}
	return 0;
}
```
```
output: 1
        2
        3
```

## While Loops
#### C17
```c
#include <stdio.h>

int main() {
	int x = 1;
	while(x <= 3) {
		printf("%d\n", x++);
	}
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	auto x = 1;
	while(x <= 3) {
		cout << x << endl;
	}
	return 0;
}
```
```
output: 1
        2
        3
```

## Goto
The use of goto is contraversial as it can promote bad code decisions.
However it can be very useful for avoiding large nested 'if' statements.
#### C17
```c
#include <stdio.h>

int main() {
	int x;
	scanf("%d", &x);
	if(x < 3) goto cleanup;
	// Program code here
	cleanup:
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	int x;
	cin >> x;
	if(x < 3) goto cleanup;
	// Program code here
	cleanup:
	return 0;
}
```

## Integer Promotion
Any operand whose type ranks lower than int is temporarily promoted to int or unsigned int for comparison.
#### C17
```c
#include <stdio.h>

int main() {
	char x = 'A';
	if(x < 'a') printf("Less than\n"); // x is promoted to int to compare it with the integer value of 'a'.
	else printf("Greater than or equal to\n");
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	auto x = 'A';
	if(x < 'a') printf("Less than\n"); // x is promoted to int to compare it with the integer value of 'a'.
	else printf("Greater than or equal to\n");
	return 0;
}
```
```
output: Less than
```

## Program Arguments
#### C17
```c
#include <stdio.h>

int main(int argc, char* argv[]) {
	for(int i = 0; i < argc; i++) {
		printf("%s\n", argv[i]);
	}
	return 0;
}
```
#### C++20
```cpp
#include <iostream>

int main(int argc, char* argv[]) {
	for(auto i = 0; i < argc; i++) {
		printf("%s\n", argv[i]);
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

## Includes
Includes are instructions to the preprocessor to include external code. External code is made up of at least a header file (interface) and a source file (implementation).

When compiling your program, **#include** the header, and link the source file at compile time.
#### C17
In file main.c:
```c
#include <stdio.h> // Include a dependency from the system library
#include "prog.h" // Include a local dependency from a relative path
```
In file prog.h:
```c
#ifndef PROG_H // Only process the below if it hasn't already been processed in the current compilation.
#define PROG_H

// File contents here

#endif
```
#### C++20
In file main.cpp:
```cpp
#include <iostream> // Include a dependency from the system library
#include "prog.hpp" // Include a local dependency from a relative path
```
In file prog.hpp:
```cpp
#ifndef PROG_HPP // Only process the below if it hasn't already been processed in the current compilation.
#define PROG_HPP

// File contents here

#endif
```

## Modules
Modules are a new method in C++ that act like packages.
#### C++20
In file foo.cpp:
```cpp
export module Foo;

namespace Bar {
	int f_internal() {
	        return 10;
	}

	export int f() {
		return f_internal();
	}
}
```
In file main.cpp:
```cpp
import std;
import Foo;
using namespace std;

int main() {
	cout << Bar::f() << endl;
	return 0;
}
```
```
output: 10
```

## Storage Class Specifiers
#### C17
```c

```
#### C++20
```cpp

```

## Type Qualifiers
#### C17
```c
const int x

```
#### C++20
```cpp

```

## Inline Functions
#### C17
```c

```
#### C++20
```cpp

```

## Conditional If
#### C17
```c

```
#### C++20
```cpp

```

## Arithmetic Operators
#### C17
```c

```
#### C++20
```cpp

```

## Ternary Operator
#### C17
```c

```
#### C++20
```cpp

```

## Address Resolution Operator
#### C17
```c

```
#### C++20
```cpp

```

## Dereference Operator
#### C17
```c

```
#### C++20
```cpp

```

## Pointers
#### C17
```c

```
#### C++20
```cpp

```

## Pointer Arithmetic
#### C17
```c

```
#### C++20
```cpp

```

## Threads
#### C17
```c

```
#### C++20
```cpp

```

## Structs
#### C17
```c

```
#### C++20
```cpp

```

## Atomic
#### C17
```c

```
#### C++20
```cpp

```

## Union
#### C17
```c

```
#### C++20
```cpp

```

## Input / Output
#### C17
```c

```
#### C++20
```cpp

```

## Bitwise Operations
#### C17
```c

```
#### C++20
```cpp

```

## Typedef
#### C17
```c

```
#### C++20
```cpp

```

## Enumerations
#### C17
```c

```
#### C++20
```cpp

```

## Variadic Functions
#### C17
```c

```
#### C++20
```cpp

```

## Heap Allocation
#### C17
```c

```
#### C++20
```cpp

```

## Assertions
#### C17
```c

```
#### C++20
```cpp

```

## Preprocessor
#### C17
```c

```
#### C++20
```cpp

```

## Compound Assignment
#### C17
```c

```
#### C++20
```cpp

```

## Range
#### C++20
```cpp

```

## Namespaces
#### C++20
```cpp

```

## Classes
#### C++20
```cpp

```

## Class Methods
#### C++20
```cpp

```

## Constructors / Destructors
#### C++20
```cpp

```

## Virtual Functions
#### C++20
```cpp

```

## Friend Functions
#### C++20
```cpp

```

## Encapsulation
#### C++20
```cpp

```

## Inheritance
#### C++20
```cpp

```

## Overloading
#### C++20
```cpp

```

## Templates
#### C++20
```cpp

```

## Project Structure
#### C17
```c

```
#### C++20
```cpp

```

Copyright &copy; 2019 Sean Valeo and contributors | [Source](https://github.com/seanvaleo/cbyexample "Source") | [Contributors](https://github.com/seanvaleo/cbyexample/blob/master/CONTRIBUTORS.txt "Contributors")

