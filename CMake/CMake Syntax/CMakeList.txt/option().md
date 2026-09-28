ref: [cmake docs -> option()](https://cmake.org/cmake/help/latest/command/option.html) 

Creates a boolean value that can be toggled on and off.

```cpp
option(<variable> "<help_text>" [value])
```

for instance if i need a variable to toggle between building debug code then I could do:

```cpp
option(COMPILE_DEBUG_CODE "enables/disables debug code to built" OFF)
```

which then can be used in an [if statement](if statements) to activate debug code or deactivate it. while you can toggle the option directly in the CMakeLists, an alternative and probably better option is use the ```
``` ``` -D <option>=<value> ``` command on top of the cmake build command:

```
cmake -S ../../ -B . -D COMPILE_EXECUTABLE=ON
```