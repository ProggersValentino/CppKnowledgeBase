ref: [cmake docs -> set_property()](https://cmake.org/cmake/help/latest/command/set_property.html)

sets predefined properties within for a specified target to true/false

for instance, if I want to activate link time optimizations I would need to:
```cmake
set_property(TARGET <target name> PROPERTY INTERPROCEDURAL_OPTIMIZATION TRUE)
```