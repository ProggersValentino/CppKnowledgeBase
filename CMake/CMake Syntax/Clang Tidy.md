ref: [VS Clang tidy](https://learn.microsoft.com/en-us/cpp/code-quality/clang-tidy?view=msvc-170), [clang tidy docs](https://clang.llvm.org/extra/clang-tidy/index.html)


clang tidy is a linter tool designed to provide warnings and errors of the code its analyzing based on checks activated like style violations, interface misuse, or bugs that can be deduced via static analysis.


To setup in a Cmake project for linux you'll need a .clang-tidy file which configures what checks you want clang-tidy to do:
```cmake
---
Checks: 'clang-analyzer-*,cppcoreguidelines-*,modernize-*,bugprone-*,performance-*, 
readability-non-const-parameter,misc-const-correctness, misc-use-anonymous-namespace,google-explicit-constructor,
-modernize-use-trailing-return-type,-bugprone-exception-escape,-cppcoreguidelines-pro-bounds-constant-array-index,
-cppcoreguidelines-avoid-magic-numbers,-bugprone-easily-swappable-parameters'
WarningsAsErrors: ''
HeaderFilterRegex: '\(CMake_TestProject)\/*.\(h|hpp)'
AnalyzeTemporaryDtors: false
FormatStyle: none
...
```

otherwise if you're on windows you'll need to activate two options and set the specific checks in the preset file:

```JSON
{
  "configurations": [
  {
    "name": "x64-debug",
    "generator": "Ninja",
    ....
   "clangTidyChecks": "llvm-include-order, -modernize-use-override",
   "enableMicrosoftCodeAnalysis": true,
   "enableClangTidyCodeAnalysis": true
  }
  ]
}
```

#### Extra Args
you can also add extra arguments from the [clang command line](https://clang.llvm.org/docs/ClangCommandLineReference.html) to apply your clang-tidy which is done in this format:
```cmake
ExtraArgs:
- '<name of argument 1>'
- '<name of argument 2>'

```

which leaves you with a file like:

```cmake
Checks: '<name of check>'
WarningsAsErrors: ''
HeaderFilterRegex: '<regex pattern>'
ExtraArgs: 
	- '-Wno-unused-command-line-argument'
	- '-EHsc'
FormatStyle:	none
```