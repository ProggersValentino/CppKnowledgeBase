ref: [cmake -> add libraries](https://cmake.org/cmake/help/latest/command/add_library.html)

To add a library **(Static, module, shared)** add use
``` cpp
add_library(<name>, [<type>] [Exclude from all] <sources...) 
```

for instance if you want to add a dll called "my_lib":

``` cpp
add_library(Library MODULE "my_lib.h" "my_lib.cpp") 
```

which provides cmake the necessary information needed to build the library file correctly

however, this will not compile on its own and will **return an error** when attempting to build you will receive this error:
```cmake
FAILED: CMake_TestProject/CMake_TestProject 
: && /usr/bin/g++-13 -g  CMake_TestProject/CMakeFiles/CMake_TestProject.dir/CMake_TestProject.cpp.o -o CMake_TestProject/CMake_TestProject   && :
/usr/bin/ld: CMake_TestProject/CMakeFiles/CMake_TestProject.dir/CMake_TestProject.cpp.o: in function `main':
/home/proggersvalentino/.vs/CMake_TestProject/CMake_TestProject/CMake_TestProject.cpp:11:(.text+0x9): undefined reference to `Lib::PrintDumbText()'
```

this is because we **have to tell the linker** that we have a library that we would like to link to the executable which is with the [target_link_library](target_link_library):
```cpp
//...

target_link_libraries(<name of target> <items we want to link that target to>)

//...
```

