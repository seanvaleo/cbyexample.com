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
  * [Ternary Operator](#ternary-operator)
  * [Address Resolution Operator](#address-resolution-operator)
  * [Dereference Operator](#dereference-operator)
  * [Pointers](#pointers)
  * [Pointer Arithmetic](#pointer-arithmetic)
  * [Structs](#structs)
  * [Union](#union)
  * [Input & Output](#input--output)
  * [Bitwise Operations](#bitwise-operations)
  * [Typedef](#typedef)
  * [Enumerations](#enumerations)
  * [Variadic Functions](#variadic-functions)
  * [Threads](#threads)
  * [Mutex](#mutex)
  * [Heap Allocation](#heap-allocation)
  * [Assertions](#assertions)
  * [Compound Assignment](#compound-assignment)
  * [Pass by Reference](#pass-by-reference)
  * [Range](#range)
  * [Namespaces](#namespaces)
  * [Classes](#classes)
  * [Class Methods](#class-methods)
  * [Constructors & Destructors](#constructors--destructors)
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
Every variable has an associated data type that defines its data storage format. Each type requires a certain amount of memory and permits a relevant set of operations.
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
Comments are used to write notes and documentation that is to be ignored by the compiler at build time.
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
An array is a collection of items stored at contiguous memory locations. Elements in an array can be accessed randomly using indices.
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
A string is an array of characters. C++ supports **string** types natively, but in C, a string is an array of **char** data, terminated with the '\0' character.
#### C17
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
Functions are re-usable code segments, created to perform specific tasks.
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
Loops allow for continuous execution of a statement or group of statements, usually until a condition is met.
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
Loops allow continuous execution of a statement or group of statements, usually until a condition is met.
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
Used to jump between code sections. The use of **goto** is contraversial as it can promote bad code decisions, but it can be very useful for avoiding large nested 'if' statements.
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
A program can optionally take a set of arguments from the user at launch.
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
Modules are a new method in C++ to allow for better package management and easier library integration.
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
Define the storage duration of an object.
#### C17
```c
int main() {
	auto int x; // automatic duration - scope lifetime
	extern int x; // defined elsewhere
	static int x; // hold value between invocations
	register int x; // store in CPU register for fast access
	return 0;
}
```
#### C++20
```cpp
int main() {
	extern int x; // defined elsewhere
	static int x; // hold value between invocations
	register int x; // store in CPU register for fast access
	return 0;
}
```

## Type Qualifiers
A way of expressing additional information about a value through the type system to ensure correctness in the use of the data.
#### C17
```c
int main() {
	restrict int* x; // x should only be accessed from this pointer
	const int x; // x, once defined, is constant and cannot be changed
	atomic int x; // x can only be modified by one thread at a time
	volatile int x; // x can be modified externally. the program will check x's value before using it, even if it hasn't been modified locally.
	return 0;
}

```
#### C++20
```cpp
int main() {
	restrict int* x; // x should only be accessed from this pointer
	const int x; // x, once defined, is constant and cannot be changed
	atomic int x; // x can only be modified by one thread at a time
	volatile int x; // x can be modified externally. the program will check x's value before using it, even if it hasn't been modified locally.
	return 0;
}
```

## Inline Functions
Directly include the given function in the caller code sequence. This ensures that: function call overhead doesn’t occur ; overhead of push/pop variables on the stack is eliminated ; overhead of the return call is eliminated ; context-specific optimizations can be enabled at compile time.
#### C17
```c
#include <stdio.h>

inline void square(int* x) {
	*x *= *x;
	return;
}

int main() {
	int num = 5;
	square(&num);
	printf("%d\n", num);
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

inline void square(int& x) {
	x *= x;
	return;
}

int main() {
	int num = 5;
	square(num);
	cout << num << endl;
	return 0;
}
```
```
output: 5
```

## Conditional If
Responsible for modifying the flow of execution in a program. Always used with a condition, which is evaluated first before executing any statement inside the body.
#### C17
```c
#include <stdio.h>

int main() {
	int x = 4;
	if(!x) printf("x is 0\n"); // one line if statement
	else if(x < 0) printf("x is negative\n");
	else { // or you can use a block			
		printf("x is positive\n", x);
	}
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	if(int x = 4 ; !x) cout << "x is 0" << endl; // one line if statement with optional init statement before condition
	else if(x < 0) cout << "x is negative" << endl;
	else { // or you can use a block
		cout << "x is positive" << endl;
	}	
	return 0;
}
```
```
output: x is positive
```

## Ternary Operator
A conditional operator that provides a shorter syntax for the **if** statement. The first operand is a boolean expression; if the expression is true then the value of the second operand is returned otherwise the value of the third operand is returned.
#### C17
```c
#include <stdio.h>

int main() {
	int x = 4;
	x < 0 ? printf("x is negative\n") : printf("x is 0 or positive\n");
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	int x = 4;
	x < 0 ? cout << "x is negative" << endl : cout << "x is 0 or positive" << endl;
	return 0;
}
```

## Address Resolution Operator
Use '&' before a variable name to use it's address in memory rather than the value stored.
#### C17
```c
#include <stdio.h>

int main() {
	int x = 5;
	printf("The address of x is %p\n", (void*)&x);
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	int x = 5;
	cout << "The address of x is" << &x << endl;
	return 0;
}
```

## Dereference Operator
Use '\*' before a variable name to use the value it points to rather than the address stored.
#### C17
```c
#include <stdio.h>

int main() {
	int x = 4;
	int* y = &x;
	printf("the value stored at x is %d\n", *y);
	return 0;
}
```
#### C++20
```cpp
#include <iostream>

int main() {
	int x = 4;	
	int* y = &x;
	cout << "the value stored at x is" << *y << endl;
	return 0;
}
```

## Pointers
A pointer is a variable that can hold the address of another variable. Just like regular data types, they must have their own type which refers to the type of the data at the address pointed to.
#### C17
```c
#include <stdio.h>

int main() {
	int* x; // pointer to type int
	return 0;
}
```
#### C++20
```cpp
#include <iostream>

int main() {
	int* x; // pointer to type int
	return 0;
}
```

## Pointer Arithmetic
Perform integer addition or subtraction operations on pointers, taking the data type's size into account to return the correct address of the next item.
#### C17
```c
#include <stdio.h>

int main() {
	int x = 12, *x_ptr = &x;
	char y = 'a', *y_ptr = &y;
	printf("Value of x_ptr = %p\n", (void*)x_ptr);
	printf("Value of y_ptr = %p\n", (void*)y_ptr);
	printf("Value of x_ptr + 1 = %p\n", (void*)(x_ptr + 1));
	printf("Value of y_ptr + 1 = %p\n", (void*)(y_ptr + 1));
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	int x = 12, *x_ptr = &x;
	char y = 'a', *y_ptr = &y;
	cout << "Value of x_ptr = " << &x_ptr << endl;
	cout << "Value of y_ptr = " << &y_ptr << endl;
	cout << "Value of x_ptr + 1 = " << &(x_ptr + 1) << endl;
	cout << "Value of y_ptr + 1 = " << &(y_ptr + 1) << endl;
	return 0;
}
```
```
Output: Value of x_ptr = 492316
        Value of y_ptr = 492303
        Value of x_ptr + 1 = 492320
        Value of y_ptr + 1 = 492304
```

## Structs
Structs are user defined data storage objects containing public members by default.
#### C17
```c
#include <stdio.h>

struct my_struct {
	int x;
	int y;
};

int main() {
	struct my_struct object1;
	object1.x = 1;
	printf("%d\n", object1.x);
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

struct my_struct {
	int x;
	int y;
};

int main() {
	struct my_struct object1;
	object1.x = 1;
	cout << object1.x << endl;
	return 0;
}
```
```
output: 1
```

## Union
A union is a special data type that can store different data types at the same memory location. You can define a union with many members, but only one member can contain a value at any given time. Unions provide an efficient way of using the same memory location for multiple purposes. A union's size will be the size of the largest constituent type.
#### C17
```c
#include <stdio.h>

union my_data {
	int i;
	float f;
	char str[20];
};
 
int main() {
	union my_data object1;        
	printf("Size of my_data union: %d\n", sizeof(object1));
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

union my_data {
	int i;
	float f;
	char str[20];
};

int main() {
	union my_data object1;        
	cout << "Size of my_data union: " << sizeof(object1) << endl;
	return 0;
}
```
```
Output: Size of my_data union: 20
```

## Input & Output
In C, interacting with the user console is made possible through the **stdio.h** (standard input output library) header, which contains methods for input and output. C++ provides a convenient abstraction built into the **iostream** header, known as streams, to perform input and output operations in sequential media such as the screen, the keyboard or a file. A stream is an entity that a program can use to either insert or extract data.
#### C17
```c
#include <stdio.h>

int main() {
	int x;
	printf("Enter an integer value for x: ");
	scanf("%d", &x);
	printf("The value at x is now: %d\n", x);
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	int x;
	cout << "Enter an integer value for x: ";
	cin >> x;
	cout << "The value at x is now: " << x << endl;
	return 0;
}
```
```
output: Enter an integer value for x: 6
        The value at x is now: 6
```

## Bitwise Operations
Bitwise operators are used to perform bit-level operations.
#### C17
```c
#include <stdio.h>

int main() {

	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Typedef
#### C17
Used to add an additional name to a type. Useful when working with more complex types, making them more human readable.
```c
#include <stdio.h>

int main() {
	unsigned char a = 5; // 00000101
	unsigned char b = 9; // 00001001
	printf("a & b = %d\n", a & b); // 00000001
	printf("a | b = %d\n", a | b); // 00001101
	printf("a ^ b = %d\n", a ^ b); // 00001100
	printf("~a = %d\n", a = ~a); // 11111010
	printf("b << 1 = %d\n", b << 1); // 00010010
	printf("b >> 1 = %d\n", b >> 1); // 00000100
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	unsigned char a = 5; // 00000101
	unsigned char b = 9; // 00001001
	cout <<	"a & b = " << (a & b) << endl; // 00000001
	cout <<	"a | b = " << (a | b) << endl; // 00001101
	cout <<	"a ^ b = " << (a ^ b) << endl; // 00001100
	cout <<	"~a = " << (~a) << endl; // 11111010
	cout << "b << 1 = " << (b << 1) << endl; // 00010010
	cout <<	"b >> 1 = " << (b >> 1) << endl; // 00000100
	return 0;
}
```
```
output: a & b = 1
        a | b = 13
        a ^ b = 12
        ~a = 250
        b << 1 = 18
        b >> 1 = 4
```
## Enumerations
A user-defined data type, used to assign names to integral constants to make a program easier to read and maintain.
#### C17
```c
#include <stdio.h>

enum week {
	mon,
	tue,
	wed,
	thu,
	fri,
	sat,
	sun
};

int main() {
	for(int i = mon; i <= sun; i++)
	{
		printf("%d ", i); 
	} 
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

enum week {
	mon,
	tue,
	wed,
	thu,
	fri,
	sat,
	sun
};

int main() {
	for(int i = mon; i <= sun; i++)
	{
		cout << i << endl; 
	} 
	return 0;
}
```
```
output: 0
        1
        2
        3
        4
        5
        6
```

## Variadic Functions
Create a function with an arbitrary argument count for more flexibility.
#### C17
```c
#include <stdio.h>
#include <stdarg.h>

int sum(int count, ...)
{
	int total, i, temp;
	total = 0;
	va_list args;
	va_start(args, count);
	for(int i = 0; i < count; i++) {
		temp = va_arg(args, int);
        	total += temp;
	}
	va_end(args);
	return total;
}

int main() {
	int numbers[3] = {5, 10, 15};
	int sum_of_numbers = sum(3, numbers[0], numbers[1], numbers[2]);
	printf("Sum of the array %d\n", sum_of_numbers);
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int sum(int count, ...)
{
	int total, i, temp;
	total = 0;
	va_list args;
	va_start(args, count);
	for(int i = 0; i < count; i++) {
		temp = va_arg(args, int);
        	total += temp;
	}
	va_end(args);
	return total;
}

int main() {
	int numbers[3] = {5, 10, 15};
	int sum_of_numbers = sum(3, numbers[0], numbers[1], numbers[2]);
	cout << "Sum of the array << sum_of_numbers << endl;
	return 0;
}
```
```
output: 30
```

## Threads
Used to execute one or more subthreads to allow for parallel processing in the same memory space, usually resulting in a performance improvement in a larger program.
#### C17
```c
#include <stdio.h>
#include <threads.h>

int thread_func(void* arg) { 
	printf("Printing from Thread\n"); 
	return NULL;
} 
   
int main() { 
	thrd_t thread_id; 
	thrd_create(&thread_id, thread_func, NULL); 
	thrd_join(thread_id, NULL);  // Wait for thread to return before continuing execution
	printf("Thread returned\n"); 
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
#include <thread>
using namespace std;

void thread_func() {
	cout << "Printing from Thread" << endl;
	return NULL;
}

int main() {
	thread thread_obj(thread_func);
	thread_obj.join();
	cout << "Thread returned" << endl;
	return 0;
}
```
```
output: Printing from Thread
        Thread returned
```

## Mutex
Mutual exclusion functionality. Can be used to serialize access of shared variables between concurrent threads.
#### C17
```c
#include <stdio.h>
#include <threads.h>

typedef struct data {
	mtx_t mtx;
	int x;
} data;

int thread_func(void* arg) { 
	data* d = (data*)arg;
	mtx_lock(&d->mtx);	
	d->x = 2;	
	mtx_unlock(&d->mtx);
	return 0;
} 
   
int main() {
	data d;
	mtx_init(&d.mtx, mtx_plain);
	thrd_t thread_id; 
	thrd_create(&thread_id, thread_func, (void*)&d); 
	thrd_join(thread_id, NULL);  // Wait for thread to return before continuing execution
	printf("x has safely been modified to %d\n", d.x); 
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
#include <thread>
#include <mutex>
using namespace std;

typedef struct data {
	mutex mtx;
	int x;
} data;

void thread_func(data* d) { 
	const lock_guard<mutex> lock(d->mtx);
	d->x = 2;	
	return;
} 
   
int main() {
	data d;
	thread thread_obj(thread_func, &d); 
	thread_obj.join();  // Wait for thread to return before continuing execution
	cout << "x has safely been modified to " << d.x << endl; 
	return 0;
}
```

## Heap Allocation
Memory can be allocated on the heap, an unreserved and relatively large region of memory outside of the program's memory scope.
#### C17
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
	int* x = (int*)malloc(sizeof(int)); // pointer to a heap-reserved integer
	if(x) { // test that the memory was allocated before you use it
		free(x); // you must manually free any memory you allocated on the heap or it will persist (memory leak)
	}
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
#include <new>
using namespace std;

int main() {
	int* p  = new(int); // pointer to a heap-reserved integer
	if(p != nullptr) { // test that the memory was allocated before you use it
		delete p; // you must manually free any memory you allocated on the heap or it will persist (memory leak)
	}
	return 0;
}
```

## Assertions
Statements used to explicitly test assumptions made by the programmer. Will be checked at runtime, or if static at compile time. A powerful tool for statement or unit testing.
#### C17
```c
#include <stdio.h>
#include <assert.h>

int main() {
	int x = 1;
	assert(x == 2); // this should break the execution of the program
	return 0;
}
```
#### C++20
```cpp
#include <assert.h>

int main() {
	int x = 1;
	assert(x == 2); // this should break the execution of the program
	return 0;
}
```
```
output: int main(): Assertion `x == 2' failed. 
```

## Compound Assignment
Provides a shorter syntax for assigning the result of an arithmetic or bitwise operator by performing an operation on the two operands before assigning the result to the first operand.
#### C17
```c
#include <stdio.h>

int main() {
	int x = 1;
	x += 1;
	printf("x = %d\n", x);
	return 0;
}
```
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	int x = 1;
	x += 1;
	cout << "x = " << x << endl;
	return 0;
}
```
```
output: x = 2
```

## Pass by Reference
Use the **&** symbol as an alternative to passing an address by pointer or passing by value.
#### C++20
```cpp
#include <iostream>
using namespace std;

void square(int& x) {
	x *= x;
	return;
}

int main() {
	int x = 2;
	square(x);
	cout << x << endl;
	return 0;
}
```
```
output: 4
```

## Range
Used as a more readable equivalent to a traditional loop when iterating over a range of data.
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Namespaces
A declarative region that provides a named scope to its constituent identifiers. Useful for organizing and reducing ambiguity in code.
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Classes
A user-defined data structure template declared with keyword **class** containing member functions and data.
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Class Methods
Functions in a class.
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Constructors & Destructors
A special member function of a class used to instantiate the class object.
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Virtual Functions
Used to facilitate runtime polymorphism by allowing redefinition of a base class function.
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Friend Functions
A function of a class defined outside of its scope but with the right to access all private and protected members of the class.
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Encapsulation
Fundamental OOP concept used to group together data and functions, and provide varying levels of abstraction from the user.
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Inheritance
Fundamental OOP concept. The capability of a class to derive properties and characteristics from another class.
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Polymorphism
Fundamental OOP concept. Allows operations or objects to behave differently in different contexts. Through runtime function overriding (using virtual functions) or, as below, through compile-time function overloading by creating more than one function with the same name but different parameters.
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Templates
A blueprint for creating a generic class or function. The foundation of generic programming, which involves writing code in a way that is independent of any particular type.
#### C++20
```cpp
#include <iostream>
using namespace std;

int main() {
	
	return 0;
}
```

## Project Structure
It's useful to follow a conventional and sensible structure when organizing a project, to maintain readability.
#### C17
```
src/myproject/main.c // main function
src/myproject/include/file.c // function definitions
src/myproject/include/file.h // structs, function prototypes
src/myproject/makefile // automated project build file
src/myproject/README.md // store any useful documentation or links to documentation in here
bin/file // executable output from compiler
```
#### C++20
```
src/myproj/main.cpp // main function
src/myproj/include/file.cpp // function definitions
src/myproj/include/file.hpp // classes, function prototypes
src/myproj/makefile // automated project build file
src/myproject/README.md // store any useful documentation or links to documentation in here
bin/file // executable output from compiler
```

Copyright &copy; 2019 Sean Valeo | [Source](https://github.com/seanvaleo/cbyexample "Source") | [Contributors](https://github.com/seanvaleo/cbyexample/blob/master/CONTRIBUTORS.txt "Contributors")

