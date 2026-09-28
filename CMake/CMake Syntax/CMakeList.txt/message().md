ref: [cmake docs -> message()](https://cmake.org/cmake/help/latest/command/message.html)

prints a message log within the console 

for instance if I want to print a status message to display what part of the build process is getting executed then:
```cmake
message(STATUS "Initializing Test stage of build")
```

the message has many modes that it can defer from status to sending an error to stop the build entirely

