refs: [cmake docs -> find_library](https://cmake.org/cmake/help/latest/command/find_library.html)

When you need to know if the a built library is there you can use:
```
find_library (<VAR> <name> [<path>...])
```

so say i need to determine if a library I supplied exists then you word do:
```cpp
find_library("SocketLib" ${<target name>})
```