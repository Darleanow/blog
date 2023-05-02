---
title: "Input/Output (I/O) Streams in C++: File and Console Operations"
seoTitle: "I/O in C++"
datePublished: Tue May 02 2023 22:00:42 GMT+0000 (Coordinated Universal Time)
cuid: clh6tcnnc0bddojnv8qzl1h8l
slug: inputoutput-io-streams-in-c-file-and-console-operations
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682867494079/e4024c56-14a9-4d50-b202-0949cfe6f9fd.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682867723658/bb202106-90fd-46ab-88c6-54e623bda68a.jpeg
tags: cpp, programming-blogs, streams, cpp-ck4ra5k7300nlv2s1jbkdp2qh, input-output

---

Input/Output (I/O) streams in C++ provide a convenient and consistent way to handle reading from and writing to various sources, such as the console or files. The C++ Standard Library provides a set of stream classes to facilitate I/O operations. In this article, we will discuss the fundamentals of I/O streams in C++ and how to use them for file and console operations.

## Console I/O: cin, cout, cerr, clog

The C++ Standard Library provides four predefined objects for console I/O:

* `cin`: Standard input stream for reading from the console
    
* `cout`: Standard output stream for writing to the console
    
* `cerr`: Standard error stream for writing error messages to the console
    
* `clog`: Standard log stream for writing log messages to the console
    

These objects are defined in the `<iostream>` header file.

```cpp
#include <iostream>

int main() {
    int number;
    std::cout << "Enter a number: ";
    std::cin >> number;
    std::cout << "You entered: " << number << std::endl;
    std::clog << "This is a log message." << std::endl;
    std::cerr << "This is an error message." << std::endl;
}
```

## File I/O: ifstream, ofstream, fstream

To perform file I/O operations, you need to include the `<fstream>` header file and use the following stream classes:

* `ifstream`: Input file stream for reading from files
    
* `ofstream`: Output file stream for writing to files
    
* `fstream`: File stream for both reading and writing
    

```cpp
#include <iostream>
#include <fstream>

int main() {
    std::ofstream outFile("output.txt");
    outFile << "This is a line of text." << std::endl;
    outFile.close();

    std::ifstream inFile("input.txt");
    std::string line;
    while (std::getline(inFile, line)) {
        std::cout << line << std::endl;
    }
    inFile.close();
}
```

## Stream Manipulators

Stream manipulators are functions or objects that can be used to modify the behavior of I/O streams. They are defined in the `<iomanip>` header file. Some commonly used manipulators include `setw`, `setprecision`, `fixed`, and `boolalpha`.

```cpp
#include <iostream>
#include <iomanip>

int main() {
    int number = 42;
    double pi = 3.14159;
    bool isTrue = true;

    std::cout << std::setw(10) << number << std::endl;
    std::cout << std::setprecision(2) << std::fixed << pi << std::endl;
    std::cout << std::boolalpha << isTrue << std::endl;
}
```

## Conclusion

I/O streams in C++ offer a consistent way to handle reading from and writing to various sources, such as files and the console. In this article, we discussed the basics of I/O streams, including console I/O using cin, cout, cerr, and clog, file I/O using ifstream, ofstream, and fstream, and stream manipulators. Understanding and effectively using I/O streams is essential for performing I/O operations in your C++ programs. In future articles, we will explore more advanced topics related to I/O streams and other important aspects of C++ programming.