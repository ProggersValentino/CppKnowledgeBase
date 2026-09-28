ref: [cmake docs -> target_include_directories](https://cmake.org/cmake/help/latest/command/target_include_directories.html)

when you organise your file structure into subdirectories you need to expose the directory when compiling a target that is included across multiple CMakeLists 
```cpp
target_include_directories(<target> [SYSTEM] [AFTER|BEFORE]
  {INTERFACE|PUBLIC|PRIVATE} <dir...
  [{INTERFACE|PUBLIC|PRIVATE} <dir>...]...)
```

for instance say this is the file structure:
![[Pasted image 20260317192235.png]]

and you need to ensure the src header and cpp files are included in other subdirectories which then in the src CMakeLists you include:

```cpp
add_library(Library SHARED "my_lib.h" "my_lib.cpp")

target_include_directories(Library PUBLIC "../../")

```

which is done after adding an executable or library.

This allows you to now be able to **include files by their name** compared to having to provide the absolute path

