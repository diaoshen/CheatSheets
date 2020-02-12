## Setup
#### Compile program with -g to enable debug support 
``` gcc -g -o main foo.c ```
#### Start GDB with program
``` gdb ./main ```
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
#### Set Breakpoint at function 
``` break function_name ```
#### Conditional Breakpoint 
`break sample.c:17 if i==113 //gdb stop at line 17 if i happens to be 113`
#### List All Breakpoints 
``` info b ```
#### Delete Breakpoint # 
``` delete # ```
#### Clear All Breakpoints 
``` clear ```

## Location/Watch/Print
#### Where you at?
``` where ```
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


## Etc 
#### Print StackCalls that lead to seg fault 
``` backtrace ```