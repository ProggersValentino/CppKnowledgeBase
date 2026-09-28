ref: [explaination to why](https://github.com/llvm/llvm-project/issues/53778)

if you try to run:
```bash
clang-tidy path/to/file --
```

then you could be met with this error:
```cmake
Stack dump:  
0. Program arguments: "C:\\Program Files\\Microsoft Visual Studio\\2022\\Community\\VC\\Tools\\Llvm\\bin\\clang-tidy.exe" lib/packetlib/PacketSerialization.cpp --  
Exception Code: 0xC0000005  
#0 0x01220e60 (C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Tools\Llvm\bin\clang-tidy.exe+0x770e60)  
#1 0x77d71b01 (C:\WINDOWS\SYSTEM32\ntdll.dll+0x81b01)  
#2 0x00f4522e (C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Tools\Llvm\bin\clang-tidy.exe+0x49522e)  
#3 0xc8000000  
#4 0xe8046c65  
#5 0xe8046c65  
#6 0x00046c65  
#7 0x42000000  
#8 0x006ec6f1  
#9 0xd4880079  
#10 0x0103174e (C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Tools\Llvm\bin\clang-tidy.exe+0x58174e)
```

This only occurs if the option ```modernize-use-nullptr``` is enabled in the clang-tidy checks while activating clang-tidy on the x86 architecture causing it to error

### Solution
take out ```modernize-use-nullptr``` from the options clang-tidy uses

**OR**

switch to using the x64 clang-tidy by setting a new location for where clang-tidy should be executed for instance: 

```json
"configurePresets": [
    {
		//...
        "cacheVariables": {
            "CMAKE_CXX_CLANG_TIDY":  "C:\\Program Files\\Microsoft Visual Studio\\2022\\Community\\VC\\Tools\\Llvm\\x64\\bin\\clang-tidy.exe"
        },
        ...
    },
```