ref: [cmake docs -> find_package()](https://cmake.org/cmake/help/latest/command/find_package.html), [cmake docs -> dependency guide](https://cmake.org/cmake/help/latest/guide/using-dependencies/index.html#using-pre-built-packages-with-find-package)

whether an external package can be found 

```cmake
find_package(<PackageName> [<version>] [REQUIRED] [COMPONENTS <components>...])
```

for instance, say you need to check if the user have the python package to do a custom command with it:

```cmake 
find_package(Python3 COMPONENTS Interpreter)
```

there are [interface variables](https://cmake.org/cmake/help/latest/command/find_package.html#package-file-interface-variables) which provides the user values to use in situations that need certain values to determine a valid condition:

```cmake
if(Python3_FOUND)
	#do code
endif()
```