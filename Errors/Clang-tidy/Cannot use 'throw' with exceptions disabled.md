ref: [error solution](https://stackoverflow.com/questions/75496284/clang-tidy-emits-errors-about-exceptions-being-disabled-when-the-are-enabled)

full error:
```
error: cannot use 'throw' with exceptions disabled [clang-diagnostic-error]
```

if you have a throw exception within your project while having exceptions disabled on clang, then it will throw this error.

#### Solution
depending what compiler you need to add the extra arg to your .clang-tidy file:
##### MSVC
```
-EHsc
```
##### GCC
```
-fexceptions
```

if you use ```-fexceptions``` on the msvc compiler then you will get a [[Unknown argument ignored in clang-cl '-fexceptions']] error