A makefile contains a set of commands to execute which can be organised into subsets allowing to create custom commands for the terminal when trying to build. This can **only be executed if you have cd into the directory with a valid makefile**. 

```bash
prepare:
	rm -rf out/build
	mkdir out/build
	cd out/build
```

which can be executed with the command:

```bash
make 
```
 or
 ```bash
 make <name of subset>
 ```
 if you want to execute a specific set of commands 

**PERSONAL NOTE:** you **CANNOT** use spaces in makefiles, you **MUST** tab for whitespace