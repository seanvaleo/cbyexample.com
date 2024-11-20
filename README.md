# C by Example

C and C++ are general-purpose computer programming languages. They are closely related but with significant differences.
This guide intends to showcase some of the features and differences of **both languages** in a user-friendly, progressive format.
This is not a substitution for in-depth study, but should serve well as an introduction or a refresher.

Inspired by <a href="https://gobyexample.com" target="_blank">Go By Example</a>, <a href="https://lotz84.github.io/haskellbyexample/" target="_blank">Haskell By Example</a>, <a href="http://jpryan.me/dartbyexample/" target="_blank">Dart By Example</a> and <a href="https://javascriptbyexample.com" target="_blank">Javascript By Example</a>.

Check out the list of examples below to get started:

  * [Hello World](#hello-world)
  * [Types](#types)
  * [Initialization](#initialization)
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
  * [Project Structure](#project-structure)
  * [Includes](#includes)
  * [Compilation](#compilation)

C++ only:

  * [Modules](#modules)
  * [Pass by Reference](#pass-by-reference)
  * [Range](#range)
  * [Namespaces](#namespaces)
  * [Classes](#classes)
  * [Class Methods](#class-methods)
  * [Constructors & Destructors](#constructors--destructors)
  * [Encapsulation](#encapsulation)
  * [Inheritance](#inheritance)
  * [Polymorphism](#polymorphism)
  * [Friend Functions](#friend-functions)
  * [Templates](#templates)
  * [Structured Bindings](#structured-bindings)
  * [Lambda Expressions](#lambda-expressions)
  * [Exception Handling](#exception-handling)

Programs:

  * [Linked List](#linked-list)
  * [Binary Search Tree](#binary-search-tree)
  * [Copy a File](#copy-a-file)
  * [Multithreaded Queue](#multithreaded-queue)

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

int main() {
    std::cout << "Hello World!" << std::endl;
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
    unsigned int b; // Unsigned integers only store positive numbers. As a result, they have a higher positive range.
    char c; // Character
    short d; // Short integer
    long e; // Long integer
    float f; // Floating point integer
    double g; // Double-precision floating point integer
    bool h; // Boolean TRUE or FALSE
    return 0;
}
```
#### C++20
```cpp
int main() {
    int a; // Integer
    unsigned int b; // Unsigned integers only store positive numbers. As a result, they have a higher positive range.
    char c; // Character
    short d; // Short integer
    long e; // Long integer
    float f; // Floating point integer
    double g; // Double-precision floating point integer
    bool h; // Boolean TRUE or FALSE
    auto k = 1; // Automatically infer type. Not a type in itself.
    return 0;
}
```

## Initialization
#### C17
```c
int main() {
    int a = 0;
    char greeting_a[6] = {'H','e','l','l','o','\0'};
    char greeting_b[] = "Hello";
    char* greeting_c = "Hello";
    return 0;
}
```
#### C++20
```cpp
#include <string>

int main() {
    int a = 0; // C-like initialization
    int b {0}; // Uniform initialization. Does not allow narrowing conversions.
    int c(0); // Constructor initialization
    char greeting_a[6] = {'H','e','l','l','o','\0'};
    char greeting_b[] = "Hello";
    char* greeting_c = "Hello";
    std::string greeting_d = "Hello";
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
Jump to a matching value. Can be cleaner to write than an if/else tree.
#### C17
```c
#include <stdio.h>

int main() {
    int x = 2;
    switch(x) {
    case 1:
        printf("One");
        break; // You must break the search or it will fall through to the next match.
    case 2:
        printf("Two");
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

int main() {
    int x = 2;
    switch(x) {
    case 1:
        std::cout << "One" << std::endl;
        break; // You must break the search or it will fall through to the next match.
    case 2:
        std::cout << "Two" << std::endl;
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
    int my_array_b[] = {0,1,2,3,4}; // You can init the array from it's elements. Size can be detected automatically here.

    size_t len = sizeof(my_array) / sizeof(my_array[0]);
    for(size_t i = 0; i < len; i++) {
        my_array[i] = i;
    }

    printf("%d\n", my_array[2]);
    return 0;
}
```
#### C++20
```cpp
#include <iostream>
#include <array>

int main() {
    std::array<int, 5> my_array;

    for(size_t i = 0; i < my_array.size(); i++) {
        my_array[i] = i;
    }

    std::cout << my_array[2] << std::endl;
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
    char* greeting_c = "Hello";
    return 0;
}
```
#### C++20
```cpp
#include <string>

int main() {
    std::string str1 = "Hello";
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
    std::cout << double_number_a(num) << std::endl;
    std::cout << num << std::endl;
    double_number_b(&num);
    std::cout << num << std::endl;
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

int main() {
    for (auto i = 1; i <= 3; i++) {
        std::cout << i << std::endl;
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

int main() {
    auto x = 1;
    while(x <= 3) {
        std::cout << x++ << std::endl;
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
    if (x < 3) goto cleanup;
    // Program code here
cleanup:
    return 0;
}
```
#### C++20
```cpp
#include <iostream>

int main() {
    int x;
    std::cin >> x;
    if (x < 3) goto cleanup;
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
    if (x < 'a') printf("Less than\n"); // x is promoted to int to compare it with the integer value of 'a'.
    else printf("Greater than or equal to\n");
    return 0;
}
```
#### C++20
```cpp
#include <iostream>

int main() {
    auto x = 'A';
    if (x < 'a') std::cout << "Less than" << std::endl; // x is promoted to int to compare it with the integer value of 'a'.
    else std::cout << "Greater than or equal to" << std::endl;
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
        std::cout << argv[i] << std::endl;
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

## Storage Class Specifiers
Define the storage duration of an object.
#### C17
```c
int main() {
    extern int a; // defined elsewhere
    static int b; // hold value between invocations
    register int c; // store in CPU register for fast access
    auto int d; // automatic duration - scope lifetime. Implicit if not specified
    _Thread_local int e; // thread storage duration
    return 0;
}
```
#### C++20
```cpp
int main() {
    extern int a; // defined elsewhere
    register int c; // automatic storage duration. Also hints to the compiler to place the object in the processor's register
    static int b; // hold value between invocations
    thread_local int e; // thread storage duration
    return 0;
}
```

## Type Qualifiers
A way of expressing additional information about a value through the type system to ensure correctness in the use of the data.
#### C17
```c
int main() {
    restrict int* a; // Should only be accessed from this pointer
    const int b; // Once defined, is constant and cannot be changed
    atomic int c; // Can only be modified by one thread at a time
    volatile int d; // Can be modified externally. the program will check x's value before using it, even if it hasn't been modified locally.
    return 0;
}
```
#### C++20
```cpp
#include <atomic>

int main() {
    const int a = 1; // a, once defined, is constant and cannot be changed
    std::atomic<int> b; // b can only be modified by one thread at a time
    volatile int c; // c can be modified externally. the program will check x's value before using it, even if it hasn't been modified locally.
    return 0;
}
```

## Inline Functions
Directly include the given function in the caller code sequence. This ensures that: function call overhead doesn’t occur ; overhead of push/pop variables on the stack is eliminated ; overhead of the return call is eliminated ; context-specific optimizations can be enabled at compile time.
#### C17
```c
#include <stdio.h>

static inline void square(int* x) {
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

inline void square(int& x) {
    x *= x;
    return;
}

int main() {
    int num = 5;
    square(num);
    std::cout << num << std::endl;
    return 0;
}
```
```
output: 25
```

## Conditional If
Responsible for modifying the flow of execution in a program. Always used with a condition, which is evaluated first before executing any statement inside the body.
#### C17
```c
#include <stdio.h>

int main() {
    int x = 4;
    if (!x) printf("x is 0\n"); // one line if statement
    else if (x < 0) printf("x is negative\n");
    else { // or you can use a block            
        printf("x is positive\n");
    }
    return 0;
}
```
#### C++20
```cpp
#include <iostream>

int main() {
    if (int x = 4 ; !x) std::cout << "x is 0" << std::endl; // one line if statement with optional init statement before condition
    else if (x < 0) std::cout << "x is negative" << std::endl;
    else { // or you can use a block
        std::cout << "x is positive" << std::endl;
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

int main() {
    int x = 4;
    x < 0 ? std::cout << "x is negative" << std::endl : std::cout << "x is 0 or positive" << std::endl;
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

int main() {
    int x = 5;
    std::cout << "The address of x is " << &x << std::endl;
    return 0;
}
```
```
output: The address of x is 0x7ffd7b254c2c
```

## Dereference Operator
Use '\*' before a variable name to use the value it points to rather than the address stored.
#### C17
```c
#include <stdio.h>

int main() {
    int x = 4;
    int* y = &x;
    printf("The value stored at x is %d\n", *y);
    return 0;
}
```
#### C++20
```cpp
#include <iostream>

int main() {
    int x = 4;  
    int* y = &x;
    std::cout << "The value stored at x is " << *y << std::endl;
    return 0;
}
```
```
output: The value stored at x is 4
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
    int x[5];
    int* x_ptr = &x[0];
    printf("Value of x_ptr = %p\n", (void*)x_ptr);
    printf("Value of x_ptr + 1 = %p\n", (void*)(x_ptr + 1));
    char y[5];
    char* y_ptr = &y[0];
    printf("Value of y_ptr = %p\n", (void*)y_ptr);
    printf("Value of y_ptr + 1 = %p\n", (void*)(y_ptr + 1));
    return 0;
}
```
#### C++20
```cpp
#include <iostream>

int main() {
    int x[5];
    int* x_ptr = &x[0];
    std::cout << "Value of x_ptr = " << x_ptr << std::endl;
    std::cout << "Value of x_ptr + 1 = " << x_ptr + 1 << std::endl;
    char y[5];
    char* y_ptr = &y[0];
    std::cout << "Value of y_ptr = " << y_ptr << std::endl;
    std::cout << "Value of y_ptr + 1 = " << y_ptr + 1 << std::endl;
    return 0;
}
```
```
Output: Value of x_ptr = 492316
        Value of x_ptr + 1 = 492320
        Value of y_ptr = 492303
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

struct my_struct {
    int x;
    int y;
};

int main() {
    struct my_struct object1;
    object1.x = 1;
    std::cout << object1.x << std::endl;
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
    printf("Size of my_data union: %lu\n", sizeof(object1));
    return 0;
}
```
#### C++20
```cpp
#include <iostream>

union my_data {
    int i;
    float f;
    char str[20];
};

int main() {
    union my_data object1;        
    std::cout << "Size of my_data union: " << sizeof(object1) << std::endl;
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

int main() {
    int x;
    std::cout << "Enter an integer value for x: ";
    std::cin >> x;
    std::cout << "The value at x is now: " << x << std::endl;
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

int main() {
    unsigned char a = 5; // 00000101
    unsigned char b = 9; // 00001001
    std::cout << "a & b = " << (a & b) << std::endl; // 00000001
    std::cout << "a | b = " << (a | b) << std::endl; // 00001101
    std::cout << "a ^ b = " << (a ^ b) << std::endl; // 00001100
    std::cout << "~a = " << (~a) << std::endl; // 11111010
    std::cout << "b << 1 = " << (b << 1) << std::endl; // 00010010
    std::cout << "b >> 1 = " << (b >> 1) << std::endl; // 00000100
    return 0;
}
```
```
output: a & b = 1
        a | b = 13
        a ^ b = 12
        ~a = -6
        b << 1 = 18
        b >> 1 = 4
```

## Typedef
Used to add an additional name to a type. Useful when working with more complex types, making them more human readable.
#### C17
```c
#include <stdio.h>

typedef unsigned char byte;

int main() {
    byte b1 = 'c';
    return 0;
}
```
#### C++20
```cpp
#include <iostream>

typedef unsigned char byte;

int main() {
    byte b1 = 'c';
    return 0;
}
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
    for(int i = mon; i <= sun; i++) {
        printf("%d\n", i); 
    } 
    return 0;
}
```
#### C++20
```cpp
#include <iostream>

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
    for(int i = mon; i <= sun; i++) {
        std::cout << i << std::endl; 
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
    printf("Sum of the array: %d\n", sum_of_numbers);
    return 0;
}
```
#### C++20
```cpp
#include <iostream>
#include <cstdarg>

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
    std::cout << "Sum of the array: " << sum_of_numbers << std::endl;
    return 0;
}
```
```
output: Sum of the array: 30
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

void thread_func() {
    std::cout << "Printing from Thread" << std::endl;
    return NULL;
}

int main() {
    std::thread thread_obj(thread_func);
    thread_obj.join();
    std::cout << "Thread returned" << std::endl;
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

typedef struct data {
    std::mutex mtx;
    int x;
} data;

void thread_func(data* d) { 
    d->mtx.lock()
    d->x = 2;   
    d->mtx.unlock()
    return;
} 
   
int main() {
    data d;
    std::thread thread_obj(thread_func, &d); 
    thread_obj.join();  // Wait for thread to return before continuing execution
    std::cout << "x has safely been modified to " << d.x << std::endl; 
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
    if (x) { // test that the memory was allocated before you use it
        free(x); // you must manually free any memory you allocated on the heap or it will persist (memory leak)
    }
    return 0;
}
```
#### C++20
```cpp
#include <iostream>

int main() {
    int* p  = new int; // pointer to a heap-reserved integer
    delete p; // you must manually free any memory you allocated on the heap or it will persist (memory leak)
    return 0;
}
```

## Assertions
Statements used to explicitly test assumptions made by the programmer. Will be checked at runtime, or if static at compile time. Typically used for unit testing.
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

int main() {
    int x = 1;
    x += 1;
    std::cout << "x = " << x << std::endl;
    return 0;
}
```
```
output: x = 2
```

## Project Structure
It's useful to follow a conventional and sensible structure when organizing a project, to maintain readability. Below is a suggestion as to how you might organize your project.
#### C17
```
doc/                   Only for software user guide
src/                   Only for code: .c and .h files. May also contain a contrib/ directory.
test/                  Only for integration and unit tests
Makefile               Makefile
Style.md               C style guide
_opt/                  Everything else that is not required to build/test. Developer notes, scripts, linters, ci stuff, analysis tools etc.
```
#### C++20
```
doc/                   Only for software user guide
src/                   Only for code: .cpp and .h files. May also contain a contrib/ directory.
test/                  Only for integration and unit tests
Makefile               Makefile
Style.md               C++ style guide
_opt/                  Everything else that is not required to build/test. Developer notes, scripts, linters, ci stuff, analysis tools etc.
```

## Includes
Includes are instructions to the preprocessor to include external code. External code is made up of at least a header file (interface) and a source file (implementation).

When compiling your program, **#include** the header, and link the source file at compile time.
#### C17
In file src/main.c
```c
#include <stdio.h> // Include a dependency from the system library
#include "../include/file.h" // Include a local dependency from a relative path

int main() {
    // Use file.h
}
```
In file include/file.c:
```c
#include <stdio.h> // Include a dependency from the system library
#include "file.h" // Include a local dependency from a relative path
```
In file include/file.h:
```c
#ifndef PROG_H // Only process the below if it hasn't already been processed in the current compilation.
#define PROG_H

// File contents here

#endif
```
#### C++20
In file src/main.cpp
```c
#include <iostream> // Include a dependency from the system library
#include "../include/file.hpp" // Include a local dependency from a relative path

int main() {
    // Use file.hpp
}
```
In file include/file.cpp:
```cpp
#include <iostream> // Include a dependency from the system library
#include "file.hpp" // Include a local dependency from a relative path
```
In file include/file.hpp:
```cpp
#ifndef PROG_HPP // Only process the below if it hasn't already been processed in the current compilation.
#define PROG_HPP

// File contents here

#endif
```

## Compilation
Compiling source code turns it into machine language through preprocessing, compiling, assembly and linking.

#### C17
```
gcc -c -std=c17 src/main.c -o obj/main.o // Compile main.c to object
gcc -c -std=c17 include/file.c -o obj/file.o // Compile file.c to object
gcc obj/main.o obj/file.o -o bin/prog // Link objects and create executable bin/prog
```
#### C++20
```
g++ -c -std=c++20 src/main.cpp -o obj/main.o // Compile main.cpp to object
g++ -c -std=c++20 include/file.cpp -o obj/file.o // Compile file.cpp to object
g++ obj/main.o obj/file.o -o bin/prog // Link objects and create executable bin/prog
```

# C++ Only

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

int main() {
    std::cout << Bar::f() << std::endl;
    return 0;
}
```
```
output: 10
```

## Pass by Reference
Use the **&** symbol as an alternative to passing an address by pointer or passing by value.
#### C++20
```cpp
#include <iostream>

void square(int& x) {
    x *= x;
    return;
}

int main() {
    int x = 2;
    square(x);
    std::cout << x << std::endl;
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
#include <vector>
 
int main() {
    std::vector<int> v = {0, 1, 2, 3};
    for(const int& i : v) { // access using const reference
        std::cout << i << std::endl;
    }
    int a[] = {4, 5, 6, 7};
    for(auto n : a) { // the initializer can be an array
        std::cout << n << std::endl;
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
        7
```

## Namespaces
A declarative region that provides a named scope to its constituent identifiers. Useful for organizing and reducing ambiguity in code. The scope resolution operator **::** is used to access a scope's contents.
#### C++20
```cpp
#include <iostream>

namespace ns_1 {
    void func() {
        std::cout << "Called from ns_1" << std::endl;
    }
}

namespace ns_2 {
    void func() {
        std::cout << "Called from ns_2" << std::endl;
    }
}

int main () {
    ns_1::func();
    ns_2::func(); 
    return 0;
}
```
```
output: Called from ns_1
        Called from ns_2
```

## Classes
A user-defined data structure template declared with keyword **class** containing member functions and data.
#### C++20
```cpp
#include <iostream>

class human {
public:
    int height;
    int weight;
};

int main() {
    human john;
    john.height = 180;
    john.weight = 220;
    return 0;
}
```

## Class Methods
Functions of a class.
#### C++20
```cpp
#include <iostream>

class human {
public:
    int height;
    int weight;
    int get_height() const {
        return height;
    }
    int get_weight() const {
        return weight;
    }
};

int main() {
    human john;
    john.height = 180;
    john.weight = 220;
    std::cout << john.get_height() << std::endl;
    std::cout << john.get_weight() << std::endl;
    return 0;
}
```
```
output: 180
        220
```

## Constructors & Destructors
A constructor is an optional special member function of a class used to instantiate the class object. It must take the same name as the class, with no return type. A destructor is an optional special member function of a class called in the destruction of a class object. It must take the same name as the class, preceded with **~**, and with no return type.
#### C++20
```cpp
#include <iostream>

class human {
public:
    int height;
    int weight;
    human(int h, int w) {
        height = h;
        weight = w;
    }
    ~human(){};
    int get_height() const {
        return height;
    }
    int get_weight() const {
        return weight;
    }
};

int main() {
    human john(180, 220);
    std::cout << john.get_height() << std::endl;
    std::cout << john.get_weight() << std::endl;
    return 0;
}
```
```
output: 180
        220
```

## Encapsulation
Fundamental OOP concept used to group together data and functions, and provide varying levels of abstraction from the user.
#### C++20
```cpp
#include <iostream>

class human {
private: // abstracted from the user
    int height;
    int weight;
public: 
    human(int h, int w) {
        height = h;
        weight = w;
    }
    int get_height() const {
        return height;
    }
    int get_weight() const {
        return weight;
    }
};

int main() {
    human john(180, 220);
    std::cout << john.get_height() << std::endl;
    std::cout << john.get_weight() << std::endl;
    return 0;
}
```
```
output: 180
        220
```

## Inheritance
Fundamental OOP concept. The capability of a class to derive properties and characteristics from another class.
#### C++20
```cpp
#include <iostream>

class human {
public:
    int height;
    int weight;
public: 
    human(int h, int w) {
        height = h;
        weight = w;
    }
    int get_height() const {
        return height;
    }
    int get_weight() const {
        return weight;
    }
};

class adult : public human { // inherit from human class
public:
    adult(int h, int w) : human(h, w) {} // call the base class constructor from this constructor
    std::string occupation;
    std::string get_occupation() const {
        return occupation;
    }   
};

int main() {
    adult john(180, 220);
    john.occupation = "lawyer";
    std::cout << john.get_height() << std::endl;
    std::cout << john.get_weight() << std::endl;
    std::cout << john.get_occupation() << std::endl;
    return 0;
}
```
```
output: 180
        220
        lawyer
```

## Polymorphism
Fundamental OOP concept. Allows operations or objects to behave differently in different contexts.
### Function Overloading
Used to facilitate compile-time polymorphism by allowing creation of more than one function with the same name but with different parameters.
#### C++20
```cpp
#include <iostream>

class human {
public:
    int height;
    float weight;
    human(int h, int w) {
        height = h;
        weight = w;
    }
};

int print(int x) {
    std::cout << x << std::endl;
}

int print(float x) {
    std::cout << x  << std::endl;
}

int main() {
    human john(180, 220);
    print(john.height);
    print(john.weight);
    return 0;
}
```
```
output: 180
        220
```

### Virtual Functions
Used to facilitate runtime polymorphism by allowing redefinition of a base class function.
#### C++20
```cpp
#include <iostream>

class human {
public:
    int height;
    int weight;
public: 
    human(int h, int w) {
        height = h;
        weight = w;
    }
    int get_height() const {
        return height;
    }
    int get_weight() const {
        return weight;
    }
    virtual void print_all() = 0; // ()=0 creates a _pure_ virtual function that must be overridden. Alternatively you can just write a default function as a virtual function with no requirement to be overwritten.
};

class adult : public human { // inherit from human class
public:
    adult(int h, int w) : human(h, w) {}
    std::string occupation;
    std::string get_occupation() const {
        return occupation;
    }   
    void print_all() { // virtual function overridden in derived class
        std::cout << height << std::endl;
        std::cout << weight << std::endl;
        std::cout << occupation << std::endl;
    }
};

int main() {
    adult john(180, 220);
    john.occupation = "lawyer";
    john.print_all();
    return 0;
}
```
```
output: 180
        220
        lawyer
```

## Friend Functions
A function of a class defined outside of its scope but with the right to access all private and protected members of the class.
#### C++20
```cpp
#include <iostream>

class human {
private:
    int weight;
public:
    human(int w) {
        weight = w;     
    }
    friend int get_weight(human h);
};

int get_weight(human h) {
    return h.weight; // we can access the private members of the associated class thanks to the friend function
}

int main() {
    human john(220);
    std::cout << get_weight(john) << std::endl;
    return 0;
}
```
```
output: 220
```

## Templates
A blueprint for creating a generic class or function. The foundation of generic programming, which involves writing code in a way that is independent of any particular type.
#### C++20
```cpp
#include <iostream>

template <class T>
T largest(T n1, T n1) {
    return (n1 > n2) ? n1 : n2;
}

int main() {
    int x, y;
    std::cout << "Enter two integers: " << std::endl;
    std::cin >> x >> y;
    std::cout << largest(x, y) << std::endl;
    return 0;
}
```
```
input:  2
        5
output: 5
```

## Structured Bindings
A convenient way to declare multiple variables initialized from a tuple, pair or struct. Often used to capture multiple return values from a function.
#### C++20
```cpp
#include <iostream>
  
struct Point {
    int x;
    int y;
};
  
int main() {
    Point p = {1, 2};
    auto[x, y] = p; // Creates and initializes x and y variables
    std::cout << x << std::endl;
    std::cout << y << std::endl;     
    return 0;
}
```
```
output: 1
        2
```

## Lambda Expressions
Also referred to as Lambda Functions. A simplified notation for defining and using an anonymous function object, capable of capturing variables in scope.
#### C++20
```cpp
#include <iostream>

int main() {
    int x = 1;
    auto multiply = [&x](int y)->int{ // Anonymous function takes a reference to x. Returns an int
        return x*y;
    };
    std::cout << multiply(5) << std::endl;
    x = 2;
    std::cout << multiply(5) << std::endl;
    return 0;
}
```
```
output: 5
        10
```

## Exception Handling
A mechanism to handle runtime errors by transferring control from one part of a program to another.
#### C++20
```cpp
#include <iostream>

double divide(double dividend, double divisor) {
    if (divisor == 0) {
            throw "Cannot divide by 0\n"; // If divisor is 0, throw this error
    }
    return dividend / divisor;
}

int main() {
    try {
        std::cout << divide(10, 0) << std::endl;

    } catch (const char *err) {
        std::cout << err << std::endl;
    }
    return 0;
}
```
```
output: Cannot divide by 0
```

# Programs

## Linked List
#### C17
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

void push_front(struct Node** headRef, int data) {
    struct Node* newNode = createNode(data);
    newNode->next = *headRef;
    *headRef = newNode;
}

void push_back(struct Node** headRef, int data) {
    struct Node* newNode = createNode(data);
    newNode->next = NULL;

    if (*headRef == NULL) {
        *headRef = newNode;
        return;
    }

    struct Node* curr = *headRef;
    while (curr->next != NULL) {
        curr = curr->next;
    }
    curr->next = newNode;
}

void printList(struct Node* head) {
    struct Node* curr = head;
    while (curr != NULL) {
        printf("%d -> ", curr->data);
        curr = curr->next;
    }
    printf("NULL\n");
}

int main() {
    struct Node* head = NULL;

    push_back(&head, 1);
    push_back(&head, 2);
    push_back(&head, 3);
    push_back(&head, 4);

    push_front(&head, 5);

    printList(head);

    return 0;
}

```
#### C++20
```cpp
#include <iostream>
#include <list>

int main() {
    std::list<int> myList;

    myList.push_back(1);
    myList.push_back(2);
    myList.push_back(3);
    myList.push_back(4);

    myList.push_front(5);

    for (auto it = myList.begin(); it != myList.end(); ++it) {
        std::cout << *it << " -> ";
    }
    std::cout << "NULL" << std::endl;

    return 0;
}
```
```
output: 5 -> 1 -> 2 -> 3 -> 4 -> NULL
```

## Binary Search Tree
#### C17
```c
#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int data;
    struct Node *left;
    struct Node *right;
} Node;

Node* create_node(int data) {
    Node* node = (Node*) malloc(sizeof(Node));
    node->data = data;
    node->left = NULL;
    node->right = NULL;
    return node;
}

Node* insert_node(Node* node, int data) {
    if (node == NULL) {
        return create_node(data);
    } else if (data < node->data) {
        node->left = insert_node(node->left, data);
    } else if (data > node->data) {
        node->right = insert_node(node->right, data);
    }
    return node;
}

void inorder_traversal(Node* node) {
    if (node != NULL) {
        inorder_traversal(node->left);
        printf("%d ", node->data);
        inorder_traversal(node->right);
    }
}

int main() {
    Node* root = NULL;
    root = insert_node(root, 50);
    insert_node(root, 30);
    insert_node(root, 20);
    insert_node(root, 40);
    insert_node(root, 60);
    insert_node(root, 10);

    inorder_traversal(root);

    return 0;
}
```
#### C++20
```cpp
#include <iostream>
#include <memory>

struct Node {
    int data;
    std::unique_ptr<Node> left, right;

    Node(int value) : data(value) {}
};

class BinarySearchTree {
public:
    BinarySearchTree() = default;

    std::unique_ptr<Node> insert_node(std::unique_ptr<Node> node, int value) {
        if (!node) {
            return std::make_unique<Node>(value);
        }
        if (value < node->data) {
            node->left = insert_node(std::move(node->left), value);
        } else if (value > node->data) {
            node->right = insert_node(std::move(node->right), value);
        }
        return node;
    }

    void inorder_traversal(Node* node) {
        if (node) {
            inorder_traversal(node->left.get());
            std::cout << node->data << " ";
            inorder_traversal(node->right.get());
        }
    }

    std::unique_ptr<Node> root = nullptr;
};

int main() {
    BinarySearchTree bst;
    bst.root = bst.insert_node(std::move(bst.root), 50);
    bst.root = bst.insert_node(std::move(bst.root), 30);
    bst.root = bst.insert_node(std::move(bst.root), 20);
    bst.root = bst.insert_node(std::move(bst.root), 40);
    bst.root = bst.insert_node(std::move(bst.root), 60);
    bst.root = bst.insert_node(std::move(bst.root), 10);

    bst.inorder_traversal(bst.root.get());
    std::cout << std::endl;

    return 0;
}
```
```
output: 10 20 30 40 50 60
```

## Copy a File
Copy a file from source to destination. Note that memory-mapped I/O can be more efficient for large files, but it requires more advanced knowledge of the operating system and may not be available on all platforms.
#### C17
```c
#include <stdio.h>

int main() {
    FILE *source_file, *destination_file;
    char buffer[4096];
    size_t bytes_read;

    source_file = fopen("source.txt", "rb");
    destination_file = fopen("destination.txt", "wb");

    if (source_file == NULL || destination_file == NULL) {
        printf("Error opening files.\n");
        return 1;
    }

    while ((bytes_read = fread(buffer, 1, sizeof(buffer), source_file)) > 0) {
        fwrite(buffer, 1, bytes_read, destination_file);
    }

    fclose(source_file);
    fclose(destination_file);

    return 0;
}
```
#### C++20
```cpp
#include <fstream>
#include <iostream>

int main() {
    const std::string source = "source.txt";
    const std::string destination = "destination.txt";

    std::ifstream input(source, std::ios::binary);
    std::ofstream output(destination, std::ios::binary);

    if (!input.is_open()) {
        std::cerr << "Failed to open source file.\n";
        return 1;
    }

    if (!output.is_open()) {
        std::cerr << "Failed to open destination file.\n";
        return 1;
    }

    output << input.rdbuf();

    input.close();
    output.close();

    return 0;
}
```
```
output: 
```

## Multithreaded Queue
#### C17
```c
#include <stdio.h>
#include <stdlib.h>
#include <threads.h>

#define BUFFER_SIZE 4 

int buffer[BUFFER_SIZE];
int count = 0;
mtx_t mutex;
cnd_t cv;

int producer(void *arg) {
    int i;
    for (i = 0; i < BUFFER_SIZE; i++) {
        mtx_lock(&mutex);
        while (count == BUFFER_SIZE) {
            cnd_wait(&cv, &mutex);
        }
        buffer[count] = i;
        count++;
        cnd_signal(&cv);
        mtx_unlock(&mutex);
    }
    return 0;
}

int consumer(void *arg) {
    while (1) {
        mtx_lock(&mutex);
        while (count == 0) {
            cnd_wait(&cv, &mutex);
        }
        int message = buffer[count - 1];
        count--;
        cnd_signal(&cv);
        mtx_unlock(&mutex);

        printf("Received message: %d\n", message);
    }
}

int main() {
    mtx_init(&mutex, mtx_plain);
    cnd_init(&cv);

    thrd_t producer_thread, consumer_thread;

    thrd_create(&producer_thread, producer, NULL);
    thrd_create(&consumer_thread, consumer, NULL);

    thrd_join(producer_thread, NULL);
    thrd_join(consumer_thread, NULL);

    mtx_destroy(&mutex);
    cnd_destroy(&cv);

    return 0;
}

```
#### C++20
```cpp
#include <iostream>
#include <queue>
#include <thread>
#include <mutex>
#include <condition_variable>

std::mutex mutex;
std::queue<int> message_queue;
std::condition_variable cv;

void producer() {
    for (int i = 0; i < 4; i++) {
        std::lock_guard<std::mutex> lock(mutex);
        message_queue.push(i);
        cv.notify_one();
    }
}

void consumer() {
    while (true) {
        std::unique_lock<std::mutex> lock(mutex);
        cv.wait(lock, []{ return !message_queue.empty(); });
        int message = message_queue.front();
        message_queue.pop();
        lock.unlock();

        std::cout << "Received message: " << message << std::endl;
    }
}

int main() {
    std::thread producer_thread(producer);
    std::thread consumer_thread(consumer);

    producer_thread.join();
    consumer_thread.join();

    return 0;
}
```
```
output: Received message: 0
        Received message: 1
        Received message: 2
        Received message: 3
```

Copyright &copy; 2024 Sean Valeo | [Source](https://github.com/seanvaleo/cbyexample "Source") | [Contributors](https://github.com/seanvaleo/cbyexample.com/graphs/contributors "Contributors") | [Donate](https://github.com/sponsors/seanvaleo)
