## Setup
#### Compile program with -g to enable debug support 
``` gcc -g -o main foo.c ```
#### Start GDB with program loaded 
```
 gdb ./main 
 gdb main
 gdb a.out 
```
### Start GDB with program loaded + command line args 
```
gdb --args main arg1 arg2 arg 3
```
#### Start GDB plain then load program 
``` 
gdb
file ./main 
```
#### Run/Restart program 
```r``` or ```run```  
#### Repeat previous command 
`EnterKey`

## Breakpoints 
#### Set Breakpoint for file at line #
``` break fileName:#  ```  or  ```  b fileName:#```
#### Set Breakpoint on a C function 
``` break func1 ```
#### Set Breakpoint on a C++ function 
``` break TestClass::testFunc(int) ```
#### Conditional Breakpoint 
`break sample.c:17 if i==113 //gdb stop at line 17 if i happens to be 113`

`break sample.cpp:17 if ((int)strcmp(variable,"hello")) == 0 //if variable == "hello"`

`break sample.cpp:17 if x == ((void*) 0) //Check for NULL pointer `
#### List All Breakpoints 
``` info b ```
#### Delete Breakpoint # 
``` delete # ```
#### Clear All Breakpoints 
``` clear ```
#### Disable Breakpoint 
``` disable # ```
## Location/Watch/Print
#### Where you at?
``` where ```
#### What frame you at ? 
``` frame ```
#### Set variable 
`set var varName=Value`
#### Print variable value 
`print foo` or `p foo`
#### Print variable value in hex
`print/x foo `
#### Watch variable 
`watch foo`

## Controls 
#### Continue to next breakpoint 
`c` or `continue`
#### Step Into (will step into function)
`s` or `step`
#### Next (next line but don't dive into function)
`n` or `next`
#### Return from function 
`fin` or `finish`

## Etc 
#### Print StackCalls that lead to seg fault 
``` backtrace ```
#### Clearn GDB screen 
``` Control + L ```