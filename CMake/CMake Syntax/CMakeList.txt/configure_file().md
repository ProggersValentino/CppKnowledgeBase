ref: [cmake docs -> configure_file](https://cmake.org/cmake/help/latest/command/configure_file.html)

Copies the [input file given](config.hpp.in) into an output location performing value replacement ([transformations](https://cmake.org/cmake/help/latest/command/configure_file.html#transformations)) of all values thats defined with @@ 

for instance take this config.hpp.in:
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

which then after the configure file function is performed during the configuration step of cmake, it will output to this:
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