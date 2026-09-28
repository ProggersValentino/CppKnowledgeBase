## C++ and C arrays 
[cppref](https://en.cppreference.com/cpp/container/array)

In C++ you can have two types of arrays, a C-style array and a std::array:

```cpp
#include <array>
#include <iostreams>

int main()
{
	//c++ array
	std::array<int, 5> arr = {2, 5, 7, 10, 54}	
	
	//c++ array initialized with default value (0)
	std::array<int, 5> arr {}	
	
	//c-style array
	int carr[5] {4, 6, 7, 1, 9}

}
```

Arrays in c++ are static in size meaning if you want to resize them you have 

The standard leans towards using c++ arrays over c-style arrays because of their safety with allocating and reallocating elements unlike the c-style arrays where you're handling memory directly, so it's really easy to breach out of the memory block allocated. 

However, comparatively, because of that direct access, c-style arrays can be seen as the faster option.

#### Prefixing with constexpr
As you see, with c++ array you must define the type of the array and its size, however this can be negated by prefixing the [constexpr](costexpr) keyword by the initialization of the array. 

```cpp
constexpr std::array arr = {2, 5, 7, 10, 54}	
```

This works because by using constexpr we are telling the compiler to infer and filling the necessary details at compile time to make a valid array.

Generally, whenever possible using std::array, you should always prefix the initialization with a **constexpr** 
## Vectors 
[cppref](https://en.cppreference.com/cpp/container/vector)

