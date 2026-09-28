
### ```CMAKE_SOURCE_DIR```
points to the topmost folder (source directory) that contains a CMakeLists.txt

for instance:
![[Pasted image 20260324144034.png]]

CMAKE_SOURCE_DIR would be: CMake_TestProject/

### ```PROJECT_SOURCE_DIR```
Contains the full path to the root of your project source directory. Essentially where the first instance of ```project()``` is recorded in a CMakeList.txt

### ```CMAKE_CURRENT_SOURCE_DIR```
The directory where the currently processed CMakeLists.txt is located in

### ```CMAKE_CURRENT_LIST_DIR```
The directory of the listfile currently being processed 

for instance a .cmake Module

### ```CMAKE_MODULE_PATH```
Tell CMake to search first in directories listed in CMAKE_MODULE_PATH when you use FIND_PACKAGE() or INCLUDE()

### ```CMAKE_BINARY_DIR```
the filepath to the build directory 