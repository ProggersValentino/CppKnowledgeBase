ref: [cmake docs -> find_program()](https://cmake.org/cmake/help/latest/command/find_program.html)

finds the requested program 
```cmake
find_program (<VAR> <name> [<path>...])
```

if the VAR **is not defined** then cmake will execute the function else it will do nothing

for instance, you want to integrate clang-tidy within the project then you would:
```cmake
find_program(CLANGTIDY clang-tidy)
```