# Ex02 – Linux Process API: fork(), wait(), exec()

**Operating Systems Lab Exercise**

**Name:** MANORAJAPRIYAN.L.E  
**Register Number:** 212225040227

---

## AIM

To write a C program using Linux Process API system calls `fork()`, `getpid()`, and `wait()` to create a child process and display the Process ID (PID) of the parent and child processes.

## DESIGN STEPS

1. Open the Ubuntu/Linux terminal.
2. Create a C program using the `fork()`, `getpid()`, and `wait()` system calls.
3. Save the program as `fork.c`.
4. Compile the program using GCC.
5. Execute the program and verify the output.

---

## PROGRAM 1: Process Creation Using fork() and wait()

### SOURCE CODE

**File: fork.c**

```c
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>

int main()
{
    pid_t pid;

    pid = fork();

    if (pid < 0)
    {
        printf("Fork failed\n");
    }
    else if (pid == 0)
    {
        printf("Child PID: %d\n", getpid());
    }
    else
    {
        printf("Parent PID: %d\n", getpid());
        wait(NULL);
    }

    return 0;
}
```

### COMPILATION

```bash
gcc fork.c -o fork
```

### EXECUTION

```bash
./fork
```

### OUTPUT

```text
Parent PID: 2185
Child PID: 2186
```

<img width="926" height="702" alt="image" src="https://github.com/user-attachments/assets/b60a8b6b-0c49-49ea-a6d3-6fe9e4355f30" />


*Note: PID values may change every time the program is executed.*

---

## EXPLANATION

- **fork():** Creates a new child process.
- **getpid():** Returns the Process ID of the calling process.
- **wait(NULL):** Makes the parent process wait until the child process terminates.
- **pid < 0:** Indicates that process creation failed.
- **pid == 0:** Indicates that the executing process is the child.
- **pid > 0:** Indicates that the executing process is the parent.

---

## RESULT

Thus, the C program using Linux Process API system calls `fork()`, `getpid()`, and `wait()` was successfully executed, and the Process IDs of the parent and child processes were displayed.
