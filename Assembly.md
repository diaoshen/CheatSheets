# Assembly


![RegisterImage](https://www.cs.virginia.edu/~evans/cs216/guides/x86-registers.png)

## Instruction Set 
* mov
* add
* sub
* mul
* div
* inc
* dec
## Instruction Set Details 
#### mov
`mov var1 , %eax   //copy variable var1 to %eax `  
`mov %eax , %ebx   //copy %eax to %ebx `  
`mov %eax , var1   //copy %eax to var1 `  


#### add    
`add %eax %ebx    //ebx += eax  `  
```
//Code
    c = a + b 
//Assembly
    mov a , %ebx 
    add b , %ebx
    mov %ebx , c
```

#### sub 
`sub %eax %ebx  //%ebx -= %eax`
```
//Code 
    c = b - a
//Assembly 
    mov b %ebx 
    sub a %ebx 
    mov %ebx c 
```

#### mul 
` mul arg  //$eax *= arg `
> Note : If result overflow, overflow is stored in d register  
```
//Code 
    c = a * b 
//Assembly 
    mov a %eax 
    mul b 
    mov %eax c 
```

