ref: [cmake docs -> cmake_parse_arguments](https://cmake.org/cmake/help/latest/command/cmake_parse_arguments.html)

allows to format a set of arguments given a MACRO or function in cmake.

```cmake
cmake_parse_arguments(<prefix> <options> <one_value_keywords>
                      <multi_value_keywords> <args>...)
```

for instance, say you have a function that outlines warnings for the code base during compile time which then you have some input variables to determine how its going to run like what target is it going to apply to, do you want enable it? 

so instead of this:

```cmake 
#.cmake file
function(target_warnings TARGET ENABLE)
#code here...
endfunction()
#------------------
#CMakeLists

target_warnings(${targetname} ${enable})

#------------------

```

we instead can do something like this:
```cmake 
function(target_warnings)
oneValueArgs(TARGET ENABLE)

cmake_parse_arguments(
	WARNINGS
	"${options}"
	"${oneValueArgs}"
	"${multiValueArgs}"
${ARGN})

#code here...
endfunction()
```

```cmake
target_warnings(
	TARGET
	${targetName}
	ENABLE
	${enable_name}
)
```

this makes it alot more readable with whats going on.

furthermore, if you want to use the targets throughout the function then you must use the **prefix defined** at the start of the parse arguments to use the value of the variable.
```cmake
function(target_warnings)
oneValueArgs(TARGET ENABLE)

cmake_parse_arguments(
	WARNINGS
	"${options}"
	"${oneValueArgs}"
	"${multiValueArgs}"
${ARGN})


if(WARNINGS_ENABLE)
	message(STATUS "warnings enabled for this cycle")
endif()

#code here...
endfunction()
```
