ref: [cmake docs -> toolchains](https://cmake.org/cmake/help/latest/manual/cmake-toolchains.7.html)

Toolchains in cmake allow you to cross compile across different systems.

This is done through having a .cmake file that outlines the minimum variables set for the desired compiler to compile. 

Once done you would typically use ```-DCMAKE_TOOLCHAIN_FILE``` variable and set it to the .cmake toolchain file you desire. 

You could also set this value in the [presets .JSON](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#toolchainFile:~:text=%22set%22.-,toolchainFile,-An%20optional%20string) file making it a bit more easier to set up.

