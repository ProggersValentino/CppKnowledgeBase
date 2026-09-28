ref: [Templates -> cppdocs](https://en.cppreference.com/w/cpp/language/templates.html)

Templates is a tool for creating generic classes and/or functions which have a polymorphic behaviour where a generic parameter is defined in the template definition. When the program compiles, the template class/function is generated and implicitly translates the generic values based off type deduction used in the template instantiation

Templates **must** be defined within the **header file** NOT the CPP file, otherwise you will get a linker error: 2019 about how the compiler cant find the definition of the templated function  

``` c++ 20

template <typename T> 
T minimum(const T& lhs, const T& rhs) 
{ 
	return lhs < rhs ? lhs : rhs; 
}
```

``` c++ [label="block 1"]
int a = get_a(); 
int b = get_b(); 
int i = minimum<int>(a, b);
```
