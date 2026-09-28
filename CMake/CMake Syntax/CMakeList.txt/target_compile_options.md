 ref: [cmake docs -> target_compile_options()](https://cmake.org/cmake/help/latest/command/target_compile_options.html), [gcc/clang compiler options](https://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html#index-Wall), [msvc compiler options](https://learn.microsoft.com/en-us/cpp/build/reference/compiler-option-warning-level?view=msvc-170)

Adds options for the compiler to use when compiling a given target.

these options can extend to giving warnings about the code base to grinding the build to a hault.

for instance, say I'm on the gcc (or gnu) compiler and you want to add the warning options for the compiler to do during build:

```cmake 
set(GCC_WARNINGS
-Wall
-Wextra
-Wpedantic
)

target_compile_options(<target name> PUBLIC/PRIVATE ${GCC_WARNINGS})
```

which now whenever the compiler builds the project, it will output warnings to the output terminal if there are any.