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
    - [x] `FILL HERE with screenshot of execution`

    
- [ ]  Using `ps`
    - [ ] `FILL HERE with screenshot of command output`
    - [ ] `FILL HERE with your descriptions (write in English or Persian)`

- [ ]  Getting started with memory segments
    - [ ] `FILL HERE with screenshot of which command for ls`
    - [ ]  `FILL HERE with screenshot for size`
    - [ ]  `FILL HERE with segments not shown with size`
    

- [ ] Getting started with memory sharing
    1. [ ] `[FILL HERE with screenshot of lld for ls]`
    1. [ ] `[FILL HERE with screenshot of lld for nano]`
    1. [ ] `[FILL HERE with screenshot of lld for another program]`

- [ ] Getting started with addresses
    1. [ ] `[FILL HERE with your description about etext]`
    2. [ ] `[FILL HERE with your screenshots of given program analysis]`
    3. [ ] `[FILL HERE with your screenshots of sbrk analysis]`
    4. [ ] `[FILL HERE with your screenshots & code of heap growth analysis]`


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NDk5MTQwMzcsMTA2Nzg0OTUyMiwtNj
I2MTE1MzI5LC05Nzg3NjMwNzQsLTE5NjM5MTI5MTIsMTcwMTYw
MzkwMywxNzE3NDM2NDg5LDEwODYxNDc5NzYsMjE0MzcyMzcwOC
w4NTU5NjE0MSwtNzM0OTg3ODM4LDQ4MzAxODA5NiwxODc4OTUw
NzEyLDE0NDIwMDg3ODUsMTY3ODQzNjk3NiwxNDE4ODA5ODg1LC
0xOTUzODk0MzkxLC02MTk5MTM3MjEsNzk5MDY2MDUsMjAwODI0
NDhdfQ==
-->