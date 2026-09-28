[ascii table](https://www.asciitable.com/)

strings in c++ are just a specific type of character array where it the array stores a bunch of characters stringed together to make one coherent string of characters

```cpp
#include <string>
#include <string_view>
#include <iostream>

char* string = "this is a c-style string variable";

char cstring[100] = "this is a c-style string with a limited number of characters"

std::string lib_string = "this is a safer string but more costly on performance"

std::string_view svString = "this is a read-only string "

std::cout << "this is a c-style string literal" << std::endl;

```

In modern c++ (C++17 and above) it is recommended to stay away from using C-style string variables as they are dangerous because you're dealing with direct memory with no safe guards and instead use the `standard library string` 

### std::string
[cppref](https://cplusplus.com/reference/string/string/)

std::string is the default type you should use when dealing with strings and manipulating them. It has the capability to shrink and expand dynamically. 

However the `std::string` is expensive on initialization as when it initializes it copy's the string literal used to initialize the string variable, which because a string is just an array it invokes a O(n) time to copy:

```cpp
#include <string>

std::string s = "this is a string" // <-- 's' will copy the string literal into its variable value and store
```

so when using strings, especially in functions, it is preferred to use `std::string_view` instead of `std::string` because of the expensive copy it will make upon initialization, unless that string will be manipulated throughout its lifetime then you should parse the string through by **reference** and **never** by value

When return an `std::string` it is only ok to do under the following conditions:
- A local variable of type `std::string`.
- A `std::string` that has been returned by value from another function call or operator.
- A `std::string` temporary that is created as part of the return statement.

This because, under these conditions, a string will invoke its move semantics to the next string without creating a copy at all.
### std::string_view
[cppref](https://en.cppreference.com/cpp/header/string_view)

To solve the issue of the expensive initalizations and copies with `std::string` we instead swap to std::string_view, which is essentially a **read-only** string meaning we can't modify the value at all 

However, this is a lot more performant than `std::string` as `std::string_view` just **references** the existing string variable or literal defined instead of copying it 

```cpp
#include <string_view>
#include <iostream>

std::string_view str = "this is a read-only string" //<-- 'str' is just taking a ref to the string literal, no copies are made
std::cout << str << std::endl;

```

So therefore, when you're only reading from a string, it is better to use `std::string_view` than `std::string`

`std::string_view` can be initialized with other string related type which include, **string literals and std::string**

```cpp
#include <string>
#include <string_view>

std::string ns = "this is a normal string"

std::string_view sv = ns //<-- creates a ref to 'ns', any changes made to 'ns' will apply to string_view

std::string_view sv2 = "this is a string literal" //<-- creates a ref to the string literal used to initalize 

std::string_view sv3 = sv //<-- can initialize a string view with another string view

```

`std::string_view` also fully supports `constexpr` meaning we are able to create compiler specific code using strings.

```cpp
#include <iostream>
#include <string_view>

int main()
{
    constexpr std::string_view s{ "Hello, world!" }; // s is a string symbolic constant
    std::cout << s << '\n'; // s will be replaced with "Hello, world!" at compile-time

    return 0;
}
```

## String literals 

As you might've seen throughout, a string literal is a bunch a characters wrapped in the `" "` to define a string:

```cpp
"this is a string literal"
```

there are 3 types of string literals in c++


| literal                  | format |
| ------------------------ | ------ |
| C-style string literal   | `""`   |
| std::string literal      | `""s`  |
| std::string_view literal | `""sv` |
To access the other two you **MUST** declare a `using namespace std::literals` statement to apply the other two, otherwise it will not compile:

```cpp
#include <string>
#include <string_view>

using namespace std::literals;

std::string s = "this is a std::string literal"s;

std::string_view sv = "this is a std::string_view literal"sv;

```

the other two types of literals really only provide safety of initializing and manipulation as well as utility functions.

So it is generally preferred you use the other two string literals