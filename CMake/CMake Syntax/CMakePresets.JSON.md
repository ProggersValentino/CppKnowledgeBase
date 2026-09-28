ref: [microslop -> configuring CMake Presets](https://learn.microsoft.com/en-us/cpp/build/cmake-presets-vs?view=msvc-170#enable-cmakepresets-json-integration), [CMake Docs -> Presets](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#id1) 

this is where you define how you want to build c++ project.

this is layed out in a JSON format, for instance:
```JSON 
 {
     "name": "linux-debug",
     "displayName": "Linux Debug",
     "generator": "Ninja",
     "binaryDir": "${sourceDir}/out/build/${presetName}",
     "installDir": "${sourceDir}/out/install/${presetName}",
     "cacheVariables": {
         "CMAKE_BUILD_TYPE": "Debug"
     },
     "condition": {
         "type": "equals",
         "lhs": "${hostSystemName}",
         "rhs": "Linux"
     },
     "vendor": {
         "microsoft.com/VisualStudioRemoteSettings/CMake/1.0": {
             "sourceDir": "$env{HOME}/.vs/$ms{projectDirName}"
         }
     }
 }
```

