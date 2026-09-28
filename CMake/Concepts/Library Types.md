
A library is a compiled set of software with a set of tools that executables can use throughout the program. 

There are two types of libraries which are either **SHARED** or **STATIC**

#### Shared 

OS postfix:
- Windows: **.dll** 
- Linux: **.so**
- Macos: **.dylib**

Shared libraries reduce the size of code that is needed throughout the application by only instantiating that particular file when certain methods or classes are invoked throughout the program. It does mean that its accessible through runtime only  

##### Testing
if you need to test functions within a shared library then you **must** copy the built library to your **tests directory** so that the unit test can access the functions for instance:
```
add_custom_command(
	TARGET ${TARGET}
	PRE_LINK
	COMMAND ${CMAKE_COMMAND}
	ARGS -E copy $<TARGET_FILE:${FILE_TO_COPY}> $<TARGET_FILE_DIR:${TARGET}>
)
```

#### Static

OS Postfix:
- Windows: **.lib**
- Linux/Macos: **.a**

Static libraries are libraries where everything is compiled and can be accessed statically outside of runtime, however it does increase the overall size of the library 