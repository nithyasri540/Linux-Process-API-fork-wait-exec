# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls
```
#include <stdio.h> 
#include <unistd.h> 
#include <stdlib.h> 
#include <sys/wait.h> 
  
int main() { 
    pid_t pid = fork(); 
  
    if (pid < 0) { 
        printf("Fork failed\n"); 
        return 1; 
    } 
    else if (pid == 0) { 
        printf("Child Process: PID = %d\n", getpid()); 
        exit(0); 
    } 
    else { 
        wait(NULL); 
        printf("Parent Process: PID = %d\n", getpid()); 
    } 
  
    return 0; 
}
```












##OUTPUT

<img width="1920" height="1080" alt="Screenshot 2026-10-23 084705" src="https://github.com/user-attachments/assets/9affb034-bbba-42b2-b835-530c9afcadb7" />









## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family

```
#include <stdio.h> 
#include <unistd.h> 
#include <sys/wait.h> 
#include <stdlib.h> 
  
int main() { 
    pid_t pid = fork(); 
  
    if (pid == 0) { 
        printf("Child process using exec()\n"); 
        execlp("ls", "ls", "-l", NULL); 
        perror("exec failed"); 
        exit(1); 
    } else if (pid > 0) { 
        wait(NULL); 
        printf("Parent process completed\n"); 
    } else { 
        perror("fork failed"); 
    } 
  
    return 0; 
}
```

























##OUTPUT


<img width="992" height="347" alt="Screenshot 2026-10-23 084749" src="https://github.com/user-attachments/assets/807dcf4f-50b8-483b-991a-ba05a47c1830" />

















# RESULT:
The programs are executed successfully.
