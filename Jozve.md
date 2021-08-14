


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
   
- [x]  Checking the process ids
    - [x]  code
	    ```
	    #include <stdio.h>
		#include <pthread.h>
		void *printHello(void *threadid) {
		    printf("Hello from pthread ID - %lu\n", pthread_self());
		    return NULL;
		}

		int main()
		{
		    /*creating thread id*/
		    pthread_t id;
		    int ret;
		  
		    /*creating thread*/
		    ret = pthread_create (&id,NULL,printHello,NULL);
		    if(ret==0){
		        printf("Thread created successfully.\n");
		    }
		    else{
		        printf("Thread not created.\n");
		        return 0; /*return from main*/
		    }
		    
		    void *retval;
		    ret = pthread_join(id, &retval);
		    if (retval == PTHREAD_CANCELED)
		            printf("The thread was canceled - \n");
		    else
		    	printf("Returned value %d - \n", (int)retval);

		    printf("Hello from pthread ID - %lu\n", pthread_self());
		     
		    return 0;
		}
	    ```
    - [x]  screenshot of execution:
![thread-id](https://user-images.githubusercontent.com/45392657/129453116-53c4a483-5024-457e-a45a-5fa70fb77603.png)
    - [x] your descriptions (write in English or Persian)
    At the beginning of the code a new thread is created with the function of `printHello` in which thread id is printed. Then the main thread wait until the new thread ends and then print its own thread id.

- [x]  Shared variables
    - [x] code
	    ```
	    #include <stdio.h>
		#include <pthread.h>
		  
		  
		int oslab;
		/*thread function definition*/
		void* threadFunction(void* args)
		{
		    while (1)
		    {
		        printf("I am threadFunction.\n");
		    }
		}

		void *printHello(void *threadid) {
			oslab = 100;
		    printf("Hello from pthread ID - %lu, oslab: %d\n", pthread_self(), oslab);
		    return NULL;
		}

		int main()
		{
		    /*creating thread id*/
		    pthread_t id;
		    int ret;
		  
		    /*creating thread*/
		    ret = pthread_create (&id,NULL,printHello,NULL);
		    if(ret==0){
		        printf("Thread created successfully.\n");
		    }
		    else{
		        printf("Thread not created.\n");
		        return 0; /*return from main*/
		    }
		    
		    void *retval;
		    ret = pthread_join(id, &retval);
		    if (retval == PTHREAD_CANCELED)
		            printf("The thread was canceled - \n");
		    else
		    	printf("Returned value %d - \n", (int)retval);

		    printf("Hello from pthread ID - %lu oslab: %d\n", pthread_self(), oslab);
		    oslab = 200;
		    printf("Hello from pthread ID - %lu oslab: %d\n", pthread_self(), oslab);
		    
		     
		    return 0;
		}
	    ```
    - [x] screenshot of output
![share-mem-thread](https://user-images.githubusercontent.com/45392657/129453357-d4c0ca25-f8d3-469b-ba40-ee1f9532fddc.png)
    - [x]   your descriptions (write in English or Persian) on how the variable has been changed and why
    at first the `oslab` variable is define in the outer most scope which is global and initialized to `0`. then in the new thread its value is changed to `100`, after finishing the new thread, in the main thread first we directly print the `oslab` and as it can be seen the value is `100`. This shows us that the `oslab` is share between the threads, otherwise the result would be `0`. Finally its value is changed to the `200` and again the change can be easily seen. 

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
eyJoaXN0b3J5IjpbLTc0MzE2OTU0MCwtNDAwMDcxNzMzLC0zOD
Y2MzY5ODUsOTEyMDQ3MTMzLDEyODk3MjI5NTEsMTQ3MTE4MDI0
MiwtMTQ0OTkxNDAzNywxMDY3ODQ5NTIyLC02MjYxMTUzMjksLT
k3ODc2MzA3NCwtMTk2MzkxMjkxMiwxNzAxNjAzOTAzLDE3MTc0
MzY0ODksMTA4NjE0Nzk3NiwyMTQzNzIzNzA4LDg1NTk2MTQxLC
03MzQ5ODc4MzgsNDgzMDE4MDk2LDE4Nzg5NTA3MTIsMTQ0MjAw
ODc4NV19
-->