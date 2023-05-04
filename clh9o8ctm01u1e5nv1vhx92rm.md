---
title: "Advanced Pointers in C++: Pointer-to-Member Functions, Custom Smart Pointers, and Complex Data Structures"
seoTitle: "Advanced Pointers in C++, Custom Smart Pointers etc..."
datePublished: Thu May 04 2023 22:00:41 GMT+0000 (Coordinated Universal Time)
cuid: clh9o8ctm01u1e5nv1vhx92rm
slug: advanced-pointers-in-c-pointer-to-member-functions-custom-smart-pointers-and-complex-data-structures
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682868296239/0c06e62e-428c-42df-b498-10e519caf1c9.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682869804219/1690ff0c-bba2-4961-9353-1a280eb9d589.jpeg
tags: cpp, programming-blogs, memory-management, advanced-pointers

---

Pointers are an essential aspect of C++ programming, providing powerful tools for managing memory, working with functions, and implementing complex data structures. In this article, we will explore advanced topics related to pointers, including pointer-to-member functions, creating custom smart pointers, and implementing complex data structures using pointers.

## Pointer-to-member functions

Pointer-to-member functions allow you to store and invoke non-static member functions of a class. To declare a pointer-to-member function, use the following syntax:

```cpp
ReturnType (ClassName::*PointerName)(Parameters);
```

Here's an example of using a pointer-to-member function:

```cpp
#include <iostream>

class MyClass {
public:
    void print_hello() {
        std::cout << "Hello from MyClass!" << std::endl;
    }
};

int main() {
    void (MyClass::*print_func)() = &MyClass::print_hello;
    MyClass obj;
    (obj.*print_func)(); // Call the print_hello function through the pointer
}
```

## Custom smart pointers

While C++ provides built-in smart pointers like `std::unique_ptr` and `std::shared_ptr`, you may sometimes need to create custom smart pointers to handle specific resource management scenarios. Custom smart pointers can be implemented using a class template that overloads the pointer-related operators, such as `->`, `*`, and `=`.

Here's a simple example of a custom smart pointer:

```cpp
template <typename T>
class CustomSmartPointer {
public:
    CustomSmartPointer(T* ptr) : m_ptr(ptr) {}
    ~CustomSmartPointer() { delete m_ptr; }

    T* operator->() const { return m_ptr; }
    T& operator*() const { return *m_ptr; }

private:
    T* m_ptr;
};
```

## Implementing complex data structures using Pointers

Pointers are crucial for implementing complex data structures, such as linked lists, trees, and graphs. They enable the creation of dynamic, non-contiguous data structures that can grow and shrink during program execution.

For example, here's a simple implementation of a singly-linked list:

```cpp
#include <iostream>

struct Node {
    int data;
    Node* next;
};

void print_list(Node* head) {
    Node* current = head;
    while (current != nullptr) {
        std::cout << current->data << " ";
        current = current->next;
    }
    std::cout << std::endl;
}

int main() {
    Node* head = new Node{1, nullptr};
    head->next = new Node{2, nullptr};
    head->next->next = new Node{3, nullptr};

    print_list(head);

    // Don't forget to delete the nodes to avoid memory leaks
    delete head->next->next;
    delete head->next;
    delete head;
}
```

## Conclusion

Advanced pointer techniques in C++ provide powerful tools for handling memory, working with functions, and implementing complex data structures. In this article, we discussed pointer-to-member functions, creating custom smart pointers, and implementing complex data structures using pointers. Understanding these advanced topics is essential for writing efficient, flexible, and maintainable C++ code. As you continue to explore C++ programming, you will encounter even more advanced techniques that build upon these foundations.