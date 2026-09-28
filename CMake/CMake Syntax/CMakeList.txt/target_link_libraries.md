ref: [cmake -> target_link_lib doc](https://cmake.org/cmake/help/latest/command/target_link_libraries.html)

Used to tell the linker of certain libraries that need to be linked to source code to make a valid build 

```cpp
target_link_libraries(<target> ... <item>... ...)
```

for instance if you have a library and are using it in an **executable called "MyExecutable"** file then:

``` cpp
//within library CMakeLists ....
add_library(Library MODULE "my_lib.h" "my_lib.cpp")
//....

//within executable CMakeLists ....
target_link_libraries(MyExecutable PUBLIC Library)
//..........
```

which will now link the library to the necessary executable or any other file specified which will allow you to use the ```#include "<some file>``` instead of needing to reference the absolute location.

if we want to include an external library that we are fetching, then we must follow the naming convention of ```<project name>::<library name> ```

for instance you want to use an external library call [zlib](https://github.com/madler/zlib/tree/develop) then it would be:
```cpp
target_link_libraries(<libraryName> PUBLIC ZLIB::ZLIB)
```
### PUBLIC 
```cmake
target_link_libraries(A PUBLIC fmt)
```

library A links to fmt as public which means that library A uses fmt in its implementation. Furthermore, because it is public, fmt is used in A's public API meaning that another library (called C) can use fmt when linking to library A. 

```cmake 
target_link_libraries(C PUBLIC/PRIVATE A)
```

Therefore, C is able to use fmt within their implementation.

### PRIVATE
```cmake
target_link_libraries(B PRIVATE spdlog)
```

When library B **privately links** to spdlog it means that library B's implementation uses spdlog. Unlike PUBLIC, if say library C where to link with B, it **would not** be able to use spdlog library through it.

### INTERFACE
```cmake
add_library(D INTERFACE)
target_link_libraries(D INTERFACE {CMAKE_CURRENT_SOURCE_DIR}/include)
```

When library D is INTERFACE, it generally means that the library is a header-only library with no compilation logic behind it 