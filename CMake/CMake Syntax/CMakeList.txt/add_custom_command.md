ref: [cmake docs -> add_custom_command](https://cmake.org/cmake/help/latest/command/add_custom_command.html), [cmake docs -> CMAKE_COMMAND](https://cmake.org/cmake/help/latest/manual/cmake.1.html#manual:cmake(1))
custom commands allow you to execute commands during the build. 
This can be used to either generate new files:

```cmake
add_custom_command([OUTPUT](https://cmake.org/cmake/help/latest/command/add_custom_command.html#output) <output1> [<output2> ...]
                     COMMAND <command1> [ARGS] [<args1>...]
                     [...])
```

OR used to create custom build events **linked to a specified target** that are executed during the build

```
add_custom_command([TARGET](https://cmake.org/cmake/help/latest/command/add_custom_command.html#target) <target>
                     PRE_BUILD | PRE_LINK | POST_BUILD
                     [...])
```

#### Copy a file
if you want to copy a file to a location then you must do ```-E copy <file>...<destination>```