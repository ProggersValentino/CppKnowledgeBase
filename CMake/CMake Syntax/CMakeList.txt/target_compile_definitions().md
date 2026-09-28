ref: [cmake docs -> target_compile_definitions()](https://cmake.org/cmake/help/latest/command/target_compile_definitions.html)

For when we have preprocessor MACROs within the code base to which needs to be defined to CMake so it can properly build  

for instance if you have MACRO in a cpp file:
```cpp
#ifdef PRINT_ERROR
	#define PP int
#endif
```

then we would need to define within the subdirectory's CMakeList.txt:

```cmake
target_compile_definitions(<target name> PUBLIC/PRIVATE PRINT_ERROR)

target_compile_definitions(<target name> PUBLIC/PRIVATE PP)
```

To which then allows the cmake to build with no errors because all the MACROs have been defined