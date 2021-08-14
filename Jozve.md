Team Name: `97101359-97105782`

Student Name of member 1: `Mohammad Sepehr Pourghannad`
Student No. of member 1: `97101359`

Student Name of member 2: `Mostafa Ojaghi`
Student No. of member 2: `97105782`

- [x] Read Session Contents.

## Section 7.4

### Section 7.4.1
- [x] Creating a thread using pthread
    - [x] screenshot of execution
    ![creating-thread](https://user-images.githubusercontent.com/45392657/129452629-a86318d0-3fe0-4f22-9808-3193b4140cce.png)
    - [x] code
	    ```
		    #include <stdio.h>
		#include <pthread.h>
		  
		/*thread function definition*/
		void* threadFunction(void* args)
		{
		    while (1)
		    {
		        printf("I am threadFunction.\n");
		    }
		}
		int main()
		{
		    /*creating thread id*/
		    pthread_t id;
		    int ret;
		  
		    /*creating thread*/
		    ret=pthread_create(&id,NULL,&threadFunction,NULL);
		    if(ret==0){
		        printf("Thread created successfully.\n");
		    }
		    else{
		        printf("Thread not created.\n");
		        return 0; /*return from main*/
		    }
		  
		    while(1)
		    {
		      printf("I am main function.\n");      
		    }
		  
		    return 0;
		}
	    ```
   
- [ ]  Checking the process ids
    - [ ] `FILL HERE with screenshot of code`
    - [ ] `FILL HERE with execution of code`
    - [ ] `FILL HERE with your descriptions (write in English or Persian)`

- [ ]  Shared variables
    - [ ] `FILL HERE with screenshot of codes`
    - [ ]  `FILL HERE with screenshot of output`
    - [ ]  `FILL HERE with your descriptions (write in English or Persian) on how the variable has been changed and why`

- [ ] Sum of 2 to n
    1. [ ] `[FILL HERE with screenshot of code]`
    1. [ ] `[FILL HERE with screenshot of an execution of the code for n=(mean of team's student numbers)]`

### Section 7.4.2
- [ ] Multiple threads    
    - [ ] `FILL HERE with screenshot of code`
    - [ ] `FILL HERE with execution of code`

### Section 7.4.3
- [ ] Compiling the code
    - [ ] `FILL HERE with screenshot of compilation`

- [ ] global_param
    - [ ] `FILL HERE with screenshot of code`
    - [ ] `FILL HERE with screenshot of output`

- [ ] Forking
    - [ ] `FILL HERE with screenshot of code`
    - [ ] `FILL HERE with screenshot of output`
### Section 7.4.4
- [ ] Passing multiple variables
    - [ ] `FILL HERE with screenshot of code`
    - [ ] `FILL HERE with screenshot of output`

<!--stackedit_data:
eyJoaXN0b3J5IjpbOTEyMDQ3MTMzLDEyODk3MjI5NTEsMTQ3MT
E4MDI0MiwtMTQ0OTkxNDAzNywxMDY3ODQ5NTIyLC02MjYxMTUz
MjksLTk3ODc2MzA3NCwtMTk2MzkxMjkxMiwxNzAxNjAzOTAzLD
E3MTc0MzY0ODksMTA4NjE0Nzk3NiwyMTQzNzIzNzA4LDg1NTk2
MTQxLC03MzQ5ODc4MzgsNDgzMDE4MDk2LDE4Nzg5NTA3MTIsMT
Q0MjAwODc4NSwxNjc4NDM2OTc2LDE0MTg4MDk4ODUsLTE5NTM4
OTQzOTFdfQ==
-->