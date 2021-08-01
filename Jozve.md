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


- [ ] Describe the C program (fork program)
    1. [ ] `[FILL HERE with descriptions]`

- [ ] Program showing that memory of the parent and the child is seperate
    1. [ ] `[FILL HERE with your source code]`

- [ ] Program printing different messages for parent and child process
    1. [ ] `[FILL HERE with your source code]`

- [ ] Program for the last task of this section
    1. [ ] `[FILL HERE with your source code]`
    1. [ ] `[FILL HERE with you description of the output`]

## Section 4.4.3

- [ ] Program using `wait` and counting from 1 to 100
    1. [ ] `[FILL HERE with your source code]`
    1. [ ] `[FILL HERE about description for the parameter of wait system call]`

- [ ] Program showing process adoption
    1. [ ] `[FILL HERE with your source code]`
    1. [ ] `[FILL HERE an image from execution of your program]`

### Section 4.4.4

- [ ] Describe following commands/APIs:
    1. `[FILL HERE with description about execv]`
    1. `[FILL HERE with description about execl]`
    1. `[FILL HERE with description about execvp]`
    1. `[FILL HERE with description about execlp]`

- [ ] Program which forks and executues `ls` command
    1. [ ] `[FILL HERE with your source code]`
    1. [ ] `[FILL HERE an image from execution of your program]`

## Source Code Submission

please submit all your codes in a zip file

 - [ ] `Zip File HERE`

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjE0MzcyMzcwOCw4NTU5NjE0MSwtNzM0OT
g3ODM4LDQ4MzAxODA5NiwxODc4OTUwNzEyLDE0NDIwMDg3ODUs
MTY3ODQzNjk3NiwxNDE4ODA5ODg1LC0xOTUzODk0MzkxLC02MT
k5MTM3MjEsNzk5MDY2MDUsMjAwODI0NDgsMTMwMjM1NjA3LC0x
MDcwMTg3NDMsLTczOTkxODA1NywxNTMxOTkxMTM4LC0xMDI3Mz
Y1OTY4LDQ3MTI0ODYxMCwtMTQ5MzQxNzk5NiwtMjA3ODM3NjAy
MV19
-->