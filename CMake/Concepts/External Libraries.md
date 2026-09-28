
during the lifetime of the project you may need to use to external libraries to move the project along. 

generally we should add a dedicated subdirectory for external libraries

In cmake there are two ways to achieve and implement this.
### Git submodule
we can use git to create a reference to a git project we want to use within our project called a submodule. this is generally used if the project is it is not a cmake project otherwise generally fetch is used but you can still use git submodule for cmake projects.

to do this we need into initialize git on the project through:
```bash 
git init
```

then from there we copy a URL of a git repo and add it to the project:

```bash
cd <root>

mkdir external

git submodule add https://github.com/nlohmann/json external/json
```

you can make a cmake file function that can template and execute commands when called in a CMakeList file:

```cmake 
function(add_git_submodule dir)
	find_package(Git REQUIRED)

	if(NOT EXISTS ${CMAKE_SOURCE_DIR}/{dir}/CMakeLists.txt)
		execute_process(COMMAND ${GIT_EXECUTABLE}
		submodule update --init --recursive -- ${CMAKE_SOURCE_DIR}/${dir} WORKING_DIRECTORY ${PROJECT_SOURCE_DIR})
	endif()

	if(EXISTS ${CMAKE_SOURCE_DIR}/${dir}/CMakeLists.txt)
		add_subdirectory(${CMAKE_SOURCE_DIR}/${dir})
	endif()
	

endfunction(add_git_submodule)
```

CMakeList.txt:
```cmake 
set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake/")
include(AddGitSubmodule)

add_git_submodule(external/json)
```

**NOTE:** when making the function, you should do ```--recursive``` as if that library has submodules within it, it will not properly add them as the library is a reference to a git project **NOT a clone of it**
### Fetch Content
ref: [[FetchContent Module]]

Fetch Content does the same thing as git submodule with the added benefit of not need to create a cmake file to template a bash command. However, this **CAN ONLY BE USED** for **cmake git projects**.

for instance, if the git repo is a cmake project then we can do:
```cmake
include(FetchContent)

FetchContent_Declare(
	nlohmann_json
	GIT_REPOSITORY https://github.com/nlohmann/json
	GIT_TAG  v3.12.0
	GIT_SHALLOW TRUE

)
FetchContent_MakeAvailable(nlohmann_json)
```

which will then, when configured, add these folders to the project allowing you to access the library:
![[Pasted image 20260323144450.png|196]]

to be able to use and include the library within c++ files you need to include within the CMakeList ```
``` ```<project_name::library_name>``` when target_linking the external libraries to the c++ files for instance:
```CMake
target_link_libraries(${EXECUTABLE_NAME} PUBLIC 
Library
nlohmann_json::nlohmann_json
spdlog::spdlog
cxxopts::cxxopts)
```

which then you'll be able to include the libraries safely within c++ files:
```cpp
#include <nlohmann/json.hpp>
#include <spdlog/spdlog.h>
#include <cxxopts.hpp>

int main()
{
	std::cout << "JSON LIB VERSION: "
		<< NLOHMANN_JSON_VERSION_MAJOR << "."
		<< NLOHMANN_JSON_VERSION_MINOR << "."
		<< NLOHMANN_JSON_VERSION_PATCH << std::endl;

	std::cout << "CXXOPTS: "
		<< CXXOPTS__VERSION_MAJOR << "."
		<< CXXOPTS__VERSION_MINOR << "."
		<< CXXOPTS__VERSION_PATCH << std::endl;

	std::cout << "SPDLOG: "
		<< SPDLOG_VER_MAJOR << "."
		<< SPDLOG_VER_MINOR << "."
		<< SPDLOG_VER_PATCH << std::endl;
	return 0;
}

```

### CPM 
ref: [CPM repo](https://github.com/cpm-cmake/cpm.cmake)

CPM is package manage that simplifies adding external libraries to your cmake project through a single line by running FetchContent under the hood 

```cmake 
include(CPM)

CPMADDPACKAGE("<importing from>: <github username>/<library name>#v<version number>")
```

### Conan Package Manager
ref: 


### VCPKG
ref:

VCPKG is microsofts in house package installer which supports cmake.
first you got to clone the project onto your cmake project:
```bash 
git clone https://github.com/microsoft/vcpkg.git
```

once the VCPKG has been cloned onto your cmake project, you then need to execute this line:
for windows:
```bash
cd vcpkg; 
.\bootstrap-vcpkg.bat
```

for linux:
```bash
cd vcpkg; 
.\bootstrap-vcpkg.sh
```