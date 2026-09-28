ref: [cmake -> add_subdirectory docs](https://cmake.org/cmake/help/latest/command/add_subdirectory.html)

Adding subdirectories allows you to have **multiple CMakeLists** that can be all combined and built in one 

```cpp
add_subdirectory(source_dir [binary_dir] [EXCLUDE_FROM_ALL] [SYSTEM])
```

for instance, take this directory:
![[Pasted image 20260317184749.png]]

so we have 3 separate CMakeLists each responsible for a part of the code base to which then in the top-level CMakeLists out file would have:

```cpp
add_subdirectory("CMake_TestProject/src")
add_subdirectory ("CMake_TestProject")
```

which now all files in any directories are included for the cmake to build and are able to be build all at once 

**KEY NOTE: Order Matters** 