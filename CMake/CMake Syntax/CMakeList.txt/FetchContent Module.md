ref: [cmake docs -> FetchContent()](https://cmake.org/cmake/help/latest/module/FetchContent.html)

A module that enables populating content at configure time which includes using external libraries. This supports all methods outlined in the [ExternalProject Module](https://cmake.org/cmake/help/latest/module/ExternalProject.html#externalproject) just that it makes the content accessible at configure time compared to during build time.

#### ```FetchContent_Declare()```

Define an external library to use within the project which **MUST** be a cmake project, else it will throw an error

```cpp
FetchContent_Declare(
  <name>
  <contentOptions>...
  [EXCLUDE_FROM_ALL]
  [SYSTEM]
  [OVERRIDE_FIND_PACKAGE |
   FIND_PACKAGE_ARGS args...]
)
```

for instance, we want to get the nlohmann_json library so we would do:
```cmake 
FetchContent_Declare(
	nlohmann_json
	GIT_REPOSITORY https://github.com/nlohmann/json
	GIT_TAG  v3.12.0
	GIT_SHALLOW TRUE

)
```


#### ```FetchContent_MakeAvailable()```
Given the libraries that have been declared, make the libraries available to use within the cmake project for c++ (or other supported languages) files. the name parsed through **MUST** be the **project's name**

for instance, once you have declared the external library nlohmann_json, you then make it available to your project:
```
FetchContent_MakeAvailable(nlohmann_json)
```

to which then in the cpp:
```cpp
#include <nlohmann/json.hpp>

int main()
{
	std::cout << "JSON LIB VERSION: "
		<< NLOHMANN_JSON_VERSION_MAJOR << "."
		<< NLOHMANN_JSON_VERSION_MINOR << "."
		<< NLOHMANN_JSON_VERSION_PATCH << std::endl;
	return 0;
}
```

