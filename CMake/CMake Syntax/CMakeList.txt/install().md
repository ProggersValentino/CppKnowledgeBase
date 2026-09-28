ref: [cmake docs -> install()](https://cmake.org/cmake/help/latest/command/install.html)

a command that installs and packages the desired generated executables/libraries on the user's local machine

```cmake 
install(TARGETS <target>... [EXPORT <export-name>]
        [RUNTIME_DEPENDENCIES <arg>...|RUNTIME_DEPENDENCY_SET <set-name>]
        [<artifact-option>...]
        [<artifact-kind> <artifact-option>...]...
        [INCLUDES DESTINATION [<dir> ...]]
        )
```

