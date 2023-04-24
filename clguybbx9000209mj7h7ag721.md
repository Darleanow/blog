---
title: "Arrays, Structs, and Unions in C++"
datePublished: Mon Apr 24 2023 14:46:24 GMT+0000 (Coordinated Universal Time)
cuid: clguybbx9000209mj7h7ag721
slug: arrays-structs-and-unions-in-cpp
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682347410609/65d12130-ccd0-472f-8a46-dcfadf37efab.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682347564989/ba4ce731-5b35-44b0-8676-37fd60a713c0.jpeg
tags: programming-blogs, arrays, cpp-ck4ra5k7300nlv2s1jbkdp2qh, structs, unions

---

Arrays, structs, and unions are fundamental data structures in C++ that allow you to organize and manage data more efficiently. These data structures help you group related data together and make it easier to work with complex data types. In this article, we will cover the basics of arrays, structs, and unions in C++.

## Arrays

An array is a collection of elements of the same type, stored in contiguous memory locations. Arrays are fixed in size, and you need to specify the number of elements when you declare an array. You can access individual elements of an array using their index, starting from 0.

```cpp
#include <iostream>

int main() {
    int numbers[5] = {1, 2, 3, 4, 5};

    for (int i = 0; i < 5; ++i) {
        std::cout << "Element " << i << " = " << numbers[i] << std::endl;
    }
}
```

## Structs

A struct (short for structure) is a user-defined data type that groups variables of different data types under a single name. Structs allow you to create more complex data types and keep related data together.

```cpp
#include <iostream>
#include <string>

struct Student {
    std::string name;
    int age;
    double gpa;
};

int main() {
    Student s1 = {"Alice", 20, 3.8};

    std::cout << "Name: " << s1.name << std::endl
              << "Age: " << s1.age << std::endl
              << "GPA: " << s1.gpa << std::endl;
}
```

## Unions

Unions are similar to structs but have a key difference: all union members share the same memory location. This means that a union can hold only one of its members at a time. Unions are useful when you need to store different types of data in the same variable but not at the same time.

```cpp
#include <iostream>

union Data {
    int i;
    float f;
    char c;
};

int main() {
    Data d;
    d.i = 42;
    std::cout << "Integer: " << d.i << std::endl;

    d.f = 3.14f;
    std::cout << "Float: " << d.f << std::endl; // The value of d.i is now undefined

    d.c = 'A';
    std::cout << "Char: " << d.c << std::endl; // The values of d.i and d.f are now undefined
}
```

## Conclusion

Arrays, structs, and unions are essential data structures in C++ that help you organize and manage data more efficiently. Arrays allow you to store multiple elements of the same type, while structs and unions enable you to create more complex data types by grouping variables of different types. Understanding and using these data structures effectively is vital for writing well-structured and maintainable C++ code. In future articles, we will explore more advanced topics related to arrays, such as multi-dimensional arrays, dynamic memory allocation, and array-based algorithms.