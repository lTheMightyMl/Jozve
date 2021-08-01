


Team Name: `97105782-97101359`

Student Name of member 1: `Mostafa Ojaghi`
Student No. of member 1: `97105782`

Student Name of member 2: `Mohammad Sepehr Pourghannad`
Student No. of member 2: `97101359`

- [x] Read Session Contents.

### Section 4.4.1
- [x] Investigate the ps command
    1. [x] ps command to get all processes
![ps-aux](https://user-images.githubusercontent.com/45392657/127770525-e2e0f4a5-b712-4972-9613-90962a973ad0.png)
there are some columns that indicate attributes of each process. For instance, CPU and MEM show the cpu usage and ram usage respectively or VSZ show the virtual memory size of the process.


- [x] Infromation about processes with PID = 1
    1. [x] Due tho the below picture pid = 1 is init process
![pid1](https://user-images.githubusercontent.com/45392657/127770777-e7392d3b-b987-4866-8775-bb3e1f46d0f4.png)
systemd(init) is a system and service manager for Linux operating systems. When run as first process on boot (as PID 1), it acts as init system that brings up and maintains userspace services. init is started by the kernel during the booting process.

- [x] Program using getpid
    1. [x] C++ code for `getpid`
```
#include <iostream>
#include <sys/types.h>
#include <unistd.h>

using namespace std;

int main() {
   int pid = getpid();
   cout << "My process id = " << pid << endl;
   return 0;
}
```

### Section 4.4.2

- [x] Program using getppid
	1. [x]  program code
		```
		#include <iostream>
		#include <sys/types.h>
		#include <unistd.h>

		using namespace std;

		int main() {

		   pid_t parent_pid = getppid();
		   pid_t my_pid = getpid();

		   cout << "My pid = " << my_pid << ", my parent pid = " << parent_pid << endl;

		   return 0;
		}
		```
	2. [x]  descriptions about the parent process
    ![fatherdesc](https://user-images.githubusercontent.com/45392657/127772326-07b72d5f-16a8-4a9b-b5be-03c4ec60ba2f.png)
 since the code is executed in the terminal the father process is ZSH

    1. [x] image of execution
![ppid](https://user-images.githubusercontent.com/45392657/127772212-20b103c2-4619-425b-a388-735c04d6506b.png)


- [x] Describe the C program (fork program)
    1. [x] the `if == 0` stands for the child process and the `else` scope is for father process. the father wait until the child process is finished and afterward it prints the return code of the child process which is `23`

- [x] Program showing that memory of the parent and the child is seperate
    1. [x] source code
	```
	#include <unistd.h>
	#include <sys/types.h>
	#include <errno.h>
	#include <stdio.h>
	#include <sys/wait.h>
	#include <stdlib.h>

	int main(void)
	{
		int localVar = 0;
		int* p = (int*) malloc(2);
		pid_t childPID = fork();

		// Putting value at allocated address
		*p = 0;
	    if (childPID == 0) // child process
	    {
	        printf("\n Child Process Initial Value :: localVar = %d", localVar);
	        localVar++;

	        int c = 500;
	        printf("\n Child Process :: localVar = %d", localVar);
	        printf("\n Address of malloced mem child = %p and value is %d", p, *p);
	        printf("\n change the value pointed my malloc");
	        *p = 50;
	        printf("\n Address of malloced mem child = %p and value is %d", p, *p);
	    }
	    else // Parent process
	    {
	        printf("\n Parent process Initial Value :localVar = %d", localVar);
	        localVar = 10;
	        printf("\n Parent process :: localVar = %d", localVar);
	        printf("\n Address of malloced mem parent= %p and value is %d", p, *p);
	        *p = 100;
	        printf("\n Address of malloced mem parent= %p and value is %d", p, *p);
	    }

		return 0;
	}
	```
- [x] Program printing different messages for parent and child process
    1. [x] source code
    ```
    #include <stdio.h>
	#include <sys/wait.h>
	#include <unistd.h>
	int main() {
		int ret = fork();
		if (ret == 0) {
			printf("i am the child in the ret == 0\n");
			return 23;
		} else {
			int rc = 0;
			wait(&rc);
			printf("i am parent\n");
		}
		return 0;
	}
    ```

- [x] Program for the last task of this section
    1. [x] source code
    ```
	#include <stdio.h>
	#include <sys/wait.h>
	#include <unistd.h>
	int main() {
		int ret = fork();
		if (ret == 0) {
			printf("i am the child in the ret == 0\n");
			return 23;
		} else {
			int rc = 0;
			wait(&rc);
			printf("i am parent\n");
		}
	    printf("after the first fork\n");
	    fork();
	    printf("after the second fork\n");
	    fork();
	    printf("after the third fork\n");
	    printf("finish\n");
		return 0;
	}
    ```
	
    3. [x] description of the output
![forkfork](https://user-images.githubusercontent.com/45392657/127773743-626604b9-4ece-4d3e-879f-24462688a602.png)
at the beginning, it's just as before, when the first fork is finished, we can see 3 consecutive `after i fork` and the finish which is referred to the parent process. Then there is 2  consecutive `after i fork` which is referred to the second fork. the remaining messages are from the third fork which is once initialized in the parent process and once in the child process of the second fork. 


## Section 4.4.3

- [x] Program using `wait` and counting from 1 to 100
    1. [x] source code
    ```
	#include<stdio.h>
	#include<sys/wait.h>
	#include<unistd.h>
	 
	int main()
	{
	    if (fork()== 0)
	    {
	        for (int i = 1; i <= 100; i++) {
	            printf("%d ", i);
	        }
	        printf("\n");
	    }
	    else
	    {
	        wait(NULL);
	        printf("parent: child has terminated\n");
	    }
	    return 0;
	}
    ```
    2. [x] description for the parameter of wait system call
    `wait(0)` means wait until a state change in the child process. The call `wait(&wstatus)` is equivalent to:
           `waitpid(-1, &wstatus, 0);`
           and the parameter of `wstatus` is used for storing the status of child process.

- [x] Program showing process adoption
    1. [x] source code
    ```
	#include <stdio.h>
	#include <sys/wait.h>
	#include <unistd.h>
	#include <iostream>
	 
	int main()
	{
	    if (fork()== 0)
	    {
	        printf("the parent id of the child is: %d\n", getppid());
	        sleep(2);
	        printf("the parent id of the child after sleeping is: %d\n", getppid());
	    }
	    else{
	        return 0;
	    }
	}
    ```
    3. [x] image from execution of your program    
![sleep](https://user-images.githubusercontent.com/45392657/127775117-5271e540-945c-4bb4-b185-85e9fd7c2f2c.png)


### Section 4.4.4

- [x] Describe following commands/APIs:
    1. `execv` : `execv (const char *filename, char *const argv[])`
    The filename is the file of the new process image. argv represents an array of null-terminated strings.
    1. `execl` : `execl (const char *filename, const char *arg0, …)`
    Same as `execv` but the arguments are provided as an individual string (separated by commas) instead of an array/vector.
    1. `execvp` : `execvp (const char *filename, char *const argv[])`
    Same as `execv` function but it searches standard environment variable PATH to find the filename if the filename does not contain a slash.
    1. `execlp` : `execlp (const char *filename, const char *arg0, …)`
    Same as `execl` function except the fact that if performs the filename search as the `execvp` function.

- [x] Program which forks and executues `ls` command
    1. [x] source code
    ```
    
	#include <stdio.h>
	#include <sys/wait.h>
	#include <unistd.h>

	int main()
	{
	    if (fork()== 0)
	    {
	        char *args[] = {"ls", "-g", "-h", NULL};
	        printf("in the child\n");
	        execvp(args[0], args);
	    }
	    else{
	        return 0;
	    }
	    return 0;
	}
    ```
    3. [ ] `[FILL HERE an image from execution of your program]`

## Source Code Submission

please submit all your codes in a zip file

 - [ ] `Zip File HERE`

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA2Nzg0OTUyMiwtNjI2MTE1MzI5LC05Nz
g3NjMwNzQsLTE5NjM5MTI5MTIsMTcwMTYwMzkwMywxNzE3NDM2
NDg5LDEwODYxNDc5NzYsMjE0MzcyMzcwOCw4NTU5NjE0MSwtNz
M0OTg3ODM4LDQ4MzAxODA5NiwxODc4OTUwNzEyLDE0NDIwMDg3
ODUsMTY3ODQzNjk3NiwxNDE4ODA5ODg1LC0xOTUzODk0MzkxLC
02MTk5MTM3MjEsNzk5MDY2MDUsMjAwODI0NDgsMTMwMjM1NjA3
XX0=
-->