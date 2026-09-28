Unit testing in CMake uses a CTest to create and read tests. However you can combine this with an external library that may be built for testing in a language with the addition of easier syntax and extra content to thoroughly test your code.

For instance if we want to use the library [Catch2](https://github.com/catchorg/Catch2) for testing, we can import it in using the [[FetchContent Module]] and then use it to create test cases for our code: 

```cmake
	FetchContent_Declare(
		Catch2
		GIT_REPOSITORY https://github.com/catchorg/Catch2
		GIT_TAG  v3.13.0
		GIT_SHALLOW TRUE

	)
	FetchContent_MakeAvailable(Catch2)
```

you must also make sure to add the ctest to the highest CMakeList.txt file otherwise you wont be able to use it to its full capacity:
```cmake
include(CTest)
enable_testing()
```

to which then once the set up is complete in the local CMakeLists file for the unit test cpp file, you can create test cases:
```cmake
include(Catch)

set(TEST_MAIN "unit_tests")
set(TEST_HEADERS "main.h")
set(TEST_SOURCES "main.cc")
set(TEST_INCLUDES "./")

add_executable(${TEST_MAIN} ${TEST_SOURCES} ${TEST_HEADERS})
target_include_directories(${TEST_MAIN} PUBLIC ${TEST_INCLUDES})
target_link_libraries(${TEST_MAIN} PUBLIC 
${LIBRARY_NAME}
Catch2::Catch2WithMain
)

#allows you to sync up with ctest so you dont need to call the executable everytime
CATCH_DISCOVER_TESTS(${TEST_MAIN})
```


```cpp name="unit_test main file"
#define CATCH_CONFIG_MAIN

#include <catch2/catch_test_macros.hpp>
#include "CMake_TestProject/src/my_lib.h"

TEST_CASE("Factorials are computed", "[Factorial]") {
    REQUIRE(Lib::Factorial(1) == 1);
    REQUIRE(Lib::Factorial(2) == 2);
    REQUIRE(Lib::Factorial(3) == 6);
    REQUIRE(Lib::Factorial(10) == 3'628'800);
}
```

Once then you have built the project and are cd into its location, you can do the following terminal command to activate all unit tests:
```bash
cd <build location>
 
ctest
```

or if you want to test an individual test case then you can activate the individual executable:
```bash 
cd <unit test directory location>

./<unit test executable name>
```