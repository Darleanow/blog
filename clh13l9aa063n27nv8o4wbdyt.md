---
title: "Understanding the Standard Template Library (STL) in C++"
seoTitle: "STL in C++"
datePublished: Fri Apr 28 2023 22:00:42 GMT+0000 (Coordinated Universal Time)
cuid: clh13l9aa063n27nv8o4wbdyt
slug: understanding-the-standard-template-library-stl-in-c
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682356188189/824ac7de-f84f-4320-aa74-36644e11fbd0.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682356645580/6b6b2b7c-d6b3-4b42-8ca0-1fe9c4e2d4b3.jpeg
tags: programming-blogs, cpp-ck4ra5k7300nlv2s1jbkdp2qh, stl

---

The Standard Template Library (STL) in C++ is a powerful library containing a collection of template classes and functions that provide common data structures and algorithms. It enables developers to write efficient and maintainable code by leveraging these pre-built components. In this beginner's guide, we will provide an introduction to the STL, explain its main components, and demonstrate its usage with simple examples.

## Main components of the STL

The STL consists of four main components:

* Containers: Data structures that store and organize data, such as vectors, lists, sets, and maps.
    
* Algorithms: Functions that perform common operations on containers, such as sorting, searching, and transforming data.
    
* Iterators: Objects that enable traversal of container elements.
    
* Function objects (Functors): Objects that can be called like functions, often used as arguments for algorithms.
    

### Containers

Let's explore some common STL containers:

* Vector: A dynamic array that can grow or shrink in size. It is useful for storing elements that need to be accessed randomly or resized frequently.
    
    ```cpp
    #include <vector>
    
    int main() {
        std::vector<int> my_vector = {1, 2, 3, 4, 5};
        my_vector.push_back(6); // Add an element to the end
        my_vector.pop_back(); // Remove the last element
        int first_element = my_vector.front(); // Access the first element
        int last_element = my_vector.back(); // Access the last element
    }
    ```
    
* list: A doubly-linked list that allows for efficient insertion and deletion of elements. It is useful when you need to perform frequent insertions or deletions but do not require random access to elements.
    
    ```cpp
    #include <list>
    
    int main() {
        std::list<int> my_list = {1, 2, 3, 4, 5};
        my_list.push_front(0); // Add an element to the beginning
        my_list.pop_back(); // Remove the last element
    }
    ```
    
* map: An associative container that stores key-value pairs in sorted order. It is useful for storing data that needs to be looked up using a unique key.
    
    ```cpp
    #include <map>
    
    int main() {
        std::map<std::string, int> my_map;
        my_map["apple"] = 1; // Add a key-value pair
        my_map["banana"] = 2;
        int value = my_map["apple"]; // Access value by key
    }
    ```
    

### Algorithms

STL algorithms can be applied to containers to perform various operations. Here are some examples:

* Sort: Sort elements in a specified range.
    
    ```cpp
    #include <vector>
    #include <algorithm>
    
    int main() {
        std::vector<int> numbers = {5, 3, 1, 4, 2};
        std::sort(numbers.begin(), numbers.end()); // Sort the vector in ascending order
    }
    ```
    
* Find: Find the first occurrence of an element in a specified range.
    
    ```cpp
    #include <vector>
    #include <algorithm>
    
    int main() {
        std::vector<int> numbers = {5, 3, 1, 4, 2};
        auto it = std::find(numbers.begin(), numbers.end(), 3); // Find the number 3
        if (it != numbers.end()) {
            // Element found
        } else {
            // Element not found
        }
    }
    ```
    
* Count: Count the occurrences of an element in a specified range.
    
    ```cpp
    #include <vector>
    #include <algorithm>
    
    int main() {
        std::vector<int> numbers = {5, 3, 1, 4, 2, 3, 1, 5, 3};
        int count = std::count(numbers.begin(), numbers.end(), 3); // Count the occurrences of 3
    }
    ```
    

### Iterators

Iterators enable traversal of container elements and can be used with STL algorithms. Here are some examples:

* Iterate through a vector using iterators:
    
    ```cpp
    #include <vector>
    #include <iostream>
    
    int main() {
        std::vector<int> numbers = {1, 2, 3, 4, 5};
        for (auto it = numbers.begin(); it != numbers.end(); ++it) {
            std::cout << *it << " "; // Access the element using the dereference operator (*)
        }
    }
    ```
    
* Iterate through a map using iterators:
    
    ```cpp
    #include <map>
    #include <iostream>
    
    int main() {
        std::map<std::string, int> my_map = {{"apple", 1}, {"banana", 2}, {"orange", 3}};
        for (auto it = my_map.begin(); it != my_map.end(); ++it) {
            std::cout << it->first << ": " << it->second << std::endl; // Access key and value using the arrow operator (->)
        }
    }
    ```
    

### Function objects (Functors)

Function objects (functors) are objects that can be called like functions. They can be used as arguments for STL algorithms. Here's an example of using a custom functor for sorting a vector of integers in descending order:

```cpp
#include <vector>
#include <algorithm>
#include <iostream>

class Greater {
public:
    bool operator()(int a, int b) {
        return a > b;
    }
};

int main() {
    std::vector<int> numbers = {5, 3, 1, 4, 2};
    std::sort(numbers.begin(), numbers.end(), Greater()); // Sort the vector using a custom comparator

    for (const auto& num : numbers) {
        std::cout << num << " ";
    }
}
```

## Conclusion

We introduced the Standard Template Library (STL) in C++, discussed its main components, and provided examples of its usage. The STL is a powerful tool for C++ developers, allowing them to write efficient and maintainable code by leveraging pre-built data structures, algorithms, iterators, and functors. As you continue learning C++, I recommend further exploring the STL and its various components to fully appreciate its capabilities and benefits.