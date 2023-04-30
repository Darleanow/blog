---
title: "Exception Handling in C++: Try, Catch, and Throw"
seoTitle: "Exception handling in C++"
datePublished: Sun Apr 30 2023 22:00:39 GMT+0000 (Coordinated Universal Time)
cuid: clh3ygw1l03cfltnvekqtf6xr
slug: exception-handling-in-c-try-catch-and-throw
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682357741786/341010c5-15a8-4bc2-b0ea-175bf176fd35.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682357986166/7d84d165-21c7-4e0c-9c6f-60b03d7e2130.jpeg
tags: programming-blogs, cpp-ck4ra5k7300nlv2s1jbkdp2qh, exceptionhandling

---

Exception handling is an important aspect of C++ programming, as it allows you to handle errors and exceptional situations gracefully. In this article, we will discuss the basics of exception handling in C++, including the use of try, catch, and throw statements.

## Exception handling basics

In C++, exception handling is achieved using three main keywords: try, catch, and throw. These keywords allow you to define blocks of code that might raise exceptions and specify how to handle these exceptions.

* try: Encloses a block of code that might throw an exception.
    
* catch: Defines a block of code that will handle a specific type of exception.
    
* throw: Used to raise an exception, which can be caught by a catch block.
    

## Using Try and Catch blocks

When using try and catch blocks, you enclose the code that might raise an exception within a try block. Then, you define one or more catch blocks to handle specific types of exceptions.

```cpp
#include <iostream>

int main() {
    try {
        int numerator = 10;
        int denominator = 0;
        if (denominator == 0) {
            throw "Division by zero!";
        }
        int result = numerator / denominator;
        std::cout << "The result is: " << result << std::endl;
    } catch (const char* e) {
        std::cerr << "Error: " << e << std::endl;
    }
}
```

In this example, if the denominator is zero, a custom exception is thrown (a string in this case). The catch block catches the exception and prints an error message to the standard error stream.

## Handling multiple exception types

You can handle multiple exception types by defining multiple catch blocks. Each catch block should handle a specific type of exception.

```cpp
#include <iostream>
#include <stdexcept>

double divide(double a, double b) {
    if (b == 0) {
        throw std::runtime_error("Division by zero!");
    }
    return a / b;
}

int main() {
    try {
        double result = divide(10, 0);
        std::cout << "The result is: " << result << std::endl;
    } catch (const std::runtime_error& e) {
        std::cerr << "Error: " << e.what() << std::endl;
    } catch (...) {
        std::cerr << "An unknown error occurred." << std::endl;
    }
}
```

In this example, we catch a `std::runtime_error` and a catch-all block for any other exception type.

## Custom exception classes

You can create custom exception classes by inheriting from the standard exception classes, such as `std::exception`. This allows you to add custom behavior or additional information to your exceptions.

```cpp
#include <iostream>
#include <stdexcept>

class DivisionByZeroError : public std::runtime_error {
public:
    DivisionByZeroError() : std::runtime_error("Division by zero!") {}
};

double divide(double a, double b) {
    if (b == 0) {
        throw DivisionByZeroError();
    }
    return a / b;
}

int main() {
    try {
        double result = divide(10, 0);
        std::cout << "The result is: " << result << std::endl;
    } catch (const DivisionByZeroError& e) {
        std::cerr << "Error: " << e.what() << std::endl;
    }
}
```

## Conclusion

Exception handling is a crucial aspect of C++ programming, allowing you to handle errors and exceptional situations gracefully. In this article, we covered the basics of exception handling in C++, including the use of try, catch, and throw statements. We also discussed handling multiple exception types, creating custom exception classes, and inheriting from standard exception classes. By understanding and effectively using exception handling, you can improve the robustness and maintainability of your C++ programs. In future articles, we will explore more advanced topics related to exception handling and other important aspects of C++ programming like namespaces, I/O handling, concurrency...