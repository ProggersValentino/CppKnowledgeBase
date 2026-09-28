
full error:
```
error: unknown argument ignored in clang-cl: '-fexceptions'
```

This issue is caused when you use a clang command line option while using the msvc compiler

#### Solution
use the alternative that is supported for the msvc compiler like in this instance using ```-EHsc``` instead of the ```-fexceptions```

