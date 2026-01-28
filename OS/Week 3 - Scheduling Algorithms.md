### Multiprocessing vs. Multiprogramming

- **Multiprocessing**
	- The use of two or more CPUs within a single computer system. It also refers to the ability of a system to support more than one processor and/or the ability to allocate tasks between them.
- **Multiprogramming**
	- Multiple processes share common resources, e.g., a CPU. In a single CPU computer, only one process is running at any time. Multiprogramming solves the problem by scheduling the CPU from one process to another (context switch). When context switches occur frequently enough the illusion of parallelism is achieved. Even on multiprocessor computers, multiprogramming allows many more tasks to be run then there are CPUs.
- **Multithreading**
	- The ability of an OS to support multiple threads of execution within a single process.

### Resource Sharing

Multiprogramming introduces the resource sharing problem: which processes gets to use the physical resources of the machine when?

One crucial resource: CPU.

Only one process may use the CPU at a given time. (Only one PCB active at a time). 

Use pre-emptive multitasking; OS runs one process for a while, then takes the CPU away from that process and lets another process run. However must save and restore the process state.

Key Issue: to ensure that all processes get their fair share of the CPU.

### Representation of Process Scheduling

 - PCBs move from queue to queue as they change state.
 - Scheduling decisions: in which order to remove processes from queues.

![[Pasted image 20260126101400.png]]

### Schedulers

*A scheduler is an essential part of an OS, which schedules processor time for each process to facilitate multitasking*.

 - Often more processes are submitted than can be executed immediately.
	 - Spooled to a mass-storage device (e.g., a disk), where they are kept for later execution.
 - **Long-term Scheduler** (or job scheduler) - selects which processes should be brought into the ready queue.
 - **Short-term Scheduler** (or CPU scheduler) - selects which process should be executed next and allocates CPU.
 - The short-term scheduler is invoked very frequently (milliseconds) and therefore must be very fast.
 - The long-term scheduler controls the degree of multiprogramming (num. of processes in memory) - invoked infrequently e.g., when a process leaves the system (seconds, minutes) and therefore may be slow.
 - Processes can be described as either:
	 - I/O-bound processes: spend more time doing I/O than other computations, many short CPU bursts
	 - CPU-bound process: spend more time doing computations; few very long CPU bursts.
 - The long-term scheduler has to select a good process mix of I/O-bound and CPU bound processes.
 - Medium-term scheduler swaps the processes in and out of memory to balance the process mix.

### Basic Concepts

 - Maximum CPU utilisation obtained with multiprogramming.
 - CPU-I/O Burst Cycle
	 - Process execution consists of a cycle of CPU execution and I/O wait.
	 - Example: Alternating Sequence of CPU and I/O Bursts.
	 - In an I/O-bound program would have many very short CPU bursts.
	 - In a CPU-bound program would have a few very long CPU bursts.

### CPU Scheduler

Selects from among the processes in memory that are ready to execute, and allocates the CPU to one of them.

CPU Scheduling decisions may take place when a process:

 1. Switches from running to waiting state.
 2. Switches from running to ready state.
 3. Switches from waiting to ready.
 4. Terminates.

Scheduling under 1 and 4 is non-pre-emptive.

All other scheduling is pre-emptive - implications for data sharing between threads/processes.

### Dispatcher

 - Dispatcher module gives control of the CPU to the process selected by the scheduler; this involves:
	 - Switching context.
	 - Switching to user mode.
	 - Jumping to the proper location in the user program to restart that program.
 - **Dispatch latency** - time is takes for the dispatcher to stop one process and start another running.

![[Pasted image 20260126102747.png]]

### Scheduling Criteria

 - **CPU Utilisation** - Keep the CPU as busy as possible.
 - **Throughput** - # of processes that complete their execution per time unit.
 - **Turnaround time** - Amount of time to execute a particular process.
 - **Waiting time** - Amount of time a process has been waiting in the ready queue.
 - **Response time** - Amount of time it takes from when a request was submitted until the first response is produced, not output (for time-sharing environment).

### Scheduling Algorithm Assumptions

 - Basic assumptions behind most scheduling algorithms.
	 - There is a pool of runnable processes contending for the CPU.
	 - The processes are independent and compete for resources.
	 - The job of the scheduler is to distribute the scare resource of the CPU to the different processes *fairly* (according to some definition of fairness) and in a way that optimises some performance criteria.

### Scheduling Algorithm Goals

 - All Systems
	 - Fairness; giving each process a fair share of the CPU.
	 - Policy enforcement; seeing that stated policy is carried out.
	 - Balance; keeping all parts of the system busy.
 - Batch Systems
	 - Throughput; maximising jobs per hour.
	 - Turnaround time; minimise time between submission and termination.
	 - CPU Utilisation; keep the CPU busy all of the time.
 - Interactive Systems:
	 - Response time; respond to requests quickly.
	 - Proportionality; meet user's expectations.
 - Real-time Systems;
	 - Meeting deadlines; avoid losing data.
	 - Predictability; avoid quality degradation in multimedia systems

### First-Come, First-Served (FCFS) Scheduling

 - Each process joins the Ready queue.
 - When the current process ceases to execute, the oldest process in the Ready queue is selected.

![[Pasted image 20260126104143.png]]

![[Pasted image 20260126104204.png]]

### FCFS Pros and Cons

 - Pros:
	 - Simple algorithm to implement.
 - Cons:
	 - A short process may have to wait a very long time before it can execute.
	 - Favours CPU-bound processes.
	 - I/O processes have to wait until CPU-bound process completes.

### Shortest-Job-First (SJF) Scheduling

 - Associate with each process the length of its next CPU burst.
	 - Use these lengths to schedule the process with the shortest time.
 - SJF is optimal - gives minimum average waiting time for a given set of processes:
 - Two schemes:
	 - Non-preemptive: once CPU given to the process it cannot be preempted until it completes its CPU burst.
	 - Preemptive: a new process arrives with CPU burst length less than remaining time of current executing process, preempt. This scheme is known as the Shortest-Remaining-Time-First (SRTF).

### Example

![[Pasted image 20260128225419.png]]

### Priority Scheduling

 - A priority number (integer) is associated with each process.
 - The CPU is allocated to the process with the highest priority (smallest integer = highest priority)
	 - Preemptive
	 - Non-preemptive
 - Note that SJF is a priority scheduling where priority is the predicted next CPU burst time.
 - Problem = **Starvation**: low priority processes may never execute.
 - Solution = **Aging**: as time progresses increase the priority of the process.

### Round Robin (RR)

 - Each process gets a small unit of CPU time (time quantum), usually 10-100ms. After this time has elapsed, the process is preempted and added to the end of the ready queue.
 - We can predict wait time: If there are *n* processes in the ready queue and the time quantum is *q*, then each process gets 1/*n* of the CPU time in chunks of at most *q* time units at once. No process waits more than (*n* - 1)*q* time units.
 - Performance
	 - *q* large => FIFO
	 - *q* small => may hit the context switch wall: *q* must be large with respect to context switch, otherwise overhead is too high.

### Example

![[Pasted image 20260128230746.png]]

![[Pasted image 20260128230811.png]]

### Round Robin (RR) Analysis

 - Pros
	 - Better for short jobs, fair.
	 - Context switching time adds up for long jobs
 - Performance:
	 - How to choose a time quantum?
		 - If the quantum is too big, response time suffers, same as FCFS
		 - If the quantum is too small, throughput suffers.
 - Quantum must be large with respect to context switch, otherwise overhead is too high.

### Multilevel Queue

 - With priority scheduling, have separate queues for each priority.
 - Schedule the process in the highest-priority queue.
 - Ready queue is partitioned into separate queues:
	 - Foreground (interactive)
	 - Background (batch)
 - Each queue has its own scheduling algorithm:
	 - Foreground (RR)
	 - Background (FCFS)
 - Scheduling must be done between the queues:
	 - Fixed priority scheduling, (i.e., serve all from foreground then from background). Possibility of starvation
	 - Time slice: each queue gets a certain amount of CPU time which it can schedule amongst its processes: i.e., 80% to foreground in RR.
	 - 20% to background in FCFS.

![[Pasted image 20260128231349.png]]