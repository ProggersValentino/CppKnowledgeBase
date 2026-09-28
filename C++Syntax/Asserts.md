[cpplearn](https://www.learncpp.com/cpp-tutorial/assert-and-static_assert/)

asserts and static asserts provide a way to test conditions and establish more elaborate error msg'ing throughout the code base:

```cpp
#include <casserts>
bool something = false;

//using assert from casserts library, we are able to provide a test condition we want to evaluate
assert(something && "something wasn't true")

//assert evaluated at compile time
static_assert(something && "something failed test")

```

`assert()` is evaluated at **runtime** 
`static_assert()` is evaluated at **compile time**

as you can see `static_assert()` is a keyword that doesn't require a 3rd party library to use 

when using `asserts` are only executed on **debug builds** and will get phased out at compile time for **release builds** allowing you to use them as much as possible without fear of bloating production code.

**NOTE:** you should only use assertions for conditions that should **never occur** so that when that condition does occur you can fix it easily
