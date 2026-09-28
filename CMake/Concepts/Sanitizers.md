ref: [gcc sanitizers](https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html#index-fsanitize_003daddress), [msvc sanitizers](https://learn.microsoft.com/en-us/cpp/build/reference/fsanitize?view=msvc-170) 

tools that will help detect errors on runtime, generally use [[add_compile_options]] to add said tools to the compiler for the project so that when compiling it will apply these options to all targets.

for instance when we have an overflow error:
```cpp
int pp[2];
pp[2] = 2322
```

the **compiler warnings will not pick it up** and when we run the project it will run and then terminate with a very vague error message, however when we activate the sanitizers on a compiler and try running the executable we will get this:

```powershell
/mnt/c/ApplicationProjects/CMake_TestProject/CMake_TestProject/CMake_TestProject.cpp:16:5: runtime error: index 2 out of bounds for type 'int [2]'  
/mnt/c/ApplicationProjects/CMake_TestProject/CMake_TestProject/CMake_TestProject.cpp:16:7: runtime error: store to address 0x741a89c00028 with insufficient space for an object of type 'int'  
0x741a89c00028: note: pointer points here  
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 80 bf 89 1a 74 00 00 00 00 00 00  
^  
=================================================================  
==5636==ERROR: AddressSanitizer: stack-buffer-overflow on address 0x741a89c00028 at pc 0x63011d29c45a bp 0x7ffd9f5b74a0 sp 0x7ffd9f5b7490  
WRITE of size 4 at 0x741a89c00028 thread T0  
#0 0x63011d29c459 in main /mnt/c/ApplicationProjects/CMake_TestProject/CMake_TestProject/CMake_TestProject.cpp:16  
#1 0x741a8bc2a1c9 in __libc_start_call_main ../sysdeps/nptl/libc_start_call_main.h:58  
#2 0x741a8bc2a28a in __libc_start_main_impl ../csu/libc-start.c:360  
#3 0x63011d2996c4 in _start (/mnt/c/ApplicationProjects/CMake_TestProject/out/build/CMake_TestProject/Executable+0x1b6c4) (BuildId: 71e8c1b373b82ea4b920e4eb60cf2c9ca10a0060)  
  
Address 0x741a89c00028 is located in stack of thread T0 at offset 40 in frame  
#0 0x63011d29c351 in main /mnt/c/ApplicationProjects/CMake_TestProject/CMake_TestProject/CMake_TestProject.cpp:12  
  
This frame has 1 object(s):  
[32, 40) 'x' (line 15) <== Memory access at offset 40 overflows this variable  
HINT: this may be a false positive if your program uses some custom stack unwind mechanism, swapcontext or vfork  
(longjmp and C++ exceptions *are* supported)  
SUMMARY: AddressSanitizer: stack-buffer-overflow /mnt/c/ApplicationProjects/CMake_TestProject/CMake_TestProject/CMake_TestProject.cpp:16 in main  
Shadow bytes around the buggy address:  
0x741a89bffd80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
0x741a89bffe00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
0x741a89bffe80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
0x741a89bfff00: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
0x741a89bfff80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
=>0x741a89c00000: f1 f1 f1 f1 00[f3]f3 f3 00 00 00 00 00 00 00 00  
0x741a89c00080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
0x741a89c00100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
0x741a89c00180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
0x741a89c00200: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
0x741a89c00280: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
Shadow byte legend (one shadow byte represents 8 application bytes):  
Addressable: 00  
Partially addressable: 01 02 03 04 05 06 07  
Heap left redzone: fa  
Freed heap region: fd  
Stack left redzone: f1  
Stack mid redzone: f2  
Stack right redzone: f3  
Stack after return: f5  
Stack use after scope: f8  
Global redzone: f9  
Global init order: f6  
Poisoned by user: f7  
Container overflow: fc  
Array cookie: ac  
Intra object redzone: bb  
ASan internal: fe  
Left alloca redzone: ca  
Right alloca redzone: cb  
==5636==ABORTING
```


providing alot more information about what has happened 