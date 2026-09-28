ref: [CppLearn - constexpr](https://www.learncpp.com/cpp-tutorial/constant-expressions/)

**constexpr** is a key word in c++ that allows you to mark a variable or function to compiler to be evaluated at compile time instead of the runtime of the application. This provides a few benefits one of which is increased performance during runtime of the application 

For instance, say we have an array who's size is dependent on a struct/class, but that class can't be created until runtime so size value that defines how big the class is for the array won't be available till runtime. So because the creation of the class doesn't happen till runtime and the array must have its size at compile time, we can't provide the array an accurate size for how much we need. We could just pick a number that we know won't cause the array to over but for this case we must to know the accurate size.

``` c++ 
StorageClass sc = StorageClass();

uint32_t storage[sc.size]
```

 OR instead we can a constexpr to get the evaluation at compile because the size of the class will be constant just the creation is runtime dependent.

  ``` c++ 
  class StorageClass
  {
	int valuex;
	///...
	  
	static constexpr const int DetermineClassSize()
	{
		const int size = sizeof(valuex);
		return size;
	} 
  }
  
  MainProgram
  {
	StorageClass sc = StorageClass();

	uint32_t storage[StorageClass::DetermineClassSize()]
  }
  
  ```
now we have both benefits of having the freedom to create at runtime and pre-allocate storage at compile time 

### Long Ago 

Before C++11 (when constexpr released) the common method to get integral compile-time evaluation, was use template in combination with enum:
``` c++ 
template<uint32_t x> struct Log2 
{
	enum { a = x | (x >> 1),
		   b = a | (a >> 2),
		   c = b | (b >> 4),
		   d = c | (c >> 8),
		   e = d | (d >> 16),
		   f = e >> 1,
		result = Popcount<f>::result 

	};
};

int logResult = Log2<6>::result;
```

this is because with [templates](Templates), they evaluate at compile to which then the compiler would subsequently evaluate and solve all the options within the enum. 