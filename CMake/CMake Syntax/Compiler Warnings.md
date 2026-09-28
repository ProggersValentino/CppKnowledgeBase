ref: [microslop docs -> MSVC compiler warnings cmake](https://learn.microsoft.com/en-us/cpp/build/reference/compiler-option-warning-level?view=msvc-170)

to activate compiler warnings for your project you'll need to make a .cmake file with a script that activates the warnings for each compiler 

there are 3 different target compile functions to use to customize how the compiler will behave.

target_compile_options for creating general compile flags

target_compile_features for activating or changing core features like c++ version

target_compile_definitions for when we MACRO functions/variables to which then they need to be defined to cmake so it can properly build otherwise it will error