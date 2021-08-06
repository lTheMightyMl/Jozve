

Team Name: `97105782-97101359`

Student Name of member 1: `Mostafa Ojaghi`
Student No. of member 1: `97105782`

Student Name of member 2: `Mohammad Sepehr Pourghannad`
Student No. of member 2: `97101359`

- [x] Read Session Contents.

## Section 6.4

- [x] Using `malloc` and `free` in program
    - [x] code
    ```
	#include <stdio.h>
	#include <stdlib.h>

	struct MyStruct {
	    int a;
	    int b;
	    char name[20];
	};

	int
	main ()
	{
	  struct MyStruct *obj = malloc (sizeof(struct MyStruct));
	  obj->a = 5;
	  obj->b = 10;
	  strcpy(obj->name, "sepehr");
	  printf("the content of the strcut is: a: %d, b: %d, name: %s", obj->a, obj->b, obj->name);
	  free(obj);
	}
	```
    - [x] screenshot of execution
![malloc](https://user-images.githubusercontent.com/45392657/128445355-db388dea-2e48-44fd-89d6-8b8dc1d1a72b.png)

    
- [x]  Using `ps`
    - [x] screenshot of command output
    ![pso](https://user-images.githubusercontent.com/45392657/128445459-a57579ca-f5bd-4e1f-9d05-fa02c0ec21e0.png)
    - [x] your descriptions (write in English or Persian)
    * `vsz`: virtual memory size of the process in KiB (1024-byte units).  Device mappings are currently excluded; this is subject to change. 
    * `RSS`: resident set size, the non-swapped physical memory that a task has used (in kilobytes).
    * `%MEM`: ratio of the process's resident set size  to the physical memory on the machine, expressed as a percentage.
    * `COMMAND`: command name (only the executable name)

- [x]  Getting started with memory segments
    - [x] screenshot of which command for ls
    ![ls](https://user-images.githubusercontent.com/45392657/128446252-ab4f13b6-afeb-449b-b03c-040e49256a0b.png)
    - [x]  screenshot for size
![size](https://user-images.githubusercontent.com/45392657/128446382-a0bf4856-69dd-4ec2-9860-bf20f18376e7.png)
    - [x]  `FILL HERE with segments not shown with size`
    heap and stack
    

- [x] Getting started with memory sharing
    1. [x]  screenshot of lld for ls    
![ldd](https://user-images.githubusercontent.com/45392657/128446640-ccde56c6-ebdd-4672-885c-b3db65f4f6b5.png)
    1. [x] screenshot of lld for nano    
![nano](https://user-images.githubusercontent.com/45392657/128446717-6c06ab24-a5de-4b5c-9fba-544055d6aa80.png)
    1. [x] screenshot of lld for another program
    `ldd` for `scp`:
    
![scp](https://user-images.githubusercontent.com/45392657/128446846-bce7be55-ab98-4e03-8bcd-54cb26b88b82.png)

- [x] Getting started with addresses
    1. [x] description about etext
    The addresses of these symbols indicate the end of various program segments:
    * `etext`: This is the first address past the end of the text segment (the program code).
    * `edata`: This is the first address past the end of the initialized data segment.
    * `end`: This is the first address past the end of the uninitialized data segment (also known as the BSS segment).
    2. [x] screenshots of given program analysis
![example](https://user-images.githubusercontent.com/45392657/128447290-fbd67726-f008-46e8-9524-e0c12c7c3b1e.png)
the results are consistent to the descriptions of the variables since the addresses are Ascending which is expected.
    3. [x] screenshots of sbrk analysis
    code:
	    ```
	    #include <unistd.h>
		#include <stdio.h>
		#include <stdlib.h>
		#include <string.h>

		struct MyStruct {
		    int a;
		    int b;
		    char name[20];
		};

		int
		main ()
		{
		  void *heap1 = sbrk(0);
		  struct MyStruct *obj = malloc (sizeof(struct MyStruct));
		  void *heap2 = sbrk(0);
		  printf("end of heap address before malloc: %p\n", heap1);
		  printf("end of heap address after malloc: %p\n", heap2);
		}    
	    ```
	    the image of execution:
![sbrk](https://user-images.githubusercontent.com/45392657/128448550-d8e29640-f453-46c3-98ae-c09573adb2e1.png)
    4. [x] screenshots & code of heap growth analysis
    screenshot of execution:
![rec](https://user-images.githubusercontent.com/45392657/128449107-9db836a6-3f5b-4d30-9883-53af11411488.png)
    code:
	    ```
	    #include <unistd.h>
		#include <stdio.h>
		#include <stdlib.h>
		#include <string.h>

		void rec(int counter)
		{
			if (counter == 0)
				return;
			int i;
			printf("address of i: %p\n", &i);
			counter --;
			rec(counter);
		}

		int
		main ()
		{
			rec(100);
		}
	    ```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI4OTcyMjk1MSwxNDcxMTgwMjQyLC0xND
Q5OTE0MDM3LDEwNjc4NDk1MjIsLTYyNjExNTMyOSwtOTc4NzYz
MDc0LC0xOTYzOTEyOTEyLDE3MDE2MDM5MDMsMTcxNzQzNjQ4OS
wxMDg2MTQ3OTc2LDIxNDM3MjM3MDgsODU1OTYxNDEsLTczNDk4
NzgzOCw0ODMwMTgwOTYsMTg3ODk1MDcxMiwxNDQyMDA4Nzg1LD
E2Nzg0MzY5NzYsMTQxODgwOTg4NSwtMTk1Mzg5NDM5MSwtNjE5
OTEzNzIxXX0=
-->