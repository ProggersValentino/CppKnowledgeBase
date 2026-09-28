ref: [error explaination](https://maskray.me/blog/2023-08-25-clang-wunused-command-line-argument), [solution](https://github.com/xmake-io/xmake/issues/2811) 

full error:
```
error: argument unused during compilation: '-ZI' [clang-diagnostic-unused-command-line-argument]
```
#### Solution
disable unused-command-line-arguments in your .clang-tidy file by adding the extra arg: 
```
-Wno-unused-command-line-argument
```
