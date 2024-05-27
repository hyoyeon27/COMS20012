# Exercises sheet: Intro to Software Security

## Questions


**1. What is a spatial memory safety violation?**
+ A spatial memory safety violation is where a program accesses memory that would not normally be accessible to it.
  
2. In the reading [article](http://www.pl-enthusiast.net/2014/07/21/memory-safety/)  by Prof. hicks, he provides a definition of memory safety as *No accesses to undefined memory*. **Later he argues that it does not cover buffer overflows. Can you explain why so?**
+ Because the memory that is being overwritten is allocated. i.e. defined, whereas the definition says that only the access to undefined memory is the problem. Obviously, this does not cover buffer overflows.
	
3. Consider the following code:  
    ```
    void main(){
    	int count=0;
    	int x;
    	char name[20];
    	int y;
    	int z;
    	printf("Enter you name..");
    	gets(name);
    	printf("your name is: %s", name);
    	return 0;
    }
    ```
    **Assume that variables are allocated on the stack in the same order as they are declared in the code, i.e. x will be near `rbp (ebp)` and z wil be near `rsp (esp)`.**

    Answer the following questions.

    	a. What memory error does this code have?
   		+ buffer overflow

 	b. What is the source of that memory error?
		+ gets()

 	c. Which variables may be corrupted by that error?
		+ count, name[20]

 	d. How can you fix that error?
		+ by using fgets() instead.


**4. Consider the following code:**
    ```
    //loop.c
    #include <stdio.h>
    int main()
    {
        int x;
        char array[200];
        for(x=0;x<=200;x++)
        {
        	array[x]='A';
        	printf("x: %d", x);
        }
        printf("Done\n");
        return 0;
    }
    ```
     **Compile the code with `gcc -m32 -fno-stack-protector loop.c -o loop32` and run it. On my machine, the code goes in an infinite loop. Can you find a probable cause for this?**
+ The loop runs 201 times, which overflows the array variable (off-by-one error). The 1 byte overflow corrupts 'x' at the end of the loop. If 'x' gets corrupted to the value less than 200, this will lead to indefinite loops.
     
**5. What is control hijacking in the context of exploitation? Explain one possible way to hijack control in the presence of stack overflow bug?**
+ Taking control of an executino of a program, enabling it to rune code by code that would normally not be taken by standard execution.
+ One way is to overwrite the return address of a functino on the stack to point to code the attacker wishes to run.


**6. What is a format string bug?** 
+ Format string is a memory bug that can lead to the contents of the stack being leaked. 
+ %n causes overwriting a memory location.  

