ref: [cmake docs -> get_property_target()](https://cmake.org/cmake/help/latest/command/get_target_property.html)

get a specific property from a selected target. generally properties are used to control how a target is built.

for instance, you need the sources of a library target:
```cmake
get_target_property(TARGET_SOURCES <"target name"> <property variable name>)
```