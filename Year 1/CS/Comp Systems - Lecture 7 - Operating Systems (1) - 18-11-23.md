- Support Video Notes
    
    [Powerpoint](https://learn-eu-central-1-prod-fleet01-xythos.content.blackboardcdn.com/5d2cb9c32e9d7/12458421?X-Blackboard-S3-Bucket=learn-eu-central-1-prod-fleet01-xythos&X-Blackboard-Expiration=1700244000000&X-Blackboard-Signature=i47z9pK9EnD4Oqjv8ug%2FclOnxJ%2FMR3TqmGKWLbXHXiI%3D&X-Blackboard-Client-Id=163100&X-Blackboard-S3-Region=eu-central-1&response-cache-control=private%2C%20max-age%3D21600&response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27CS1CS-Lec7-OS1-2022%25281%2529.pdf&response-content-type=application%2Fpdf&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEF8aDGV1LWNlbnRyYWwtMSJIMEYCIQDGSBFWvTcZQYBar4pMxmNbH5NKsGtqv7GApd8HfgsZ5AIhANEoJZGVfvUv8dptXeMRsr3nQNA0eGW7s%2FVMPRjFSun%2BKsYFCKj%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQAxoMNjM1NTY3OTI0MTgzIgz%2BVoRzVuJw3t02R1UqmgXhGAUACeUsM6Kg6%2FJz5BRZIhmaJP82sKY2Nim0ioYVHB%2FKa0cZKvt1kFAkjGfERdjl7fV%2FUg1OIRw7B4jCcFwpK0%2BmWV%2Fu684A0NPnD3B%2FEY9FD6IzD2wLbpM3J2vxQLqakPKdRyT%2Bb1DCg0%2BcQXbt2A%2Fd1vG0afUGHZTuLMIYS%2FfHsCAffYEBWACrQtkpKekzqxEIQ74PyhFAVADtlVTefrYt5yr4j%2FXroFw%2F1574AGj4MwQ95ggGXErNKNsOUHph4%2F7%2F5sI2rtLQwoa3ugWpHvjdJ%2Bp0GE6d0B8%2BlEY4Zx%2FJ1icJWb61sIwOjrbbrvX2zwEZAB3bmiC2OyY2Xrz84m39MPEENsQKHXayK34WRbZpr7DwldV%2Br6EizUtPdS0IZd0JtGpPW39fqMJPmvcTvrZyRo9QvBSey%2BaYxaLHeohv%2BqdVG2KqC79S%2Bp7560U43bMr%2F2VLZZz49ofq4WNNNfqVimPXWkNU0LkSWhng7gynETLzE%2FmpYg38NY3CLX0jKMqmo6Xkk%2FH0gsrTrT1WxEaVmExZKRhDB2wK%2B9owNJgZQb2%2BpY374SBIoAK31hwGOakzxj43sf%2BgeiVoqR7pmA4Y7Rc3CXBc%2BAFGV3z5uTmhzcpTDD%2FBFqtBqH5G%2BHERnPd0WN2eRhWyv3BIgmVGxhLJNfSEMpPJSddxPknJsVytqOveE1H9mmL%2FqvBB3P%2BEpNZGWqPHcNmT1Ring9vX4flREfgVdmeoPHBZYTK4kruh%2FxnF6htvsvHiocuOnAIubPtqbc%2FWk5wtyRI26TADU9EIrZZpu3MTUaIO3cZFmyKDML7vJgY7FMrsIesxzFAnZGFtHHzTGVBYQ8ta9Ig48JZh%2BK9Qrl5Y7wI1jWQrfRFY7XC9PbVKjZcw6%2B%2FdqgY6sAGhZ2ZqII3sCj%2BwhYKDSiYQeFKtO0jTeega83HYySFAv1beiM8J%2FV1sYLwkCA2L5eRS1aEJRS9u7jqCkvzN0gMU%2ByGN%2BqaxIbh9LDYuc5UckSIbOAZfHkYWqI97I2lNZJQwJ2%2B1nEFxQWM9PAQGlao5boN71REvyAHaN%2FNPhkWGSKiccGWCeeC3Fe9Lt9fJ5q2zeXXYQqUOQ4qMq1K9EPgRiFrlaBQeQcIIvDNMOrUKeQ%3D%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20231117T120000Z&X-Amz-SignedHeaders=host&X-Amz-Expires=21600&X-Amz-Credential=ASIAZH6WM4PLXWXJ4CE6%2F20231117%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Signature=501a263ef8468eef5a4b7788dba33d90a97b61318436a040e8139b40173b4008)
    
    ## What is an OS.
    
    An operating system is a piece of software; a program, that sits between the user and the hardware, let’s use an example to understand this more clearly.
    
    A user operating a spread sheet saves their file, from their view they see a hierarchical file structure in which they can add, remove and reorganise directories, saving the file in a directory of their choosing.
    
    ![[Untitled 26.png|Untitled 26.png]]
    
    The reality of the storage device, on which this file is stored, bares no resembalence to this hierarchical file system.
    
    ![[Untitled 1 15.png|Untitled 1 15.png]]
    
    Let’s assume that the file is being saved on a magnetic disk, like a HDD (Hard Disk Drive), The files location is identified by it’s track and sector.
    
    ![[Untitled 2 15.png|Untitled 2 15.png]]
    
    Files in the same directory might not be physically adjected (inhabiting sectors next to one another) and depending on the system setup they may not even be on the same drive.
    
    ![[Untitled 3 13.png|Untitled 3 13.png]]
    
    The user looking at their hierarchical structure, in a rather abstract way, is insulated from this complex system, The OS deals with a user in a way where the user can easily issue commands, and works with the hardware in a way which can make the hardware work as needed. This is what we mean by saying the OS sits between the **User** and the **Hardware.**
    
    ## What else does it do?
    
    Storage like we have mentioned previously, is a resource, and the OS manages all resources rather that be;
    
    - Storage
    - CPU Time
    - Memory
    
    - ==Peripherals and I/O==
    
    - Networking
    
    When you (the user) request access to any of these resources from your application, your application, in turn, requests services (resources) from the OS.
    
    ![[Untitled 4 12.png|Untitled 4 12.png]]
    
    Operating systems also provide the user with **Abstraction** we saw one earlier in the hierarchical file structure, which doesn’t exist in that form in reality, but there are plenty of others. If you want to **delete a file** you drag it along the Abstraction of the **desktop** (which doesn’t really exist, that’s what an abstraction is), to an abstraction of a **recycle bin** (which again isn’t real) even a file is an abstraction, it just point to an assembly of bits, possibly distributed across multiple storage devices.
    
    ![[Untitled 5 12.png|Untitled 5 12.png]]
    
    The OS allows us (the users) to make use of these bits via these abstractions.
    
    ## Kernel
    
    At the core of the OS is a program called the **Kernel**, among one of the first programs on start-up it remains in memory as long as the computer is running and is responsible for managing **memory, processes & secondary storage** the essential elements of the system.
    
    ![[Untitled 6 9.png|Untitled 6 9.png]]
    
    Other parts of the OS such as;
    
    - Infrequently used programs
    - Software tools
    - Terminal commands
    
    Are not in memory all of the time, and therefore, are not part of the Kernel
    
    ## CPU Modes
    
    The CPU spends its time in one of two modes;
    
    - Kernel Mode
        - executing code has complete access to the hardware
        - any instruction can be executed
        - any memory address can be accessed
        - crashed are catastrophic (halt the entire device)
    - User Mode
        - code makes use of APIs (application programming interfaces)
        - crashes are recoverable
        - you are (probably) here
    
    ## Types of OS
    
    - Stand-alone (desktop, laptop, etc.)
        - Windows 95, 98, XP, 7, 8, 10
        - Mac OS
        - Linux
        - DOS
        - Unix
    - Server (manages user accounts and resources across and entire network)
        - Windows NT, 2003, 2008, 2012
        - Linux
        - Unix
        - Solaris
    - Embedded/Mobile (On a ROM chip on an electronic device)
        - iOS
        - Android
    
    ## OS and CPU Management
    
    ## Multitasking
    
    This describes an instance where, multiple process are being performed at the same time, to clarify a **process** is a **program being executed** right now, to the user, such processes can appear to be dealt with simultaneously, although that is generally not the case. although CPUs can run some processes in parallel, there may be more processes than there are cores (processors)
    
    ![[Untitled 7 8.png|Untitled 7 8.png]]
    
    In addition to this, there are some processes that just can’t be ran in parallel, nevertheless from the standpoint of the user, multiple things can appear simultaneous.
    
    Generating the word count from a document is unlikely to interrupt a media player running at the same time, so how does this work?
    
    ## I/O Breaks
    
    While one process awaits Input/Output another is being executed by the CPU
    
    ![[Untitled 8 8.png|Untitled 8 8.png]]
    
    This means that in this instance, the media player is not constantly using the CPU the entire time
    
    ## Time Slicing
    
    A single CPU Core cannot complete 2 tasks at once. but it can switch rapidly between tasks.
    
    ![[Untitled 9 7.png|Untitled 9 7.png]]
    
    ![[Untitled 10 7.png|Untitled 10 7.png]]
    
    **Slicing time** amongst the processes which require it’s attention.
    
    ## Software requirement
    
    Two pieces of software needed to do these are;
    
    - Short-Term scheduler
    - Dispatcher
    
    **Short-term scheduler**
    
    The short term scheduler determined which process is next.
    
    **Dispatcher**
    
    Enforces the Short-term schedulers decision, changing the state of the process.
    
    For example, if we have a series of processes which are in the ‘ready’ state and the short-term scheduler selects ‘Process 1’ to be dealt with next, the dispatcher transfers ‘Program 1’ from ‘Ready’ to ‘Running’ each process has a unique identifier, called a process ID.
    
    When a time slice has been allocated to P1, and that time slice has passed, assuming that the process is not done, it may go back to the ‘Ready’ state. In order for the CPU to continue working on it in a later time slice, the process context needs storing.
    
    ![[Untitled 11 5.png|Untitled 11 5.png]]
    
    This includes the content of all registers when the process’ time slice expired, that means the next time it is running, it can simply continue being executed, although loading this context is a time-overhead where nothing useful is taking place.
    
    ## A process might be…
    
    - I/O Bound
        - Spend more time with I/O that the CPU
        - Many short CPU bursts
    - CPU Bound
        - Largely computation focused CPU > I/O
        - Fewer but longer CPU bursts
    
    ## Process states
    
    The process can either be;
    
    - Running
        - Being dealt with by the CPU, right now
    - Ready
        - Ready to use the CPU
    - New
        - Being created, right now
    - Waiting
        - Waiting for something other than the CPU, typically a slower device like I/O
    - Terminated
        - Finished being executed
    
    ## Long-Term Scheduler
    
    While the Short-Term Scheduler selects from processes in the “Ready” Queue, the Long-Term Scheduler decides which processes can enter the queue in the first place.
    
    ![[Untitled 12 5.png|Untitled 12 5.png]]
    
    The more processes that are allowed into the “Ready” state, the greater the degree of multiprogramming is involved
    
    ![[Untitled 13 4.png|Untitled 13 4.png]]
    
    ## Scheduling Algorithms
    
    There are several scheduling algorithms;
    
    - First-come-first-serve;
        
        - Which ever process requests the CPU first, gets it first, and gets full use of it until it is terminated, then the next process comes in.
        
        ![[Untitled 14 4.png|Untitled 14 4.png]]
        
    - Priority Scheduling;
        
        - Associated a priority level to each process that related to its performance, the ones with the highest priority level, denoted here with a lower number, are dealt with first.
        
        ![[Untitled 15 2.png|Untitled 15 2.png]]
        
        - Any schedules that come later with the same priority level are dealt with in a first come first serve schedule
        
        ![[Untitled 16 2.png|Untitled 16 2.png]]
        
        - It’s possible that low priority processes, such as the 3 here will never get any CPU time, however this can be dealt with by assigning addition priority based on how long the process has been running.
        
        ![[Untitled 17 2.png|Untitled 17 2.png]]
        
    - Round Robin scheduling;
        - This entails a ready queue, treated as a First-In-First-Out, which is iterated over by the scheduler, if the process is completed within the fixed amount of time each process is given, it will be terminated, if not it will be reached again in due course.
    
    ![[Untitled 18 2.png|Untitled 18 2.png]]
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
- Lecture Notes
    
    ==RESEARCH MORE==
    
    ## What is an OS
    
    An OS is an intermediary between the User and the Hardware.
    
    OS goals;
    
    - Execute user programs and make solving user problems easier
    - Make the computer system convenient to use
    - Use the computer hardware in an efficient manner
    
    ## Types of OS.
    
    - A **Stand-alone OS** that works on a desktop computer, laptop, etc.
    - A **Server OS** organises and coordinates how multiple users access and share resources on a network
    - A **Mobile/Embedded OS** resides on a compact ROM or RAM chip on a mobile device or consumer electronic.
    
    |Categories|Operating System|
    |---|---|
    |Stand-Alone|DOS  <br>Windows (95, 98, XP, 8, 10)  <br>Mac OS  <br>Unix  <br>Linux|
    |Server|Windows (NT, 2003, 2008, 2012)  <br>Unix  <br>Linux  <br>Solaris  <br>Netware|
    |Embedded/Mobile|Android  <br>Windows CE  <br>iOS  <br>Palm OS  <br>Blackberry  <br>Symbian  <br>Cisco iOS|
    
    ## About Linux
    
    - Linus Torvalds - Principle author of the Linux Kernel
        - Based on the GNU Unix Kernel
        - Originally developed as a free OS for PC (x86)
    - Being ported to more computer hardware platforms than any other OSs. e.g. Android
    - Ubuntu as one of many Linux distributions with desktop, mobile and server versions
    - [www.linux.org](http://www.linux.org)
    - [www.kernel.org](http://www.kernel.org)
    
    ## Types of OS (response time $ data input)
    
    General categories.
    
    - **Batch**: Execution of jobs by collecting them in a single batch. Efficiency of the system was measured in the throughput
    - **Interactive**: Gives a faster turnaround but required the development of time-sharing software.
    - **Real-Time**: 100% responsive and used in time-critical environments
    - **Hybrid**: Combination of batch and interactive; accepts and runs batch programs in the background when the interactive load is light
    - **Embedded**: small kernel and flexible functions for the product capabilities
    
    ## OS Components
    
    - Memory Resident (Kernel) component
        - Always loaded in memory and running at all time, commonly called the **kernel**
        - Contains essential services required by other parts of the OS and applications. Typically responsible for **managing memory, processes and tasks, and secondary storage**
    - Memory non-resident component
        - Infrequently used programs
        - Software tools
        - Terminal commands
    - Bootstrap program
        - Stored on a ROM chip to start the OS
    
    ## Kernel Mode and User Mode
    
    In modern OS, the CPU spends time in two distinct modes.
    
    - Kernel Mode
        - Can execute any instruction and reference any memory address
        - Crashes in Kernel mode are catastrophic; they halt the entire PC
    - User Mode
        - Code must use APIs to access hardware (Application programming interfaces)
        - Crashes in user mode are always recoverable
        - Most of the code on your computer will execute in user mode
    
    THESE TWO MODES ARE ENFORCED BY THE CPU HARDWARE.
    
    ## Overview of OS
	
	
	  
    ## ==System Calls==
    
    - ==**Programming interface**== ==to the services provided by the OS;==
    - ==_This is basically what you write to request a service like memory from the OS, it’s something the programmer would write, they just have to obey the syntax of API, most details are hidden by API_==
    - ==Typically written in a high-level language (C or C++)==
    - ==Most accessed by programs via a high-level== ==**Application Program Interface (API)**== ==rather than direct system call use;==
    - ==The caller needs to know nothing about how the system call is implemented:==
        - ==Just needs to obey API and understand what OS will do as a result call;==
        - ==Most details of OS interface hidden from programmer by APIs==
    
    ## API - System Call - OS Relationship
    
    INSERT THE GRAPHIC FROM THE POWERPOINT
    
    1111111111111111111111111111111111111111111111111111111
    
    ## Questions (for so far)
    
    Q1. The Operating System gets an input, performs an operation, produces an output, and quits. YES or NO.
    
    NO, this is more like the ALU or something
    
    Q2. The memory resident components of an OS are commonly known as the …
    
    a) kernel ← this one
    
    b) shell
    
    c) bootstrap
    
    d) API
    
    ## Common OS Services
    
    - UI and command execution
    - File system
    - CPU/Process management
    - Memory management
    - I/O management
    - System protection
    
    ![[Untitled 19 2.png|Untitled 19 2.png]]
    
    ## User Interface and Command Execution
    
    - A user interface controls how you enter data/instructions and how information is displayed on the screen
    - Types of UI
        - GUI — Graphical User Interface
        - TUI — Text-based User Interface
        - CLI — Command Line Interface
    - Shell:
        - Command Line UI and command processor that interacts with the kernel
        - UNIX / Linux: C, Bourne, bash and Korn shells
        - Windows: command prompt (cmd), powershell
    - Command Languages - Shell Scripting
        - MS Windows - .BAT files
        - UNIX/Linux - shell scripts (e.g. .sh files)
    
    ## File System Management
    
    File systems represent how data is stored on a storage device.
    
    - OS provides uniform, logical view of information storage
        - Abstracts physical properties to logical storage unit - file
        - Files usually organised into directories (files)
    - A basic file management system provides
        - Tools to copy, move, store, retrieve and manipulate files
        - Information about each file in the system and the tools to access that information
        - Directory structures for each I/O device
        - Security mechanism to protect files and control access
    - Additional file management features
        - Backup, emergency retrieval and recovery
        - File compression
        - Transparent network file access
    
    ## Unix/Linux Files and Directories
    
    - The Linux OS has a ‘hierarchical’ file system which means that directories can contain other directories or files.
    - The root directory “/” is the starting directory, and contains “child directories”, “grandchild directories”, etc. this hierarchical structure resembles an “upside-down tree”
    
    ![[Untitled 20 2.png|Untitled 20 2.png]]
    
    ## ==The File Control Block (FCB)==
    
    - ==FCB has all the information about the file==
        - ==A data structure managed by the OS==
        - ==Resides in the memory of the program that uses the file, not in OS memory==
        - ==Unix/Linux systems call these== ==**inode**== ==structures==
    
    ![[Untitled 21 2.png|Untitled 21 2.png]]
    
    ## File System Layout (How a file system is organised)
    
    File Systems stored on hard disks.
    
    - Disk is divided into 1 or more partitions
    - Sector 0 of disk called the Master Boot Record (MBR)
    - End of MBR has partition table (start & end address of partitions)
    - Each partition has a certain number of blocks
    - Block is the smallest readable or writeable unit which can be addresses (e.g. 4KB)
    - First block of each partition has boot block, loaded by MBR and executed on boot
    
    ![[Untitled 22 2.png|Untitled 22 2.png]]
    
    ## ==Storing Files==
    
    - ==Files can be allocated in different ways:==
        - ==Contiguous allocation==
            - ==Contiguous set of blocks, all bytes together in order==
        - ==Linked Structure==
            - ==Each block points to the next block==
        - ==Indexed Structure==
            - ==An index block contains pointer to many other blocks==
    
    ## Contiguous Allocation
    
    - Allocated files **contiguously** (**touching or connected throughout in an unbroken sequence**) on disk
    
    ![[Untitled 23 2.png|Untitled 23 2.png]]
    
    - Pros:
        - Simple: state required per file is start block and size (find the block + how many blocks after)
        - Performance: entire file can be read with one seek (doesn’t have to search around the disk for fragments of a file)
    - Cons:
        - ==External fragmentation== is a bigger problem (i think this is because if there is a gap between files where nothing can fit it is just lost)
        - ==Usability: user need to know size of a file (why?)==
        - _ask why_
    - Used in CDs, DVDs
    
    ## Linked List Allocation
    
    - Each file is stored as linked list of blocks
        - First word of each block point to next block
        - Rest of disk block is file data
    
    ![[Untitled 24 2.png|Untitled 24 2.png]]
    
    - Pros:
        - No space lost to external fragmentation
        - Disk only needs to maintain first block of each file
    - Cons:
        - Random access is costly (in terms of memory)
        - Overheads of pointers to each file.
    
    ## MS-DOS / Windows File System - FAT
    
    - File Allocation Table (FAT): simple file system that is still being used (e.g. FAT32, exFAT)
    - A variant of a **linked list allocation**
        - FAT stores a linked list of entries
        - One entry corresponds to a storage block
        - It stored information about all the files on the disk
    
    [What is FAT?](https://en.wikipedia.org/wiki/File_Allocation_Table)
    
    ![[Untitled 25 2.png|Untitled 25 2.png]]
    
    ## Indexed Allocation
    
    - Index block contains pointers to each data block of one file object
    - Pros & Cons?
        - Need for an index block
        - Support random access
        - Dynamic access without external fragmentation, but have overhead of index block
    
    ![[Untitled 26 2.png|Untitled 26 2.png]]
    
    ## ==UFS - Unix File System (Index Blocks) ANKI***==
    
    ![[Untitled 27.png]]
    
    ==Unix Inodes:==
    
    - ==**Direct blocks**== ==point to first few blocks of the files==
    - ==A== ==**single indirect**== ==pointer that points to a disk block used as an index block==
    - ==A== ==**double indirect**== ==pointer that points to a disk block used as a collection of pointers to index blocks==
    - ==A== ==**triple indirect**== ==pointer that points to an index block of index blocks of index blocks==
    - ==If data blocks are 4K and block address is 4 bytes==
        - ==12== ==**direct blocks**== ==- 48K reachable directly from the inode==
        - ==A== ==**single-indirect**== ==- 4MB available==
        - ==A== ==**double-indirect**== ==- 4GB available==
        - ==A== ==**triple-indirect**== ==- 4TB available==
    - ==Small files need only the direct blocks==
    - ==Larger files can use indirect blocks==
    - ==Any block can be found with at most 3 disk accesses==
    
    ## How to calculate (optional)
    
    ## Table of all the OS stuff
    
    ## Process Management
    
    **Process management** aka **CPU management**
    
    ==**Process**==
    
    - ==A program being executed==
    - ==a basic unit of work in the OS==
    
    ==Multi-tasking: multiple processes are executed concurrently==
    
    ==General process management activities:==
    
    - Creating and deleting both user and processes
    - Suspending and resuming processes
    - Providing mechanisms for process synchronization
    - Providing mechanisms for process communication
    - Providing mechanisms for deadlock handling
    
    ## What is a process?
    
    - ==Process==: ==A program together with all the resources that are associated with it as it is executed==
        - ==PID (process ID):== unique identifier for each process
    - ==Process context (this is saved what its in the ready state)==
        - All relevant register data including the program counter
        - Allows interruption and restart invisibly
    - Processes can be described as:
        - I/O-bound process — spends more time doing I/O than computations, many short CPU bursts. I/O > CPU
        - CPU-bound process — spends more time doing computations; few very long CPU bursts. CPU > I/O
    
    ## Process Control Block (PCB)
    
    ![[Untitled 28.png]]
    
    PCB: a data structure containing information associated with each process, i.e. context of a process
    
    THIS CONTAINS PROCESS CONTEXT (SEE ABOVE)
    
    - Process state
    - Program counter
    - Other CPU registers
    - CPU scheduling information
    - Memory-management information
    - Accounting information
    - I/O status information
    
    ## Multi-Programming (Multi-Tasking) How? ANKI*****
    
    **Multi-programming/Multi-tasking**: executing many processes concurrently.
    
    - To achieve multi-tasking
        - Choose the process to run in a fair and efficient way: ==Scheduling==
        - Allocate CPU to a process: ==Dispatching==
        - Keep/restore the process information: ==Context Switch==
    - Example causes of context switch
        - Time-slicing: slices the CPU time and dedicates a slot to each process. The CPU may be switched rapidly back and forth between different processes
        - I/O Break: While one program is waiting for I/O to take place, another program is using the CPU to execute instructions.
    
    ## Sharing the CPU during I/O Breaks
    
    - I/O represents a large percentage of a typical programs execution.
    
    ![[Untitled 29.png]]
    
    **CPU burst**: the amount of time the process uses the processor
    
    **I/O burst**: the amount of time the process works on I/O
    
    ## CPU Switch From Process to Process
    
    ![[Untitled 30.png]]
    
    ## Context Switch and Dispatcher
    
    - Context Switch: when CPU switches to another process, the system must save the state of the old process and load the saved state (context) of the new process
    - Dispatcher: the module that gives control of the CPU to the process selected by the Scheduler.
        - Switching the context
        - Switching to user mode
        - Jumping to the proper location in the newly loaded program
        - Basically hands the process over to the CPU after the short-term sch has confirmed for it to be sent there,
    
    ## Process States
    
    - As a process executes, it changes state:
        - new: The process is being created
        - running: Instructions are currently being executed
        - waiting: The process is waiting for some event to occur that isn’t the CPU like I/O
        - ready: The process is waiting to be assigned to a processor
        - terminated: The process has finished execution
    - Example of state changing:
        - Dispatching - Move from ready state to running state
        - Wake-up - Move from waiting or blocked state to ready state
        - Time-out - Move from running state to ready state
        - Process completion - Move from running state to terminated state
    
    ## Diagram of Process State Transition
    
    ![[Untitled 31.png]]
    
    ## Process Queues
    
    Processes migrate among the various queues
    
    - Job Queue - set of all processes in the system
    - Ready Queue - set of all processes residing in main memory, ready and waiting to execute
    - Device Queues - set of processes waiting for an I/O device
    
    ## Process Scheduling
    
    ![[Untitled 32.png]]
    
    ## Schedulers
    
    - Long-term scheduler (or job scheduler)
        - Select which process should be brought into the ready queue
        - Invoked infrequently (seconds, minutes (this is an eternity for a pc)) → May be slow;
        - Controls the degree on multi-programming (depending on how much it decides to let into the ready queue, the more that will need to be processes simultaneously, see support video notes.
    - Short-term scheduler (or CPU scheduler)
        - Selects which process should be executed next e.g. using CPU;
        - invoked VERY frequently (milliseconds) → Must be fast to coordinate time slicing, etc.
    
    ## Scheduling Algorithms
    
    Issues to consider for process selection
    
    - Efficiency
    - Fairness (are some programs being ignored)
    - Priority
    - Context switch overhead (saving time by not loading context)
    
    Three basic scheduling policies:
    
    - ==First-Come, First-Served (FCFS) scheduling==
    - ==Priority Scheduling==
    - ==Round Robin (RR) Scheduling==
    
    ## FCFS Scheduling and Example
    
    First-Come, First-Served scheduling:
    
    - The process that requests the CPU first is allocated the CPU first
    - Average waiting time can be quite long
    
    ![[Untitled 33.png]]
    
    |Process|Wait time (CPU bursts)(ms)|
    |---|---|
    |P1|0|
    |P2|24|
    |P3|27|
    
    Average wait time = (0 + 24 + 27) / 3 = 17ms avg wait.
    
    ## Priority Scheduling and Example
    
    - Priority scheduling algorithm
        - Job with the highest priority is selected
        - A priority is associated with each process, and the CPU is allocated to the process with the highest priority
        - Equal-priority processes are scheduled in FCFS (say two have a level of 3, which ever was there first will be handed to the CPU first out of both)
        - There is no general agreements on whether 0 is the highest or lowest priority, We assume low numbers are high priority here.
        - A major problem with priority scheduling is ==indefinite blocking or starvation==
    
    ![[Untitled 34.png]]
    
    |Process|Wait time (CPU bursts)(ms)|Priority|
    |---|---|---|
    |P1|6|3|
    |P2|0|1|
    |P3|16|4|
    |P4|18|5|
    |P5|1|2|
    
    Average wait time = (6 + 0 + 16 + 18 + 1) / 5 = 8.2ms avg wait.
    
    ## RR Scheduling and Example
    
    - Round Robin Scheduling
        - A small unit of time, called a time quantum, is defined. Generally from 10 to 100 ms in length
        - Ready queue is treated as First-In First-Out queue of processes. New processes are added to the tail of the ready queue, sets a timer to interrupt after on time quantum, and dispatched the process
        - short-term scheduler goes around the ready queue, allocating the CPU to each process for a timer interval of up to 1 time quantum (some processes don’t need to all so get given less obviously)
    
    **Quantum = 20**
    
    ![[Untitled 35.png]]
    
    We see here P2 is only given 17ms because that is all that it needs.
    
      
    
- Lecture Points
    
    _When a system call is made from a process, it crosses from the user mode to the kernel mode and then gets those processes._
    
    _We are covering a model on a non-networked OS._
    
    _File system layout is the layout on a hard disk_
    
    _Each partition is divided into block, the block is the unit to locate a file, files are stored in several blocks_
    
    _How do you read file, sequentially or randomly_
    
    _When a linked list points to 0, it is the last file_
    
    _FAT removes the need for the first word of a block to link to the next_
    
    _A program is static, a process is a dynamic program running._
    
    _CPU can only do one thing at once so things run CUNCURRENTLY not SIMULTANEOUSLY_
    
      
    
- Tutorial Notes
    
    _Q1. Which statement is FALSE?_
    
    _i) Operating system is the system service provider to the application programs_
    
    _  
    ii) Application developers could only access to system calls through the system Application Programming Interface (API).  
    _
    
    _  
    iii) Operating system is also called kernel which stay in the memory when computer system starts.  
    _
    
    _  
    iv)CPU spends time in both kernel and user modes.  
    _
    
    **A1. iii? This question is worded bad**
    
    _Q2. Give one example where the contiguous allocation of file blocks is a suitable data storage strategy._
    
    **A2. Anytime when the users knows the size of the file, or for DVDs where the usually just store one big file like a movie.**
    
    _Q3 (optional). The inode (index node) is a data structure in a Unix-style file system which stores the attributes and disk block locations of the object's data. Suppose one file system has block size as 1K. Disk block numbers can be stored in 4 bytes. Each inode contains 10 direct entries, one singly-indirect entry and one doubly-indirect entry._
    
    _  
    i) What is the maximum file size when one file system has block size as 1K.  
    _
    
    **1000 / 4 x 10 = 2500**_  
    ii) What is the maximum file size when increasing the block size to 4K?  
    _
    
    4KB_  
    iii) Discuss the disadvantages of using a large block size.  
    _
    
    **tbt**
    
    _Q4. Explain what the process control block (PCB) is? Do your research to find out some PID numbers on your computer system._
    
    **A4. It stores all the context for a process such as the program counter and the registers while the process is in the ready state, waiting to be loaded again when the processes is dispatched again, The ‘system’ PID is 4, ‘steam.exe’ PID is 1736, the ‘explorer.exe’ PID is 3680**
    
    _Q5. Explain the function of the ready queue._
    
    **A5. Process that are ready wait here to be scheduled by the short-term scheduler and then to be dispatched, processer here are ready to be operated and processed by the CPU**
    
    Question 6. Consider the following set of processes.
    
    |   |   |   |
    |---|---|---|
    |Process|Priority|CPU Time(ms)|
    |P1|2|20|
    |P2|1|12|
    |P3|4|3|
    |P4|3|15|
    
    i) Draw a diagram or write out the sequence showing how FCFS would schedule the processes. What is the average waiting time?
    
    **ai. p1 = 0, p2 = 20, p3 = 32, p4 = 35  
    0 + 20 + 32 + 35 / 4 = 21.75ms  
    **
    
    _ii) Assuming a lower number represent a higher priority, draw a diagram or write out the sequence showing how the Priority-based scheduling algorithm would schedule the processes. What is the average waiting time in this case?_
    
    **aii. p2 = 0, p1 = 12, p4 = 32, p3 = 47  
    0 + 12 + 32 + 47 / 4 = 22.75ms  
    **
    
    _iii) Assuming a quantum as 5ms, draw a diagram or write out the sequence showing how RR would schedule the processes. What is the average waiting time in this case?_
    
    **aiii.**
    
    **p1 = 0ms (15 burst time remaining)**
    
    **p2 = 5 (7)**
    
    **p3 = 10 (0) term**
    
    **p4 = 13 (10)**
    
    **p1 = 18 (10)**
    
    **p2 = 23 (2)**
    
    **p4 = 28 (5)**
    
    **p1 = 33 (5)**
    
    **p2 = 38 (0) term**
    
    **p4 = 40 (0) term**
    
    **p1 = 45 (0) term**
    
    _Q7. For RR scheduling algorithm, briefly explain the advantage and disadvantage of using a smaller quantum._
    
    **Advantage = faster response time which is essential or an interactive environment**
    
    **Disadvantage = Unnecessarily frequent context switching leading to more overheads and less overall throughput**
    
- Further Reading
    
    _Silberschatz, Operating System Concepts._
    
    10.1.1 Magnetic Discs
    
    Common disk drives spin at 5,400, 7,200, 10,000, 15,000 RPM. Disk speed has two parts. The transfer rate is the rate that data flows between the disk and the computer and. The **positioning time** (or random-access time), consists of two parts: the time necessary to move the disk are to the desired cylinder, called the **seek time**, and the time necessary for the desired sector to rotate to the disk head, called **rotational latency.** Typical disks can transfer several megabytes of data per second, and they have **seek times** and **rotational latencies** of several milliseconds.
    
    Because the disk flies on an extremely thin cushion of air (measured in microns), there is a danger the arm will touch the disk surface, if this happens, it is called a head crash and if this happens the entire drive must be replaced.
    
    Disks are removable so we can fit as many as needed, there are other types of removable disks such as CD, DVD and flash drives (which are a type of SSD)
    
    The disk drive is attached to the computer through the I/O bus. Data transfers on a bus are carried out by special electronic processors called controllers. A disk controller is built into each disk drive. To perform a disk I/O operation, the computer places a command into the host controller, typically using memory mapped I/O ports, the host controller then sends the command to the disk controller and the controller operates the disk drive to carry out the command. Disk controllers have a cache, Data transfer at the disk drive happens between the cache and the disk surface and data transfer to the host.
    
    10.1.2 Solid-State Disks
    
    SSDs have the same characteristics as traditional hard disks, however since they are not mechanical and have no moving parts, they have no seek time or latency, they also use less power, However they are more expensive and have less capacity and may also have a shorter life span.
    
    Because SSDs can be much faster than HDD, standard bus interfaces can cause a major limit on throughput. Some SSDs are designed to connect directly to the system bus (PCI, for example)
    
    ## 10.2 Disk Structure
    
    Modern magnetic disk drives are addressed as large one-dimensional arrays of logical blocks, where a logical block is the smallest unit of transfer. The size of a logical block is usually 512bytes, some disks can be **low-level formatted** to have different block sizes such as 1,024bytes. The one-dimensional array of logical blocks is mapped onto the sectors of the disk sequentially, Sector 0 is the first sector, of the first track on the outermost cylinder. The mapping proceeds in order through that track