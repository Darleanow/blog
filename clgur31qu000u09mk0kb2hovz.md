---
title: "Introduction to basic syntax in C++"
seoTitle: "C++ basics"
datePublished: Mon Apr 24 2023 11:24:00 GMT+0000 (Coordinated Universal Time)
cuid: clgur31qu000u09mk0kb2hovz
slug: introduction-to-basic-syntax-in-c
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682335645160/d2dd8de3-e8c6-4a91-950c-c97b8bec1878.jpeg
tags: cpp, programming-blogs, intro-to-programming

---

## Structure of a C++ program

Every C++ program consists of the following components:

* Header files: These contain declarations of functions, variables, and constants that are used in the program. To include a header file, use the #include preprocessor directive, followed by the name of the header file enclosed in angle brackets (&lt;&gt;) or quotes ("").
    
    Note: Quotes are used for the headers you create, for STL (Standard Library), you should always use brackets.
    
    ```cpp
    #include <iostream>
    #include "my_header_file.h"
    ```
    
* Main function: The main function is the entry point of a C++ program. The operating system calls this function when the program starts. The main function has the following signature:
    
    ```cpp
    int main() {
        // Your code goes here
        return 0;
    }
    ```
    
* Statements: C++ programs consist of a sequence of statements that are executed in order. Statements are typically terminated with a semicolon (;).
    

## Variable declarations

In C++, variables must be declared before they can be used. A variable declaration includes the data type, variable name, and an optional initializer. For example:

```cpp
int x; // Declare an integer variable named x
float y = 3.14; // Declare a float variable named y and initialize it with the value 3.14
```

There are also many other types like:

* Double (a float with twice the byte size (8).)
    
* Char
    
* Wchar\_t (Wide char, holds 2 bytes instead of one.)
    
* Boolean
    
* Void
    

There are also many type modifiers (signed, unsigned, etc...) that we will see later on.

## Conditional statements

Conditional statements allow you to execute different parts of your code based on certain conditions. The most common conditional statements are if, if-else, and switch. Here's an example of an if-else statement:

```cpp
int age = 18;

if (age >= 18) {
    std::cout << "You are an adult." << std::endl;
} else {
    std::cout << "You are a minor." << std::endl;
}
```

Note that you can also use switch for conditions by using the following syntax:

```cpp
int age = 18;

switch(age){
    case (18):
        std::cout << "You are an adult." << std::endl;
        break;
    case (15):
        std::cout << "You are a minor." << std::endl;
        break;
    default:
        std::cout << "I don't know this number." << std::endl;
        break;
}
```

For the switch, only recognized cases will be handled, the default case is for unhandled cases.

## Loops

Loops are used to execute a block of code repeatedly until a specified condition is met. C++ supports three types of loops: for, while, and do-while. Here's an example of a for loop:

```cpp
for (int i = 0; i < 10; i++) {
    std::cout << "i is " << i << std::endl;
}
```

In C++11, a new type of loop was introduced, the range-based loop that is suited to view the contents of an array or a vector for example:

```cpp
#include <vector> //This statement is needed to use vector

std::vector<int> numbers = { 1, 2, 3, 4, 5 };
for (int number : numbers) {
    std::cout << "Number is " << number << std::endl;
}
```

## Conclusion

Understanding the basic syntax of C++ is the first step in learning the language. In this article, we covered the structure of a C++ program, variable declarations, conditional statements, and loops. In future articles, we will dive deeper into other important concepts like functions, pointers, and object-oriented programming.