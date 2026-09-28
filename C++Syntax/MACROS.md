ref: [cpplearn preprocessor](https://www.learncpp.com/cpp-tutorial/introduction-to-the-preprocessor/)

MACROS are rules that define how inputted text is converted into replacement output text. these provide ways to give numbers meaningful names and other functionality like making functions: 
``` c++
#define ERRORCODE 4

#define MAX(min, max) DetermineMinMax(min, max)
```

this is powerful as it uses the preprocessor to evaluate and replace the macro into the output text before its compiled. 

This can also be used as an assistance to [defensive programming](https://khmerbamboo.wordpress.com/wp-content/uploads/2014/09/code-complete-2nd-edition-v413hav.pdf) where if you need debug functions but dont want to slow production then you can have macros that are only available at the development stage (debug builds) which of course speed isn't much concern if it means you can catch errors and accurately fix them quicker than usual.
``` c++
#ifdef _DEBUG
#define debugLine(msg) DebugMessage(msg)
#else
#define debugLine(msg)
#endif
```

the above is fine but say we also want some fine tuning to add other more complex conditions to validate the use for a macro like debug options that turn on and off the debug. 

Well we could try and implement an if statement but the compiler wont like that. So instead we turn to a more common and safe method for integrating a more complex conditions which is the [do{ }while(0) idom](https://www.allpcb.com/allelectrohub/the-dowhile0-idiom-in-c-and-c) where you are able to fit normal coding into a macro that gets processed by the preprocessor:
``` c++
#if  defined(_DEBUG) 
	#define PRINT_SNAP(precursorMSG, snapshot) do { \
	if(packetDebugActive) { \
		std::cout << precursorMSG << std::endl; \
		Snapshot::PrintSnapshot(snapshot); \	
	}\
	}while(0)
#else
#define PRINT_SNAP(snapshot)
#endif
```

this is generally safer as it allows us to use {} to properly define to the compiler that this is a block of code to execute and not a block and another condition to execute 