ref:[cmake docs -> CPM0069](https://cmake.org/cmake/help/latest/policy/CMP0069.html)

this error happens if you're using CMAKE version 3.8 or below where to enable LTO was built into each target. now with Cmake version 3.9 and above, you need to do this to enable LTO:

```cmake 
cmake_minimum_required(VERSION 3.9) # CMP0069 NEW
project(foo)

include(CheckIPOSupported)
check_ipo_supported()

# ...

set_property(TARGET ... PROPERTY INTERPROCEDURAL_OPTIMIZATION TRUE)
```

compared to the old way:
```cmake
cmake_minimum_required(VERSION 3.8)
project(foo)

# ...

set_property(TARGET ... PROPERTY INTERPROCEDURAL_OPTIMIZATION TRUE)
```