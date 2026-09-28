ref: [cmake docs -> set()]()

the set function allows you to set variable name and values that can be used within other CMakeLists which is done by:

```cpp
set(<variable> <value>... [PARENT_SCOPE])
```

ie

```cmake
set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake/)
```

you use ${variable name} when you need the data value but if you're trying to set something be sure to **NEVER** use the ${} otherwise it will subsitute the variable for the value within it.

you can also have multiple values represented in one variable which acts as an array:
```cmake
set(LIBRARY_SOURCE_FILES PUBLIC 
"gfgf.cpp"
"figma.cpp"
"crmma.cpp")
```