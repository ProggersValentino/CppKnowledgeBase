ref: [cmake docs -> target_compile_features](https://cmake.org/cmake/help/latest/command/target_compile_features.html), [cmake docs -> c++ known features](https://cmake.org/cmake/help/latest/prop_gbl/CMAKE_CXX_KNOWN_FEATURES.html#prop_gbl:CMAKE_CXX_KNOWN_FEATURES)

specifies compiler features that are required when compiling the cmake project. 

for instance, if we have made our c++ in standard version 20 then we want reinforce that as a requirement:

```cmake
target_compile_features(<target name> PUBLIC/PRIVATE cxx_std_20)
```

So now any time someone else clones and uses the project, at minimum they must have c++ version 20 installed to compile the project successfully.