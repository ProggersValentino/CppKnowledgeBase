
for general commands type:
```bash
cmake --help
```

To configure you can cd into the location where the cmake should build to or define the absolute location in the below command:
```bash
cmake -S <source-location (the root of the project)> -B <build-location>
```

or if you want to modify the generator used:
```bash
cmake -S <source-location (the root of the project)> -B <build-location> -G "Generator name"
```

after that, if you update the project and want to build you can update the generated project by inputting: 

``` bash
cd <absolute location>
cmake .
```

if you want to adjust options then:
```bash
cmake -S ../../ -B . -D <option name>=<value> --preset <preset name>
```

### ``` cmake --build ```
the build command allows you to build the whole project only if its previously gone through a build. 

```bash
cmake --build .
```

#### Specifying a target
If you don't want to rebuilt the whole of the project because you have a dozen or so libraries that would need to be rebuilt and therefore take a lot of time you add the ```--target``` to the cmake build command to specify a single or few targets to rebuild:

```bash
cmake --build . --target <insert target file>
```

OR if you're on linux or mac then you can create a make command to do the same thing as the command above
### ```make```
the make command can only be done if you have a valid makefile. 
```bash
make
```

