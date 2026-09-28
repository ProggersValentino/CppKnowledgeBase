Variables in CMake, like any other variable, allow to create and store different data types using the [set() function](set()) to be used in other CMakeLists.

The general recommendation for laying out variables is to define them in the highest level of CMakeLists file before using them in the subdirectories.