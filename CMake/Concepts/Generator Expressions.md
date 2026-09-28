ref: [cmake docs -> generator expressions](https://cmake.org/cmake/help/latest/manual/cmake-generator-expressions.7.html)
generator expression help to customize how we want a cmake project to build depending on its build type. 

this is only if you're using a multi-config generator or windows generator like Ninja or MSVC

We can't detect through the conventional way of just putting it into a if else statement as the configuration will skip it because of the **```CMAKE_BUILD_TYPE```** property which is evaluated at build time

