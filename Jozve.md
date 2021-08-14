



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

- [x] Sum of 2 to n
    1. [x] code
	    ```
		#include <stdio.h>
		#include <pthread.h>
		  
		void *printHello(void *num) {
			int number = *((int *) num);
			int sum = 0;
			for (int i=2; i <= number; i++) {
				sum += i;
			}
			printf("the sum: %d\n", sum);
		}

		int main()
		{
		    int inp;
		    scanf("%d", &inp);
		    /*creating thread id*/
		    pthread_t id;
		    pthread_attr_t attr;
		    pthread_attr_init(&attr);
		    int ret;
		    /*creating thread*/
		    ret = pthread_create (&id, &attr, &printHello, &inp);
		    if(ret==0){
		        printf("Thread created successfully.\n");
		    }
		    else{
		        printf("Thread not created.\n");
		        return 0; /*return from main*/
		    }
		    
		    void *retval;
		    ret = pthread_join(id, &retval);     
		    pthread_exit(0);
		    return 0;
		}
		```
    3. [x] screenshot of an execution of the code for n=(mean of team's student numbers = 97103570)
![1n](https://user-images.githubusercontent.com/45392657/129455035-7f5ce713-2950-4bd1-b2fd-cc6e64ec3577.png)


### Section 7.4.2
- [x] Multiple threads    
    - [x] code
	    ```
		#include <stdio.h>
		#include <stdlib.h>
		#include <pthread.h>
		#include <unistd.h>
		#include <errno.h>

		#ifndef NUM_THREADS
		#define NUM_THREADS 9
		#endif

		void *printHello(void *threadid) {
		    long tid;
		    tid = (long)threadid;
		    printf("Hello world from thread %ld, pthread ID - %lu\n", tid, pthread_self());
		    return NULL;
		}


		int main(int argc, char const *argv[]) {
		    pthread_t threads[NUM_THREADS];
		    int rc;
		    long t;

		    for (t = 0; t < NUM_THREADS; t++) {
		        rc = pthread_create(&threads[t], NULL, printHello, (void *)t);
		        if (rc) {
		            printf("ERORR; return code from pthread_create() is %d\n", rc);
		            exit(EXIT_FAILURE);
		        }
		    }

		    int ret;
		    for (t = 0; t < NUM_THREADS; t++) {
		        void *retval;
		        ret = pthread_join(threads[t], &retval);
		    }
		    pthread_exit(NULL);
		}

		```
    - [x] screenshot of execution of code
![multi-thread](https://user-images.githubusercontent.com/45392657/129455141-10eb6a32-cb21-4232-8500-5084472152ce.png)


### Section 7.4.3
- [x] Compiling the code
    - [x] screenshot of compilation
![compile](https://user-images.githubusercontent.com/45392657/129455312-d296d7f7-1b2f-4add-bb00-ee03864a62f6.png)

- [x] global_param
    - [x]  code
    - [ ] `FILL HERE with screenshot of output`

- [ ] Forking
    - [ ] `FILL HERE with screenshot of code`
    - [ ] `FILL HERE with screenshot of output`
### Section 7.4.4
- [ ] Passing multiple variables
    - [ ] `FILL HERE with screenshot of code`
    - [ ] `FILL HERE with screenshot of output`

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA5ODc0Njg0NywtMzUyMzA3ODcwLC0xMD
Q2OTYwMjYwLC00MDAwNzE3MzMsLTM4NjYzNjk4NSw5MTIwNDcx
MzMsMTI4OTcyMjk1MSwxNDcxMTgwMjQyLC0xNDQ5OTE0MDM3LD
EwNjc4NDk1MjIsLTYyNjExNTMyOSwtOTc4NzYzMDc0LC0xOTYz
OTEyOTEyLDE3MDE2MDM5MDMsMTcxNzQzNjQ4OSwxMDg2MTQ3OT
c2LDIxNDM3MjM3MDgsODU1OTYxNDEsLTczNDk4NzgzOCw0ODMw
MTgwOTZdfQ==
-->