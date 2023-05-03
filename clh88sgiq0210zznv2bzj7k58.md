---
title: "Concurrency in C++: Multithreading and Synchronization"
seoTitle: "Concurrency in C++"
datePublished: Wed May 03 2023 22:00:39 GMT+0000 (Coordinated Universal Time)
cuid: clh88sgiq0210zznv2bzj7k58
slug: concurrency-in-cpp
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682867817868/5ce74a0b-f092-4ab4-b1cd-6f06fad46458.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682868223536/0b5c49d0-4564-4aa7-bfac-146189355458.jpeg
tags: cpp, programming-blogs, multithreading, concurrency, mutex

---

Concurrency is a powerful concept in modern programming languages, enabling the development of applications that can execute multiple tasks simultaneously. C++11 introduced support for multithreading, providing a standard way to manage threads and synchronize access to shared resources. In this article, we will discuss the fundamentals of concurrency in C++, focusing on multithreading and synchronization.

## Creating and managing threads

C++ provides the `std::thread` class, which allows you to create and manage threads. To use `std::thread`, include the `<thread>` header file.

Here's an example of creating a simple thread:

```cpp
#include <iostream>
#include <thread>

void my_function() {
    std::cout << "Hello from my_function!" << std::endl;
}

int main() {
    std::thread t(my_function);
    t.join(); // Wait for the thread to finish
}
```

## Passing arguments to threads

You can pass arguments to a thread by providing them after the function pointer in the `std::thread` constructor.

```cpp
#include <iostream>
#include <thread>

void print_sum(int a, int b) {
    std::cout << "Sum: " << a + b << std::endl;
}

int main() {
    int x = 3;
    int y = 5;
    std::thread t(print_sum, x, y);
    t.join();
}
```

## Synchronizing access to Shared Ressources

When multiple threads access shared resources, you need to ensure proper synchronization to avoid race conditions. C++ provides several synchronization primitives, such as `std::mutex`, `std::lock_guard`, and `std::unique_lock`.

Here's an example of using a mutex to protect access to a shared resource:

```cpp
#include <iostream>
#include <thread>
#include <mutex>

std::mutex mtx;

void print_with_lock(int x) {
    std::unique_lock<std::mutex> lock(mtx);
    std::cout << "Thread " << x << " is running" << std::endl;
    lock.unlock();
}

int main() {
    std::thread t1(print_with_lock, 1);
    std::thread t2(print_with_lock, 2);
    t1.join();
    t2.join();
}
```

## Conditions variables

Condition variables allow you to synchronize threads based on specific conditions. They are often used in conjunction with mutexes to control access to shared resources and notify waiting threads when a condition is met.

```cpp
#include <iostream>
#include <thread>
#include <mutex>
#include <condition_variable>

std::mutex mtx;
std::condition_variable cv;
bool ready = false;

void print_with_condition(int x) {
    std::unique_lock<std::mutex> lock(mtx);
    cv.wait(lock, [] { return ready; });
    std::cout << "Thread " << x << " is running" << std::endl;
}

int main() {
    std::thread t1(print_with_condition, 1);
    std::thread t2(print_with_condition, 2);

    {
        std::unique_lock<std::mutex> lock(mtx);
        ready = true;
    }

    cv.notify_all();

    t1.join();
    t2.join();
}
```

## Conclusion

Concurrency in C++ allows for the development of applications capable of executing multiple tasks simultaneously. In this article, we covered the basics of concurrency in C++, including creating and managing threads, passing arguments to threads, synchronizing access to shared resources, and using condition variables. Understanding concurrency and multithreading is essential for developing efficient and high-performance C++ applications. In future articles, we will explore more advanced topics in concurrent programming, such as thread pools, parallel algorithms, and lock-free data structures.