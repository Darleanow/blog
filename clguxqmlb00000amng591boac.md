---
title: "Object-Oriented Programming (OOP) in C++"
seoTitle: "Object Oriented Programming in C++"
datePublished: Mon Apr 24 2023 14:30:18 GMT+0000 (Coordinated Universal Time)
cuid: clguxqmlb00000amng591boac
slug: object-oriented-programming-in-cpp
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682346422612/c3fe10ed-b1cd-44e3-a5a9-ad33eed45221.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682346599661/db1de7a1-a188-49d8-ad3c-c62ef7d4cc13.jpeg
tags: programming-blogs, object-oriented-programming, cpp-ck4ra5k7300nlv2s1jbkdp2qh

---

C++ supports object-oriented programming (OOP), which revolves around the concepts of classes, objects, inheritance, polymorphism, and encapsulation. In this article, we will introduce these OOP concepts and explain their importance in C++ programming.

## Classes and objects

Classes define the structure and behavior of objects, while objects are instances of classes. They encapsulate data and the methods that operate on that data. To create a class, use the 'class' keyword followed by the class name and its members enclosed in curly braces.

```cpp
class MyClass {
public:
    int x;
    void printX() {
        cout << x << endl;
    }
};
```

To create an object, use the class name followed by the object name.

```cpp
MyClass obj;
obj.x = 42;
obj.printX(); // Outputs 42
```

## Inheritance

Inheritance allows one class to inherit the properties and methods of another, promoting code reuse and modularity. To derive a class from another, use the colon (:) followed by the access specifier and the base class name.

```cpp
class Base {
public:
    int a;
};

class Derived : public Base {
public:
    int b;
};
```

### Polymorphism

Polymorphism allows a single interface to represent different types or classes, enabling more flexible and maintainable code. In C++, polymorphism is achieved using virtual functions and pointers or references to base class objects.

```cpp
class Shape {
public:
    virtual double area() = 0; // Pure virtual function
};

class Circle : public Shape {
public:
    double radius;
    double area() override {
        return 3.14159 * radius * radius;
    }
};

class Rectangle : public Shape {
public:
    double width, height;
    double area() override {
        return width * height;
    }
};
```

## Encapsulation

Encapsulation is the practice of bundling related data and methods within an object, hiding internal implementation details from the outside world. Encapsulation is achieved in C++ using access specifiers: public, private, and protected.

```cpp
class Encapsulated {
private:
    int secret;

public:
    void setSecret(int value) {
        secret = value;
    }

    int getSecret() {
        return secret;
    }
};
```

## Conclusion

Object-oriented programming in C++ allows for more organized, maintainable, and reusable code. This article introduced the key concepts of OOP, including classes and objects, inheritance, polymorphism, and encapsulation. As you continue learning C++, you will explore more advanced topics related to these concepts, such as multiple inheritance, abstract classes, and interfaces.