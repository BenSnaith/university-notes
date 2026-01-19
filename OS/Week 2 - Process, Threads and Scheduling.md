### The Concept of Multiprogramming

 - Multiprogramming is the fundamental concept in modern operating system.
 - Multiple programs can be executed at a same time.
 - Multi-programming **maximises CPU utilisation** and overall system throughput.
 - Unix, Windows NT/2000/XP/Vista/7.

### Process

 - A Process is an independent program or application running in the computer's memory.
 - A process contains the program code and its current job.
 - Process memory is divided into four parts:
	 - **Text Section** contains **Program Code**
	 - **Data Section** stores **global** and **static** variables.
	 - **Heap** used for **dynamic memory allocation** during run time.
	 - **Stack** contains temporary data like functions parameters, return address data local variables.
- A process can't directly affect another process.

![[Pasted image 20260119135644.png]]

### Memory Layout of a C Program

![[Pasted image 20260119135702.png]]

### Process != Program

**Process**
 - Process is Dynamic
 - Process is an Active
 - Process is created during the execution, directly loaded in main memory.
 - Process has its own control system known as Process Control Block.
 - Processes have significant resource demands; they require resources like Memory Addresses, Central Processing Unit, Input or Output.

**Program**
 - Program is Static
 - Program is Passive
 - Program already exists in the memory, and it is present in the secondary memory.
 - Program does not have any control system.
 - A program just needs memory space to store its instructions.

>A process is an active instance of a program that's running in memory. Processes have their own memory space, resources, and state.

>A program is a file that contaisn a set of instructions written in a programming language. Programs are static entities that are stored on the disk.

A program becomes a process when its loaded into memory and started. For example, when you double click the web browser icon, the program opens and becomes a process.

### Resource Sharing

 - **Multiprogramming** introduces the **resource** sharing problem: which processes get to use the physical resources of the machine when?
 - One essential resource: CPU
 - Only one process may use the CPU at a given time.
 - Use pre-emptive multi-tasking: OS runs one process for a while, then takes the CPU away from that process and lets another process run.
 - Must save and restore the **process state**.
 - Key issue: to ensure that all processes get their fair share of the CPU.

### Process State

 - As a process executes, it changes state:
	 - **New**: The process is being created.
	 - **Running**: Instructions are being executed.
	 - **Waiting**: The process is waiting for some event to occur.
	 - **Ready**: The process is waiting to be assigned to a processor.
	 - **Terminated**: The process has finished execution.

![[Pasted image 20260119141209.png]]

### Process Control Block (PCB)

 - The **current state** of a process is held in a process control block (PCB).
 - A PCB is a snapshot of the execution and protection environment. In include:
	 - **Process State** - running, waiting, etc.
	 - **Program Counter** - location of instruction to next execute.
	 - **CPU Registers** - contents of all process-centric registers.
	 - **CPU Scheduling Information** - priorities, scheduling queue pointers.
	 - **Memory-management Information** - memory allocated to the process.
	 - **Accounting Information** - CPU used, clock time elapsed since start, time limits.
	 - **I/O Status Information** - I/O devices allocated to process, list of open files.

![[Pasted image 20260119141722.png]]

### CPU Switch from Process to Process

 - A **Context Switch** occurs when the CPU switches from one process to another.

![[Pasted image 20260119141757.png]]

 - When CPU switches to another process, the system must save the state of the old process and load the saved state for the new process via a context switch.
 - Context of a process represented in the PCB.
 - Context-switch time is pure overhead; the system does no useful work while switching.
	 - The more complex the OS and the PCB -> The longer the context switch.
 - **Threads** as solution to context switch overhead.

### Process Creation

 - Parent process create children processes, which, in turn create other processes, forming a tree of processes.
 - Generally, process identitief and managing via a **process identifier** (**PID**).
 - Resource sharing options
	 - Parent and children share all resources.
	 - Children share a subset of parent's resources.
	 - Parent and child share no resources.
 - Options Execution
	 - Parent and children execute concurrently.
	 - Parent waits until children terminate.
 - UNIX examples:
	 - `fork()` system call creates a new process.
	 - `exec()` system call used after `fork()` to replace the process' memory space with a new program.
	 - Parent process calls `wait()` waiting for the child to terminate.

### UNIX Fork/Exec/Exit/Wait Example

```cpp
int pid = fork();

exec("program", {argvp, envp});

exit(status);

int pid = wait(&status);
```

### C Program Forking Separate Process

```cpp
int main(void)
{
	int pid;
	
	pid = fork();
	
	if(pid < 0)
	{
		std::cerr << "Fork Failed" << std::endl;
		exit(-1);
	}
	else if(pid == 0) 
	{
		execlp("/bin/ls", "ls", nullptr);		
	}
	else
	{
		wait(nullptr);
		std::cout << "Child Complete" << std::endl;
		exit(0);	
	}
	
	return 0;
}
```

### Process Termination

- Process executes last statement and then asks the operating system to delete it using the `exit()` system call.
	- Returns status data from child to parent (via `wait()`)
	- Process' resources are **deallocated** by the Operating System.
- Parent may terminate the exectution of children processes using the `abort()` system call. Some reasons for doing so:
	- A child has exceeded allocated resources.
	- Task assigned to child is no longer required.
	- The parent is exiting, and the operating system does not allow a child to continue if its parent terminates.

### Interprocess Communication

 - **Independent Processes** operating concurrently on a systems are those that can neither affect other processes or be affected by other processes.
 - **Cooperating Processes** are those that can affect or be affected by other processes.
	 - Information sharing - need to access the same file for example. (e.g., pipelines).
	 - Computation speedup - when multiple processes are involved.
	 - Modularity - The most efficient architecture may be to break a system down into cooperating modules. (e.g., databases with a client-server architecture).
	 - Convenience - Even a single user may be multi-tasking, such as editing, compiling, printing, and running the same code in different windows.
 - Cooperating processes need interprocess communication (IPC).
 - Two models of IPC:
	 - Shared memory.
	 - Message Passing.

### Shared Memory Model

- An area of **memory shared among the processes** that wish to communicate.
- The communication is under the control of the **users processes** not the operating system.
- Major issues is to provide mechanism that will allow the user processes to **sync their actions** when they access shared memory.

![[Pasted image 20260119143937.png]]

### Message Passing Model

 - Communication by means of **messages exchanged** between the cooperating processes.
 - IPC facility provides two operations:
	 - `send(message)`
	 - `receive(message)`

![[Pasted image 20260119143826.png]]

### Threads

- Light-weight processes that share the same memory and state space.
- Every process has at least one thread.
- Benefits:
	- Resource sharing, no need for IPC.
	- Economy: faster to create, faster to context switch.
	- Scalability: simple to take advantage of multi-core CPUs.
- Each thread has its own **stack**, **PC**, **registers**

![[Pasted image 20260119144655.png]]

### Single and Multithreaded Processes

![[Pasted image 20260119144709.png]]

### Thread State

 - Shared Thread State
	 - State shared by all threads in process / address space.
	 - Contents of memory (global variables, heap).
	 - I/O state (file system, network connections, etc).
 - Private Thread State
	 - State "private" to each thread.
	 - Kept in TCB = Thread Control Block.
	 - CPU registers (including program counter)
	 - An execution stack and some per-thread static storage for local variables.

### Benefits of Threads

 - **Responsiveness** - may allow continued execution if part of process is blocked, expecially important for user interfaces.
 - **Resource Sharing** - threads share resources of process, easier than shared memory or message passing. This allows an application to have several different threads of activity within the same address space.
 - **Economy** - cheaper than process creation, thread switching lower overhead than context switching. Allocating memory and resources for process creation is costly. As threads share resources of the process to, they belong it is more economical to create and context switch threads.
 - **Scalability** - threads may be running in parallel on different CPUs.

A single-threaded process can only run on one CPU, no matter how many are available. Multithreading on a multi-CPU machine increases concurrency.

### Thread Models: User and Kernel Threads

 - There are different thread models that determine how threads are managed and executed by the Operating System.
	 - User-level threads.
	 - Kernel-level threads.
	 - Combination of user-and-kernel-level threads.

### User Threads

 - User process is in complete controls
	 - Usually use a library to implement (`pthreads`)
 - OS not involved
	 - Very fast to create and manage
 - OS has no knowledge of multiple threads
	 - If one thread blocks and I/O, process blocks.
	 - Other threads in process may be available to run.

### Kernel Threads

 - OS devotes multiple threads to a process.
 - Controlled by OS
	 - Slow to create and manage.
 - OS does have knowledge of process threads
	 - If one process thread blocks, OS can schedule another thread of process.

### Multithreading Models

- Many-to-one Model
	- One kernel thread per process.
	- All process threads share a kernel thread:
		- One blocks, all blocked.
	- Can't run a multi-threaded process on multiple processors.

### Many-to-One

![[Pasted image 20260119150405.png]]

### Multithreading Models

 - One-to-One Model
	 - One kernel thread per user thread.
	 - One blocks, another can run.
	 - Slow to create and manage.
	 - Usually a finite set of threads available from OS.
	 - Allows multithreaded process' to run on multiple processors.


### One-to-One

![[Pasted image 20260119150508.png]]

### Multithreading Models

 - Many-to-Many Model
	 - Multiple user level and kernel level threads.
	 - Process can assign a set of threads to a kernel thread.
	 - If one thread blocks, all threads in it's group block but another group of threads in the process could run.
	 - Still have limitations within a group or switching between groups
		 - All in all, though, much more flexible.

### Many-to-Many

![[Pasted image 20260119150811.png]]