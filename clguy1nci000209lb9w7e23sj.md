---
title: "Exploring Templates in C++"
seoTitle: "C++ templates overview"
datePublished: Mon Apr 24 2023 14:38:52 GMT+0000 (Coordinated Universal Time)
cuid: clguy1nci000209lb9w7e23sj
slug: exploring-templates-in-c
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682346717936/1b05b39b-f995-4d9b-953d-2b6bf0b5e63b.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682347116341/7c5c4ce8-a77d-42ff-aef9-57f89fa86d3c.jpeg
tags: templates, programming-blogs, cpp-ck4ra5k7300nlv2s1jbkdp2qh

---

Templates are a powerful feature of C++ that allows for generic programming. They enable the creation of reusable code that can work with different data types without the need for duplication or typecasting. In this article, we will discuss the basics of templates, including function templates and class templates.

## Function templates in C++

Function templates are used to create generic functions that can work with different data types. To create a function template, use the 'template' keyword followed by angle brackets (&lt;&gt;) containing the template parameter(s).

```cpp
template <typename T>
T add(T a, T b) {
    return a + b;
}
```

You can then call the function with various data types:

```cpp
int main() {
    int i1 = 3, i2 = 5;
    double d1 = 3.5, d2 = 5.2;

    std::cout << add(i1, i2) << endl; // Calls the 'add' function for integers
    std::cout << add(d1, d2) << endl; // Calls the 'add' function for doubles
}
```

## Class templates

Class templates allow you to create generic classes that can work with different data types. To create a class template, use the 'template' keyword followed by angle brackets (&lt;&gt;) containing the template parameter(s), and then define the class.

```cpp
template <typename T>
class Pair {
public:
    T first, second;

    Pair(T a, T b) : first(a), second(b) {}
};
```

To create an instance of a class template, specify the data type within angle brackets (&lt;&gt;) after the class name.

```cpp
int main() {
    Pair<int> p1(1, 2);          // Creates an instance of 'Pair' for integers
    Pair<double> p2(3.5, 4.2);   // Creates an instance of 'Pair' for doubles
}
```

## Template specialization

Template specialization allows you to define custom behavior for a specific data type. Use the 'template' keyword followed by angle brackets (&lt;&gt;) containing the specific data type.

```cpp
template <class T>
void fun(T a)
{
   std::cout << "The main template fun(): "
        << a << std::endl;
}
 
template<>
void fun(int a)
{
    std::cout << "Specialized Template for int type: "
         << a << std::endl;
}

int main()
{
    fun<char>('a');
    fun<int>(10);
    fun<float>(10.14);
}
```

## Conclusion

Templates in C++ provide a powerful tool for generic programming, enabling the creation of reusable functions and classes that can work with various data types. By understanding and utilizing templates, you can write more efficient and maintainable code. In future articles, we will dive deeper into templates, exploring topics such as template specialization, variadic templates, and template metaprogramming.