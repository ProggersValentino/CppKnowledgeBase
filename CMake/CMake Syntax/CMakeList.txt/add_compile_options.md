ref: [cmake docs -> add_compile_options()](https://cmake.org/cmake/help/latest/command/add_compile_options.html)

Similar to [[target_compile_options]] however it adds options that are applied to all targets by default.

For instance, if you want to activate the warning options on the gcc compiler but want it for all target then you would do: 
```cmake
set(GCC_WARNINGS
-Wall
-Wextra
-Wpedantic
)

add_compile_options(${GCC_WARNINGS})
```

so now all targets will have these warning options activated 