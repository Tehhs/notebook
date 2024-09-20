
Below is a very simple example of code that's vulnerable to a buffer overflow exploit. 

```c

#include <stdio.h>

int main() {
    char buffer[10];  

    printf("Enter a string: ");
    gets(buffer);  

    printf("You entered: %s\n", buffer);
    return 0;
}

```

Why is this a big deal? So what, you can overwrite the buffer which would probably just cause a crash. 

Buffer overflows like the one above can be used to execute remote arbitrary code. Notablity, it can be used to overwrite a function's stack frame and control structures. Examples: 
* Return address of the function 
* Function pointers and variables 

todo: Show examples of this - in like cheat engine or something
todo: show visualizations of buffer and the stackframe around it, before and after buffer overflow exploits, potentially animate it, show assembly code too 