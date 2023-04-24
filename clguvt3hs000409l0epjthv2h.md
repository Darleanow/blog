---
title: "Operators in C++"
seoTitle: "C++ operators"
datePublished: Mon Apr 24 2023 13:36:14 GMT+0000 (Coordinated Universal Time)
cuid: clguvt3hs000409l0epjthv2h
slug: operators-in-cpp
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682342928919/ec5b1ce0-62de-4f2f-8958-7e45c8756cc6.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682343323533/36e3d781-96fe-4a21-afca-19fd98ca521f.jpeg
tags: programming-blogs, operators, cpp-ck4ra5k7300nlv2s1jbkdp2qh

---

Operators in C++ are symbols that perform specific operations on operands, such as arithmetic, comparison, and logical operations. They enable you to manipulate data and create complex expressions. In this article, we will explore the different types of operators in C++ and how they are used in practice.

## Arithmetic operators

Arithmetic operators perform basic mathematical operations on numeric values:

* Addition (+): Adds two numbers.
    
* Subtraction (-): Subtracts the second number from the first.
    
* Multiplication (\*): Multiplies two numbers.
    
* Division (/): Divides the first number by the second.
    
* Modulus (%): Returns the remainder after dividing the first number by the second.
    

Example:

```cpp
int a = 10, b = 3;
int sum = a + b; // 13
int difference = a - b; // 7
int product = a * b; // 30
int quotient = a / b; // 3
int remainder = a % b; // 1
```

## Comparison operators

Comparison operators are used to compare two values and return a boolean result:

* Equal to (==): Returns true if the two values are equal.
    
* Not equal to (!=): Returns true if the two values are not equal.
    
* Greater than (&gt;): Returns true if the first value is greater than the second.
    
* Less than (&lt;): Returns true if the first value is less than the second.
    
* Greater than or equal to (&gt;=): Returns true if the first value is greater than or equal to the second.
    
* Less than or equal to (&lt;=): Returns true if the first value is less than or equal to the second.
    

Example:

```cpp
int x = 5, y = 10;
bool isEqual = x == y; // false
bool isNotEqual = x != y; // true
bool isGreater = x > y; // false
bool isLess = x < y; // true
bool isGreaterOrEqual = x >= y; // false
bool isLessOrEqual = x <= y; // true
```

## Logical operators

Logical operators are used to combine boolean expressions:

* Logical AND (&&): Returns true if both expressions are true.
    
* Logical OR (||): Returns true if at least one of the expressions is true.
    
* Logical NOT (!): Returns true if the expression is false, and vice versa.
    

Example:

```cpp
bool a = true, b = false;
bool andResult = a && b; // false
bool orResult = a || b; // true
bool notResult = !a; // false
```

## Other operators

C++ supports several other operators, such as:

* Assignment operators: Assign values to variables and can be combined with arithmetic operators (+=, -=, \*=, /=, %=).
    
* Increment and decrement operators: Increase or decrease a variable's value by 1 (++ or --).
    
* Bitwise operators: Perform operations on individual bits of integer values (&, |, ^, ~, &lt;&lt;, &gt;&gt;).
    
* Ternary conditional operator: Shortens an if-else statement (condition ? true\_expression : false\_expression).
    

Example:

```cpp
int a = 4;
a *= 2; // 8
a++; //9

int c = 12, d = 25;
int e = c & d; //8

c < d ? std::cout << "C is less than D" : std::cout << "C is more than D";
```

## Conclusion

Operators in C++ enable you to perform various operations on data and create complex expressions. In this article, we covered arithmetic, comparison, logical, and other operators, along with examples of their usage. Understanding and using operators effectively is crucial for writing efficient and concise C++ code. In future articles, we will dive deeper into more advanced topics, such as control structures, functions, and object-oriented programming.