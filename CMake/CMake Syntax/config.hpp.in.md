this file allows you to store data in relation to the cmake project which then can be used with the source code of the C++ project. 

for instance:
```cpp
#pragma once

#include <cstdint>
#include <string_view>

static constexpr std::string_view project_name = "@PROJECT_NAME@";
static constexpr std::string_view project_version = "@PROJECT_VERSION@";

static constexpr std::int32_t project_version_major{@PROJECT_VERSION_MAJOR@};
static constexpr std::int32_t project_version_minor{@PROJECT_VERSION_MINOR@};
static constexpr std::int32_t project_version_patch{@PROJECT_VERSION_PATCH@};
```

Once a project is configured using the [configure_file()](configure_file()) function, file will output:
```cpp
#pragma once

#include <cstdint>
#include <string_view>

static constexpr std::string_view project_name = "CMake_TestProject";
static constexpr std::string_view project_version = "1.0.0";

static constexpr std::int32_t project_version_major{1};
static constexpr std::int32_t project_version_minor{0};
static constexpr std::int32_t project_version_patch{0};
```

which then allows c++ files to use those variables:
```cpp
#include "CMake_TestProject.h"
#include "src/my_lib.h"
#include "config.h"

using namespace std;

int main()
{
	Lib::PrintDumbText();

	std::cout << project_version << std::endl;
	return 0;
}
```

however this can only be done if a file location is defined for that subdirectory in the CMakeLists:
```cmake
target_include_directories(${LIBRARY_NAME} PUBLIC "../../"
"${CMAKE_BINARY_DIR}/configured_files/include" #exposing library to configure file which allows this file to use its variables
)
```

It is **recommended that the configured subdirectory** gets defined in the **highest level of CMakeLists** so that it can be used within all the other subdirectories:
![[Pasted image 20260320113229.png]]

```cmake
cmake_minimum_required (VERSION 3.8)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("CMake_TestProject" VERSION 1.0.0)

#enforcing the c++ standard version for this cmake project
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(LIBRARY_NAME Library)
set(EXECUTABLE_NAME Executable)

option(COMPILE_EXECUTABLE "Whether to compile the executable" OFF)

# Include sub-projects.
add_subdirectory("configured")

#...
```