---
title: "Embracing Modern C++: In-depth Exploration of Key Features from C++11, C++14, C++17, and C++20"
seoTitle: "Modern C++ in depth"
datePublished: Sun May 07 2023 22:00:39 GMT+0000 (Coordinated Universal Time)
cuid: clhdyjuyi0bcuonnv7rhebsyk
slug: embracing-modern-c-pp
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683382246641/a766d639-a795-4bf7-84ad-4de72a3ffa2c.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683386848964/cc3745a8-4878-4f79-b2ae-73c0d7e22ad6.jpeg
tags: cpp, modern-c, advanced-c, modern-programming

---

C++ has come a long way since its inception in the early 1980s. With each new standard release, the language introduces new features aimed at improving performance, productivity, and code readability. In this article, we will delve into the key features introduced in C++11, C++14, C++17, and C++20, providing examples and exploring their intricacies to help you understand how to effectively use them in your programs.

---

## C++ 11

### Auto keyword

The auto keyword simplifies variable declaration by automatically deducing the type of the variable from its initializer. This feature reduces verbosity and makes the code more readable. The type deduction follows the same rules as template argument deduction.

```cpp
auto i = 42; // i is an int
auto d = 3.14; // d is a double
auto s = "Hello, world!"; // s is a const char*
```

The auto keyword can also be used in conjunction with the decltype specifier to deduce the type of an expression, which can be helpful when working with complex or templated types.

```cpp
std::vector<int> numbers = {1, 2, 3};
auto itr = numbers.begin(); // itr is a std::vector<int>::iterator
decltype(itr) another_itr; // another_itr has the same type as itr
```

### Lambda expressions

Lambda expressions are a convenient way to define anonymous functions (functions without a name) directly in the code. They are particularly useful when working with algorithms and functions that require a callable object as an argument.

A lambda expression is defined by a set of square brackets (the capture clause), followed by a set of parentheses (the parameter list), an optional return type, and the function body enclosed in curly braces.

```cpp
auto add = [](int a, int b) { return a + b; }; // A simple lambda expression
int result = add(3, 4); // result is 7
```

The capture clause specifies how the lambda expression captures variables from its surrounding scope. The capture modes are:

* \[&\]: Captures all variables by reference.
    
* \[=\]: Captures all variables by value.
    
* \[this\]: Captures the "this" pointer of the enclosing class by value.
    
* \[&variable\]: Captures the specified variable by reference.
    
* \[=, &variable\]: Captures all variables by value, but captures the specified variable by reference.
    

```cpp
int x = 1, y = 2;
auto add_x_y = [x, &y] { return x + y; }; // Captures x by value and y by reference
```

### Range-based for loops

Range-based for loops simplify the process of iterating over a container or an array, making the code more readable and less error-prone. The syntax of a range-based for loop is as follows:

```cpp
for (declaration : range_expression) statement
```

The declaration is the variable that will hold the current element, and the range\_expression is the container or array to be iterated over.

```cpp
std::vector<int> numbers = {1, 2, 3, 4, 5};
for (auto number : numbers) {
    std::cout << number << ' ';
}
```

Range-based for loops use the begin() and end() member functions of the container or the corresponding non-member functions for arrays to obtain iterators. The loop automatically takes care of advancing the iterator and checking for the end of the range.

### Smart pointers

Smart pointers are a safer and more convenient way to manage dynamic memory allocation. They automatically release the memory when it is no longer needed, helping to prevent memory leaks and dangling pointers. C++11 introduces three smart pointer types: `std::unique_ptr`, `std::shared_ptr`, and `std::weak_ptr`.

* `std::unique_ptr`: Represents unique ownership of a dynamically allocated object. It automatically deletes the object when the `unique_ptr` goes out of scope. It cannot be copied, but it can be moved to transfer ownership.
    
    ```cpp
    std::unique_ptr<int> ptr(new int(42)); // Unique ownership of an int object
    auto ptr2 = std::move(ptr); // Transfer ownership to ptr2; ptr is now empty
    ```
    
* `std::shared_ptr`: Represents shared ownership of a dynamically allocated object. It keeps track of the number of `shared_ptr` instances that share ownership of the object, and automatically deletes the object when the last `shared_ptr` owning it goes out of scope.
    
    ```cpp
    std::shared_ptr<int> sptr(new int(42)); // Shared ownership of an int object
    auto sptr2 = sptr; // Both sptr and sptr2 share ownership; reference count is 2
    ```
    
* `std::weak_ptr`: A weak reference to a dynamically allocated object managed by a `shared_ptr`. It does not contribute to the reference count and does not prevent the object from being deleted. It can be used to break circular references or to observe an object without extending its lifetime.
    
    ```cpp
    std::weak_ptr<int> weak = sptr; // weak_ptr observes the int object owned by sptr
    if (auto locked = weak.lock()) { // Check if the object still exists and acquire a shared_ptr
        std::cout << "Object is still alive\n";
    } else {
        std::cout << "Object has been deleted\n";
    }
    ```
    

### Variadic templates

Variadic templates allow you to create functions and classes that accept a variable number of template arguments. This feature enables more flexible and reusable code.

A variadic template is defined using the `typename...` or `class...` syntax followed by a template parameter pack name. The parameter pack can be expanded using the pack expansion syntax (`...`) in the function or class definition.

```cpp
template<typename... Args>
void print(Args... args) {
    (std::cout << ... << args) << '\n'; // Fold expression expands the parameter pack
}

print("hello", 42, 3.14); // Prints "hello423.14"
```

Variadic templates can be used to implement generic functions or classes, such as tuples or function wrappers, that can accept any number and type of arguments.

---

## C++ 14

### Generic Lambdas

Generic lambdas extend the functionality of lambda expressions by allowing you to use the auto keyword in the parameter list. This enables the creation of lambda expressions that can accept arguments of different types.

```cpp
auto generic_sum = [](auto a, auto b) { return a + b; };
std::cout << generic_sum(3, 4) << '\n'; // 7
std::cout << generic_sum(3.1, 4.2) << '\n'; // 7.3
```

The compiler generates a templated function object (functor) for the lambda expression, with the auto parameters being deduced as template arguments.

### Return-type deduction

C++14 introduces return type deduction for regular functions, similar to how the auto keyword works for variable declaration. This feature simplifies the function declaration and makes the code more readable.

```cpp
auto add(int a, int b) {
return a + b;
}

int sum = add(3, 4); // sum is 7
```

When using return type deduction, the compiler deduces the return type based on the function's return statements. It is important to ensure that all return statements have a consistent type or are implicitly convertible to a common type. Otherwise, a compilation error will occur.

### Binary literals

Binary literals allow you to represent integer values directly in binary form, making it easier to work with bitwise operations and low-level programming tasks.

```cpp
int binary_value = 0b110101; // 53 in decimal
```

In C++14, you can specify binary literals using the `0b` or `0B` prefix, followed by a sequence of binary digits (`0` and `1`). Binary literals can be combined with the digit separators feature to improve readability.

```cpp
uint32_t bit_pattern = 0b1100'1010'1111'0000;
```

### Digit separators

Digit separators allow you to use single quotes as a separator within numeric literals to improve readability. This feature is especially useful when dealing with large numbers or bit patterns.

```cpp
int large_number = 1'000'000;
uint32_t bit_pattern = 0b1100'1010'1111'0000;
```

The digit separator can be used with decimal, binary, octal, and hexadecimal literals. Note that the separator does not affect the value of the numeric literal; it is solely for improving readability.

---

## C++ 17

### Structured bindings

Structured bindings enable you to declare multiple variables that can be initialized from a tuple, pair, or aggregate data type, such as arrays or structs. This feature simplifies the code and improves readability.

```cpp
std::tuple<int, std::string> get_data() {
    return {42, "hello"};
}

auto [value, text] = get_data();
std::cout << value << ", " << text << '\n';
```

Structured bindings work by decomposing the given object into its constituent elements and binding them to the specified variables. The number of variables in the structured binding must match the number of elements in the object. Additionally, the object must be either a tuple-like type or an aggregate type with non-static data members.

### If and switch with initializer

C++17 introduces the ability to declare a variable within the scope of an if statement or switch statement, which can help reduce code redundancy and improve readability.

```cpp
if (auto itr = my_map.find(key); itr != my_map.end()) {
    std::cout << "Found: " << itr->second << '\n';
} else {
    std::cout << "Not found\n";
}
```

In this example, the variable `itr` is initialized with the result of `my_map.find(key)` and is in scope only within the if statement and its associated else block. This reduces the need for separate variable declarations and helps prevent errors related to variable scope.

### Inline variables

Inline variables allow you to define variables with external linkage that have the same behavior as inline functions. This feature simplifies the management of global and class-scoped variables.

```cpp
inline constexpr int global_variable = 42;
```

An inline variable is defined using the `inline` keyword and has the same semantics as an inline function. It is guaranteed to have the same address in all translation units that include its definition, which helps to prevent multiple-definition errors.

### std::optionnal

The std::optional class template provides a way to represent a value that may or may not be present. This feature simplifies error handling and provides a more expressive way to represent nullable values.

```cpp
std::optional<int> maybe_value;
if (maybe_value) {
    std::cout << "Value: " << *maybe_value << '\n';
} else {
    std::cout << "No value\n";
}
```

`std::optional` can be used to indicate that a function may not return a valid result. For example, a function that searches for an element in a container could return an `std::optional` containing the found element or an empty `std::optional` if the element is not found.

```cpp
std::optional<int> find_element(const std::vector<int>& container, int value) {
    for (const auto& element : container) {
        if (element == value) {
            return element;
        }
    }
    return {}; // Return an empty optional to indicate that the value was not found
}
```

---

## C++ 20

### Concepts

Concepts provide a way to define and constrain template arguments based on their properties, such as the operations they support or the types they can be converted to. This feature improves compile-time error messages and allows for more expressive and readable code.

```cpp
template<typename T>
concept Addable = requires(T a, T b) {
    { a + b } -> std::same_as<T>;
};

template<Addable T>
T sum(T a, T b) {
    return a + b;
}
```

In this example, the `Addable` concept checks whether the given type `T` supports the addition operation and whether the result is of the same type as `T`. The `sum` function template uses the `Addable` concept to constrain its template argument, ensuring that the function can only be instantiated for types that satisfy the concept.

### Ranges

Ranges introduce a new way to work with sequences of values, providing a more concise and expressive syntax for algorithms and data manipulation. They simplify common tasks, such as filtering, transforming, or generating sequences.

```cpp
std::vector<int> numbers = {1, 2, 3, 4, 5};
auto even_numbers = numbers | std::views::filter([](int n) { return n % 2 == 0; });
```

In this example, the `std::views::filter` adaptor is used to create a new range containing only the even numbers from the original `numbers` vector. Ranges can be combined and chained using the pipe operator (`|`) to create complex data manipulation pipelines.

### Coroutines

Coroutines provide a new way to write asynchronous and concurrent code, allowing functions to be suspended and resumed at specific points in their execution. This feature simplifies the management of complex control flows and improves performance for certain types of tasks.

```cpp
std::future<int> async_sum(int a, int b) {
    co_return a + b;
}
```

In this example, the `async_sum` function is defined as a coroutine using the `co_return` keyword. When the function is called, it immediately returns a `std::future` representing the asynchronous result of the computation. The actual addition is performed asynchronously, and the result can be retrieved using the `std::future::get` method.

### constexpr improvements

C++20 extends the capabilities of constexpr functions, allowing more operations to be executed at compile-time, such as dynamic memory allocation and virtual function calls. This feature enables more efficient code generation and better optimization opportunities.

```cpp
constexpr int factorial(int n) {
    if (n <= 1) {
        return 1;
    }
    return n * factorial(n - 1);
}

constexpr int result = factorial(5); // result is 120, computed at compile-time
```

### std::format

The `std::format` function provides a type-safe and extensible way to format strings, replacing the traditional `printf`\-style formatting and the `std::stringstream` approach. It is based on the syntax of Python's format strings and is designed to be more readable, expressive, and safe.

```cpp
std::string message = std::format("Hello, {}! Today is {}.", "Alice", "Sunday");
std::cout << message << '\n';
```

`std::format` uses curly braces (`{}`) as placeholders for the values to be inserted into the string. The placeholders can include format specifiers to control the appearance of the output, such as the number of decimal places for floating-point numbers or the alignment and width of the output.

```cpp
std::string formatted_number = std::format("{:.2f}", 3.14159); // "3.14"
```

### Spaceship operator

The spaceship operator, also known as the three-way comparison operator, provides a way to compare two objects and determine their relative order in a single operation. It returns a value of type `std::partial_ordering`, `std::weak_ordering`, or `std::strong_ordering`, which indicates whether the left-hand operand is less than, equal to, or greater than the right-hand operand.

```cpp
struct Point {
    int x, y;

    constexpr std::strong_ordering operator<=>(const Point& other) const {
        if (auto cmp = x <=> other.x; cmp != 0) {
            return cmp;
        }
        return y <=> other.y;
    }
};
```

In this example, the `Point` class defines a spaceship operator that compares the `x` and `y` coordinates of two `Point` objects. The operator is implemented as a member function and can be used with the standard comparison operators, such as `<`, `==`, and `>`.

### Lambdas with templated parameters

C++20 extends the functionality of lambda expressions by allowing you to define templated parameters, which enables the creation of more generic and reusable lambda expressions.

```cpp
auto print_any = []<typename T>(const T& value) {
    std::cout << value << '\n';
};

print_any(42);
print_any(3.14);
print_any("Hello, world!");
```

In this example, the `print_any` lambda expression accepts a templated parameter `T`, which is deduced from the argument passed to the lambda. The lambda can then be used with any type that is compatible with the `std::cout` output stream.

---

## Conclusion

By exploring and incorporating these modern C++ features into your programs, you can improve the performance, productivity, and readability of your code. Embrace the latest C++ standards to stay up-to-date with the evolving language and make the most out of its capabilities.