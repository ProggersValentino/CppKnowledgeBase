ref: [cmake docs -> if](https://cmake.org/cmake/help/latest/command/if.html) 

if statements in CMake follow almost the same structure as a MACRO if statement in c++ 

```cpp
if(COMPILE_EXECUTABLE)
	add_subdirectory ("CMake_TestProject")
else()
	message("W/o exe. compiling ")
endif()
```