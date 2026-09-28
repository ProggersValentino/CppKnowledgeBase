a generator is a type of build system that cmake executes under the hood which has a list of commands that specify how to build our cmake project.

To get a list of them:
```cpp
cmake --help
```

We can customize which generator at the configure stage that will **override the selected on in the preset file** where we're building by:

```cpp
cmake -S <source-location (the root of the project)> -B <build-location> -G "Generator name"
```

