ref: [cmake docs -> list()](https://cmake.org/cmake/help/latest/command/list.html)

like the set command, list creates new variables in the current scope but has the added ability to apply subcommands to **manipulate/add/delete** data within [[set()]] variables. 

This works off the basis of [Cmake's list syntax](https://cmake.org/cmake/help/latest/manual/cmake-language.7.html#cmake-language-lists) where it separates and defined new values from whitespace or if within ```""``` then by the ```;``` 

