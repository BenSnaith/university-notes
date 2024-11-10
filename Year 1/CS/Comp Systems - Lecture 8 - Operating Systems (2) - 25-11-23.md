- Support Video Notes
    
    One of the primary roles of the OS, is managing the memory, when you open a program, at least some part of it is being loaded into the memory, once that process has completed, it’s memory space is de-allocated meaning that something else can occupy that part in memory.
    
    With programs and data entering and leaving memory, it is important to ensure no program can access memory outside of its allocated space, there is also quite often a queue of waiting programs, since there is often a greater demand for memory than a system can fully satisfy.
    
    This is what the OS manages when we are talking about memory management.
    
    Lets assume for this explanation, that an entire program has been loaded into memory, that isn’t always the case as it won’t always fit, but we are going to imagine that it has for the sake of the example.
    
    The space in memory that this program occupies is divided up into 4 parts:
    
    1. Code: these are the instructions that will be followed as the program executes
    2. Static Data: this comprises global variables, although the values here will change, the quantity of the variables wont so this component will never grow or shrink, the values will just change.
    3. Heap: contains objects that are created at the program is executed, unlike our static data, the number and the complexity of the object can vary, consequently, the heap varies in size.
    4. Stack: contains method calls and associated local variables, each time a new method is called, that method call is added to the stack, again the number of active methods can grown and shrink so the stack also varies in size.
    5. Space: space is allocated between the stack and the heap to allow for the growth of either
    
    Since multiple processes are likely to be taking place at any given time, and since the demand for memory typically exceeds supply, memory needs to be carefully managed, and there are various strategies to support this.
    
    **Fixed-size partitioning** involves splitting memory into sections these sections don’t change size although they are not necessarily the same size as one another, and a process is typically placed into the first available partition, or the smallest available that it can fit into.
    
    This leads to some wasted memory as processes won’t fit perfectly into their allocated space, there is also **variable-spaced/dynamic partitioning,** as a process is loaded into memory, the exact amount required is allocated to it, when a process then leaves memory it might then be replaced by one that requires less space, so we now have a gap, and as time goes on, we will have a number of gaps, and memory is externally fragmented, so from time to time the contents of memory are rearranged to leave one large gap, this is called **compaction, swapping** is a means of addressing the problem of memory being of limited size.
    
    P42 is currently in memory.
    
    This process is currently concerned with the transfer of images from a digital camera.
    
    I/O, being far slower than the CPU, means this process can be swapped for P43.
    
    P43 requires the CPU for a large number of calculations.
    
    Then we have **paging**. memory is split into small chunks of equal size called **page frames** processes are split into small chunks called **pages** a page can be assigned to any page frame, the pages to don’t need to be in order, or stored together as a process. The OS at all times maintains a list of all the empty frames, this way the problem of fragmentation is avoided completely, since each page fills its page frame, except maybe the very very last frame.
    
    **Virtual Memory** uses pages in this way, lets say we need 4GB of memory for a process, and only 2GB are available, once the memory dedicated to the OS itself is catered for. Secondary Storage (SSD, Disk) can behave as though it is memory acting as an extension, it is not really memory which is why it is called Virtual Memory. In understanding this concept, we must be clear on the terms, **Physical address** and **Virtual Address,** Physical addresses refer to specific individual locations in MAIN MEMORY, Virtual Addresses which will be referenced by the program, might point to a physical address in main memory, or might point to SECONDARY STORAGE. We will use this piece of program code to show this in action
    
    ```Java
    LOAD R1, 42
    ADD R3, R2, R1
    LOAD R4, 43
    ```
    
    We have some general purpose registers: R1, R2, R3, R4
    
    As well as some virtual addresses: 42, 43
    
    The first line requires that the contents of VIRTUAL address 42, are loaded into Register 1.
    
    We consult a page table that maps the virtual addresses, the physical addresses
    
    |VIRTUAL ADD|PHYSICAL ADD|
    |---|---|
    |42|04|
    |43||
    |…|…|
    
    We see here that VIRTUAL address 42, maps to the physical address 04, so the contents of physical address 4, are loaded into Register R1, instruction complete.
    
    The next instruction deals only with registers so the page table isn’t needed.
    
    Next we load Register R4, with the contents of Address 43, this is again a virtual address so we got to our page table to find it’s physical address, as we see the Physical address is empty, so this data is on secondary storage, and therefore must be loaded into a physical address in memory as part of a swap. Upon doing so the page table is updated with the new physical address and the data is loaded into Register R4.
    
    |VIRTUAL ADD|PHYSICAL ADD|
    |---|---|
    |42|04|
    |43|08|
    |…|…|
    
    This process is slower than simply having enough main memory to contain everything for two reasons. First access speeds on main memory are faster than that of secondary storage, second the process of moving data between main memory and secondary storage, as well as updating the page table, does take time. If the OS is continually performing swaps, this is called **thrashing**, and is to be avoided as it stops it doing anything valuable, It can be avoided by way of good page replacement algorithms, a reduction in the number of processes, or the installation of additional main memory.
    
- Lecture Notes
    
    [Powerpoint](https://learn-eu-central-1-prod-fleet01-xythos.content.blackboardcdn.com/5d2cb9c32e9d7/12546262?X-Blackboard-S3-Bucket=learn-eu-central-1-prod-fleet01-xythos&X-Blackboard-Expiration=1700319600000&X-Blackboard-Signature=IQsNLmsqbQWe866wdisjrb6%2Bp49JkMqBIgPx4wMpVlE%3D&X-Blackboard-Client-Id=163100&X-Blackboard-S3-Region=eu-central-1&response-cache-control=private%2C%20max-age%3D21600&response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27CS1CS-Lec8-OS2-2022%25281%2529.pdf&response-content-type=application%2Fpdf&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEHIaDGV1LWNlbnRyYWwtMSJGMEQCIAWHNLYP3wmH0L6uVkfFQmqYGYGWu9QSwAJ6kDpUqXKYAiAT3GFbqaJ%2BnrPAiu2SVhArgOrjPkVIwEehrcJARx1MiSrHBQi7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAMaDDYzNTU2NzkyNDE4MyIM08tMlAih3SzYNOKaKpsFfgimVHTI3g8xWpskXL581fD0MLyQOfMORqBvqmxpdomhI8yQazjOet0dLCQ2dCuj5P4Rw4MKYNqNyUP7lmO04%2FONn2sheeLsPeJ9YKpuZIi70xBnEwgmwZugDJxsZTroN%2BGu%2BLOqXYaHyZC02dbs1zEbhRxTGgd0trtKZzOi%2B97MUfwSkQAtld7w1ZVj7xviIJUk4Ngl2SLqIDAwkUL%2BnmdX%2FxacHA9BoQMzwQhUCy0nLqRgIX9n5b7WJongwGy8rFEVgAD0iJeMCy4XT05tQsVGebhHEWNKxK6Ymqeqvfq2Yl9L87BF%2B97zNpOQ2izDNNSEkBtDe53JorKobG09GssU8Gg7yfOm%2BS7QeK5zSdKnvZEY2cCom3k3G8xAx6uZbWRac4Hoj6S82%2BfANaPP%2FicrWNwPu09adbVZ68%2FI1YHO8ulz5xWwOyLOrPDnrV5URyt1YxK%2B79EIGbloiTk1m2St4iWyhhfzye5eHcSK92mU%2Bh%2FCftBF%2B%2FfBK0LaqkC3ew5Rqv0qMdjz2eh%2FxTRczJsgFNur4gec6jWpfeJXuqDLv%2FAwAX3Bm%2B2YS4lBzyHDrQnZG661znz94Kor4jN2VWZB8%2BtgXIPlKa05TWJ4JB5jzboVk%2FciDGsdCYb4x6%2BcEFYBnS9mK56HYJCpp%2FKwhEwihv1NvEJkAi%2FcpwNvkWu2KMb1zoyZzNKae01GPkcve%2FhZQfFYR9zj1HcRm9qVI%2BNbC%2BSstUMe2YBLGaukAixSdMsimXpgYYqv%2FB120pJZLBdMh%2FvnUiYIPd%2FMGH97iTaBt6icF0Y%2BJeaBj01AKWIsHF5SX2YrE3OZ2%2BFZVoJ8e6M3crtBBUAEVIxtaauCL4ObPLBV6PnYZj68vjGA4UH9H3LdZMIlZloGPDDZkOKqBjqyAbxUgkLXEItUPE%2FHyLK3ORDHRRViYz%2F6T9Uqv2y9s43UNGcLGHBZJGAnbOFfPtUoxd9If%2FZQyzwOJVnKyllCIobF8JLPGwlbyOymbYUB7vyb7XZw3nkC2z%2Fi9K6sfuJ5GObUsUoQdLvl%2Bx2UuH5%2FK7CSMWyMa6gSPxfthLTNcBZnRg5FCNJyWhX4FPV5jVWDD%2BfIAzqLkMlZROCUasfCD3rzsaxUIVJqQNFa1jxMlXB%2B8sQ%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20231118T090000Z&X-Amz-SignedHeaders=host&X-Amz-Expires=21600&X-Amz-Credential=ASIAZH6WM4PLW7CCZBFE%2F20231118%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Signature=316bce57334fcb1ac147fa9cfb04faa469de4368198c28f31b1cf5cf8aa27b4f)
    
    ## OS Memory Management
    
    - ==Maintains queues of waiting programs==
    - ==Allocates memory to programs to be loaded==
    - ==De-allocates a program’s memory space upon completion==
    - ==Keeps track of memory==
        - Identifies programs loaded into memory
        - Amount of space each program uses
        - Available remaining space
        - Prevents programs from reading and writing memory outside of their allocated space
    - ==Usually implemented with virtual storage==
    
    ## Address space for a process
    
    - A process’s address space logically contains 4 regions:
        - ==stack==: local variables, function parameters, return addresses, grows downward
        - ==heap==: resizes dynamically during process run time, grows upwards
        - ==static data==: global variables, does not grow or shrink
        - ==code==: loaded when program starts, does not change.
    
    ![[Untitled 36.png|Untitled 36.png]]
    
    ## Memory Management Requirements
    
    For multi-program OS:
    
    - ==Sharing and Protection==
        - Processes share one physical memory space
        - Processes should not collide in physical memory
        - Prevent access to private memory of other processes
        - Kernel data protected from user programs.
    - ==Address Translation (mapping)==
        - When translation exists,
            - ==process using virtual (logical) addresses==
            - ==memory uses physical addresses==
        - Ability to translate accesses from one address space (==virtual==) to a different one (==physical==)
    
    ## Address Binding Time
    
    - Compile time
        - Specify the physical memory locations during compiling; Used by some simple OSes e.g. DOS
    - Load Time
        - Determine physical addresses when all modules are combined into a load module and loaded into memory
    - Execution Time
        - Bind addresses when a module is executed (to allow flexibility in moving process during execution); implemented by most modern OSs
    
    ## Memory Management for Multi-program
    
    - Uni-program
        - Memory split into two
            - One for OS
            - One for current programs
        - No issues for Translation and Sharing/Protection
    - Multi-program
        - “User” part is sub-divided and shared among active processes.
    
    ![[Untitled 1 16.png|Untitled 1 16.png]]
    
    Top: Uni-program  
    Bottom: “User” part is sub-divided  
    
    From 0x00000000 to 0xFFFFFFFF which is the max of the 32-bit (full), there is some arbitrary point where the user section and the OS section split.
    
    ## Memory Management Strategy: Fixed-sized Partitioning
    
    - **Problem**: multi-programs in one physical memory space.
    - **Solution:** ==**Partitioning**==
        - Splitting memory into sections to allocate to processes (including OS)
    - **Fixed-sized partitions**
        - May not be equal size
        - Process is fitted into smallest possible hole (best fit)
        - Some wasted memory (worst thing ever)
        - Leads to variable sized partitions
    
    ## Fixed Partitioning: Equal-size partitions
    
    ![[Untitled 2 16.png|Untitled 2 16.png]]
    
    See the process that need the 7 fits into the 8, but leaves 1M of space, this is fragmentation, this will never be used and is then essentially useless, worst thing ever, computer explode kill self, also what if we have a process bigger than the partition size, bad bad bad bad bad bad bad bad bad bad bad computer die.
    
    ## Fixed Partitioning: Unequal-size partitions
    
    ![[Untitled 3 14.png|Untitled 3 14.png]]
    
    Here we have the same problem as equal-size partitions but now where the does the 9M go, there is no room for it, do we have to wait for a 16M to terminate, that isn’t very efficient
    
    ## Memory Management Strategy: Dynamic Partitioning
    
    **Solution:** ==**Allocate exactly the required memory to a process - Variable-sized partitioning**==
    
    ![[Untitled 4 13.png|Untitled 4 13.png]]
    
    We have a certain amount assigned to the OS and the rest is free game.
    
    ## Dynamic Partitioning - Effect
    
    ![[Untitled 5 13.png|Untitled 5 13.png]]
    
    ## Variable-Sized Partitioning Discussion
    
    - **Problem**: form many small holes in memory (external ==fragmentation== because it is throughout the entire section of memory and not just a pre-determined smaller piece.
        - When a process finishes or is blocked, leave a free memory partition;
        - A new process may be smaller than the out process, this leads to a small space being left free;
        - Eventually have lots and lots of holes and useless space (this is also super bad wtf
    - **Solution**:
        - ==Compaction - From time to time go through memory and move all the holes into one free block (c.f. disk de-fragmentation)==
    
    ## ==Memory Management Strategy: Swapping==
    
    ==**Problem**====: The limited size of memory & multi-programs==
    
    **==Solution==**==:==
    
    - ==Swapping:==
        - ==some or all of the previous processes are moved to disk;==
        - ==Reserve a swap space (page file) on disk==
    
    ==Why swapping works?==
    
    - ==Is it common for many processes in memory waiting on long I/O burst==
    - ==Processor is much faster than I/O==
    - ==Memory holds multiple processes and CPU can move to another process when one process is waiting==
    
    ## ==Memory Management Strategy: Paging==
    
    ==Strategy: A process does not need to be contiguous (continually allocated) space!==
    
    - ==Split memory into equal sized small chunks - page frames==
    - ==Split a process into equal sized chunks - pages==
    - ==Pages could be assigned to any available page frames==
    - ==OS maintains the list of free frames==
    
    ==Notes:==
    
    - ==At most, the wasted space in memory for one process is a fraction of the last page==
    
    ## Pages and Frames
    
    |   |   |   |
    |---|---|---|
    ||Process|Memory|
    |Unit|Page|Frame|
    |Address|Logical|Physical|
    |Size|4 to 8KB|4 to 8KB|
    
    - Page as a unit of transfer from disk to physical memory
    - Logically, each process has it’s collection of pages
    - A page will be loaded into a page frame
    - The total number of pages can exceed the number of frames (physical memory). Therefore, now all pages are put in page frames.
    
    ## Mapping Virtual Memory to Physical Memory
    
    - Divide into equal sized chunks (about 4KB - 8KB )
    - Any chunk of Virtual Memory assigned to any chunk of Physical Memory (”frame”)
    
    ![[Untitled 6 10.png|Untitled 6 10.png]]
    
      
    
    ## Virtual Memory and Paging
    
    ==Virtual Memory==: provides a program with an illusion of a very large main memory
    
    - Each process thinks it has all the memory to itself (selfish)
    - Working sets of “pages” reside in main memory — others reside on disk
    - So some pages are in frames, the physical memory and the pages that aren’t being used at this very moment are on the disk, Virtual Memory
    
    - ==Allows to share memory==
        - Different physical pages frames can be be allocated to different processes (==sharing==)
        - OS uses ==page tables== to keep track.
    - ==Allows to protect programs==
        - One process has one page table
        - A process can only touch pages in its own page table (==protection==)
    
    ## Page Table
    
    - ==A== ==page table== ==is an OS data structure which contains the mapping of virtual to physically addresses, i.e. page no and frame no.==
    - ==Each process has its own page table==
    - Page table keeps track of what is in memory and what is still out on hard disk in virtual
    
    ![[Untitled 7 9.png|Untitled 7 9.png]]
    
    Notice how in the page table, pages without a frame are just not being ran in physical memory, that it okay, it just isn’t needed right now so why load it into memory
    
    ## Pages Table for Address Translation
    
    ![[Untitled 8 9.png|Untitled 8 9.png]]
    
    028A → 328A, I think itis calling this as an individual time from the larger page, or just showing how it maps over.
    
    ## Address Translation Function
    
    - Logical address, e.g. 32-bit address; 4K page size (4k=2$^1$﻿$^2$﻿)
    
    ![[Untitled 9 8.png|Untitled 9 8.png]]
    
    So like what I said in the last caption, we have the page number + an extension to reference a particular memory address.
    
    - Use page number as index
    - Translation Function
        - Physical Offset = Virtual Offset
        - Physical Frame Number: PageTable [Page Number]
    
    ![[Untitled 10 8.png|Untitled 10 8.png]]
    
    ## Address Translation: Example
    
    Logical address = 0x3D7A1
    
    3D = Page ID (we will use this as an index to get the frame)
    
    7A1 = Offset (this maps identically)
    
    Physical address = 0x2F3577A1 (7A1 the same)
    
    ## Memory Management Unit
    
    ![[Untitled 11 6.png|Untitled 11 6.png]]
    
    - Memory Management Unit (MMU): a hardware component performs virtual address to physical address run-time mapping through page table. (does what we saw in the last example, mapping one to the other).
    - Some registers are used to support the mapping
    - Also Translation Lookaside Buffer (TLB) is used at the cache of page table
    
    ## Paging System and Swapping
    
    - Paging almost solves the Fragmentation problem: all chunks same size, so holes can be used for anything.
    - Page Table is the essence of Virtual Memory: Working set of “pages” reside in main memory - others reside on the disk. working pages in physical, all others on disk.
    - To grow a process. ask the OS.
        - If there are unused page frames, OS uses them first
        - If not, OS swaps some old pages to disk
    - OS must reserve “==Swap Space==” on disk for each process
    - ==Swap space: the space on disk created by OS for the full virtual memory space of a process.==
    
    ## Page Table and Swap Space
    
    ![[Untitled 12 6.png|Untitled 12 6.png]]
    
    ## Page fault (Page not in memory)
    
    Page fault: Required page is not in memory
    
    - Operating system must swap in the required page.
    - May need to swap out a page to make space.
        - Choose some other page belonging to a program and transfer it onto the disk if **dirty** (disk copy is not up-to-date)
        - If **clean** (disk copy is up-to-date), overwrite that data in memory
        - Choose the page to evict based on one **page replacement policy**
    - And update that program’s page table to reflect the fact that it’s memory somewhere else.
    
    ## Steps in Handling a Page fault
    
    ![[Untitled 13 5.png|Untitled 13 5.png]]
    
    ## Thrashing
    
    - Continuously swapping between the disk and the memory is called **Thrashing.**
    - OS Spends all of its time swapping
    - Little or no real work is done
    - Disk light is on all the time
    - Solutions
        - Reduce number of processes running
        - Fit more memory
        - **Good page replacement algorithms**
    
    ## Page Replacement Policies
    
    - Why do we care about Replacement Policy?
        - The cost of being wrong is high: must go to disk
        - Must keep important pages in memory, not toss them out
    - FIFO (First in, First out)
        - Throw out oldest page.
        - Fair — let every page live in memory for the same amount of time
        - Bad — because throws out pages that are heavily used instead of pages that are infrequently used.
    - LRU (Least Recently Used)
        - Replace page that hasn’t been used for the longest time
        - This makes so much sense
        - Programs have locality: if something is not used for a while, it is unlikely to be used in the future.
        - LRU is often used and considered to be good.
    
    ## Example: FIFO
    
    - Suppose we have 3 page frames we can use and 4 virtual pages (A, B, C, D) and the page reference stream like:
        - A B C A B D A D B C B
    - Consider FIFO Page replacement
    
    ![[Untitled 14 5.png|Untitled 14 5.png]]
    
    FIFO: 7 faults
    
    ## Example: LRU
    
    - Consider the following stream: A B C A B D A D B C B
    - LRU performs as follows
        - 5 faults
    
    ![[Untitled 15 3.png|Untitled 15 3.png]]
    
    ## Virtual Memory Access Problem
    
    - Problem: each virtual memory access needs two memory accesses
        - 1 memory access to Page Table in memory per virtual address
        - 1 memory access to data
    - Observation: since **locality** in pages of data, there must be locality in virtual address translations of those pages
    - Solution: use a small cache for frequently used page table entries to make translation faster
    - For historical reasons this cache is called a TLB. Translation Look-aside buffer
    
    ## Why does Virtual Memory work?
    
    - Locality of Reference
        - Most memory references are confined to small region
        - Well-written program in small loop, procedure or function
        - Data likely in array and variables stored together
    - Working set
        - Number of pages sufficient to run a program correctly, i.e. satisfy locality of a particular program
    
    ## Virtual Memory vs Cache
    
    - Cache as a quicker storage between CPU and main memory in order to speed up memory access
    - Virtual memory increases amount of perceived storage
        - Independence from the configuration and capacity of the memory system
        - Low cost per bit compared to main memory
    
      
    
    |   |   |
    |---|---|
    |Cache|Virtual Memory|
    |Block or Line|Page|
    |Miss|Page Fault|
    |Block Size: 32-64B|Page Size: 4K-8KB|
    |Write Thru or Back|Write Back|
    
    ## Memory Hierarchy (Recap)
    
    ![[Untitled 16 3.png|Untitled 16 3.png]]
    
    Memory management system presents users with the illusion of a very large and fast memory — Virtual Memory supported by OS
    
    ## I/O Management in OS
    
    - Dealing with a wide variety of I/O devices.
        - Delivery different amounts of data: by block and character
        - At different speeds measured by data rate bps (bits per second) range from 0.01 to 200,000 KB/s but all slower than CPU and RAM
        - Various methods to control them
    - OS manages I/O devices by supporting a standard, internal interface
        - A Device Driver is device-specified code in the Kernel that interacts directly with the system hardware
        - kernel I/O systems can interact easily with different devices
    - Handle recoverable errors, maintain security of the devices and optimize the performance of the I/O system.
    
    ## I/O Hardware and Software
    
    ![[Untitled 17 3.png|Untitled 17 3.png]]
    
    ## Device Drivers
    
    Software modules in OS to handle a particular device
    
    - OS and driver communication
        - Commands and data between OS and device drivers
    - Driver and hardware communication
        - Commands and data between driver and hardware
    - Driver operations
        - Initialize devices
        - Interpreting commands from OS
        - Schedule multiple outstanding requests
        - Manage data transfers
        - Accept and process interrupts when transfer done or transfer error.
        - Maintain the integrity of driver and kernel data structures
    
    ## Interrupt Types
    
    - Most modern hardware uses interrupts to communicate with OS.
    - Based on the sources, interrupts can be categorized as:
        - I/O interrupt: generated by an I/O controller, to signal normal completion of an operation or to signal a variety of error conditions.
        - Timing control: generated by a timer to signal OS with time-sharing policy
        - Hardware faulty: generated due to a hardware failurer
        - Software interrupt: generated due to the appearance of some condition as a result of an instruction execution, such as overflow, and illegal instruction, etc.
    - Multiple Interrupts: requests may happen at the same time
        - Sequential interrupt processing: disabling interrupt request while an interrupt is being processed, all interrupts will be processed sequentially.
        - Nested interrupt processing: all the interrupts may be assigned different priorities, top priorities can be processes first.
    
    ## Servicing and Interrupt - OS
    
    1. Lower priority interrupts are held until higher priority interrupts are complete.
    2. Suspend programs in progress
    3. Save context, including last instruction executed and data values in registers, in the stack are in memory
    4. Branch to interrupt handler (Interrupt Service Routine) program
    5. After interrupt routine complete, restore the context of program it was working on and resume execution.
    
    ## Servicing an Interrupt
    
    ![[Untitled 18 3.png|Untitled 18 3.png]]
    
      
    
    ## Kernel I/O Subsystem
    
    Device-Independent I/O Software
    
    - Uniform interfacing for device drivers to make all the devices look more or less the same with uniform API and naming.
    - Allocating and releasing dedicate devices
    - I/O Scheduling: organise I/O requests in a good order, e.g. disk scheduling.
    - Buffering: a memory area maintains by the kernel to store data transferring between two devices, e.g. printer buffer.
    - Error reporting and I/O protection
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
- Lecture Points
    
    The heap is for things such as, if logical condition true, create this object, because this is created while running, it goes to the heap.
    
    logical address ≠ physical address this is why we need address mapping
    
    Compile time → used by uni-program computers such as dos as it can only run one program at once.
    
    Execution time → your code uses the logical addresses.
    
    ![[Untitled 19 3.png|Untitled 19 3.png]]
    
    ![[Untitled 20 3.png|Untitled 20 3.png]]
   
