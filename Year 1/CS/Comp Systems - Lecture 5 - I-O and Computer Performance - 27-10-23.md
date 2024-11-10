- Lecture Notes
    
    [Powerpoint](https://learn-eu-central-1-prod-fleet01-xythos.content.blackboardcdn.com/5d2cb9c32e9d7/16092238?X-Blackboard-S3-Bucket=learn-eu-central-1-prod-fleet01-xythos&X-Blackboard-Expiration=1700244000000&X-Blackboard-Signature=mm93FnW9YCNl6iVac0Q6cA%2FtNjLmY20q33balyAq0eY%3D&X-Blackboard-Client-Id=163100&X-Blackboard-S3-Region=eu-central-1&response-cache-control=private%2C%20max-age%3D21600&response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27CS1CS-lec5-%2520IO%2520module%2520and%2520Computer%2520Performace23.pdf&response-content-type=application%2Fpdf&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEF8aDGV1LWNlbnRyYWwtMSJIMEYCIQDGSBFWvTcZQYBar4pMxmNbH5NKsGtqv7GApd8HfgsZ5AIhANEoJZGVfvUv8dptXeMRsr3nQNA0eGW7s%2FVMPRjFSun%2BKsYFCKj%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQAxoMNjM1NTY3OTI0MTgzIgz%2BVoRzVuJw3t02R1UqmgXhGAUACeUsM6Kg6%2FJz5BRZIhmaJP82sKY2Nim0ioYVHB%2FKa0cZKvt1kFAkjGfERdjl7fV%2FUg1OIRw7B4jCcFwpK0%2BmWV%2Fu684A0NPnD3B%2FEY9FD6IzD2wLbpM3J2vxQLqakPKdRyT%2Bb1DCg0%2BcQXbt2A%2Fd1vG0afUGHZTuLMIYS%2FfHsCAffYEBWACrQtkpKekzqxEIQ74PyhFAVADtlVTefrYt5yr4j%2FXroFw%2F1574AGj4MwQ95ggGXErNKNsOUHph4%2F7%2F5sI2rtLQwoa3ugWpHvjdJ%2Bp0GE6d0B8%2BlEY4Zx%2FJ1icJWb61sIwOjrbbrvX2zwEZAB3bmiC2OyY2Xrz84m39MPEENsQKHXayK34WRbZpr7DwldV%2Br6EizUtPdS0IZd0JtGpPW39fqMJPmvcTvrZyRo9QvBSey%2BaYxaLHeohv%2BqdVG2KqC79S%2Bp7560U43bMr%2F2VLZZz49ofq4WNNNfqVimPXWkNU0LkSWhng7gynETLzE%2FmpYg38NY3CLX0jKMqmo6Xkk%2FH0gsrTrT1WxEaVmExZKRhDB2wK%2B9owNJgZQb2%2BpY374SBIoAK31hwGOakzxj43sf%2BgeiVoqR7pmA4Y7Rc3CXBc%2BAFGV3z5uTmhzcpTDD%2FBFqtBqH5G%2BHERnPd0WN2eRhWyv3BIgmVGxhLJNfSEMpPJSddxPknJsVytqOveE1H9mmL%2FqvBB3P%2BEpNZGWqPHcNmT1Ring9vX4flREfgVdmeoPHBZYTK4kruh%2FxnF6htvsvHiocuOnAIubPtqbc%2FWk5wtyRI26TADU9EIrZZpu3MTUaIO3cZFmyKDML7vJgY7FMrsIesxzFAnZGFtHHzTGVBYQ8ta9Ig48JZh%2BK9Qrl5Y7wI1jWQrfRFY7XC9PbVKjZcw6%2B%2FdqgY6sAGhZ2ZqII3sCj%2BwhYKDSiYQeFKtO0jTeega83HYySFAv1beiM8J%2FV1sYLwkCA2L5eRS1aEJRS9u7jqCkvzN0gMU%2ByGN%2BqaxIbh9LDYuc5UckSIbOAZfHkYWqI97I2lNZJQwJ2%2B1nEFxQWM9PAQGlao5boN71REvyAHaN%2FNPhkWGSKiccGWCeeC3Fe9Lt9fJ5q2zeXXYQqUOQ4qMq1K9EPgRiFrlaBQeQcIIvDNMOrUKeQ%3D%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20231117T120000Z&X-Amz-SignedHeaders=host&X-Amz-Expires=21600&X-Amz-Credential=ASIAZH6WM4PLXWXJ4CE6%2F20231117%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Signature=1d31362a680e5aa4237e64992d05b107f3ec999239eb5db0b92b659ec0d2e177)
    
    ## **Top-level view of computer system - I/O module**
    
    ![[Untitled 43.png|Untitled 43.png]]
    
    ## **I/O Speed and Variety of I/O devices**
    
    I/O Speed: Data rate measured by bps (bits per second) e.g 100Mbps;
    
    ![[Untitled 1 23.png|Untitled 1 23.png]]
    
    ## Processor - I/O Speed Mismatch
    
    - CPU and I/O speed mismatch: simply as
        - 1GHz microprocessor: 1 billion load/store instructions per seconds, or 4,000,000 KB/s data rate
        - I/O devices data rates range from 0.01 to 2,000,000 KB/s
    - Input: device may not be ready to send data as fast as the processor loads it.
        - Also, might be waiting for human to act
    - Output: device may not be ready to accept data as fast as the processor stores it
    
    ## I/O controllers to connect CPU and Memory
    
    ![[Untitled 2 23.png|Untitled 2 23.png]]
    
    ## I/O Controller Functions
    
    - Communicates with the CPU (e.g. status reporting)
        - Recognizes messages addressed to it and accepts commands from the CPU.
    - Provides the necessary registers and controls to perform a direct memory transfer
    - Data Buffering:
        - Provides a buffer where the data from memory can be held until it can be transferred to the device;
        - Copies data from its buffer to the device/from the CPU to its buffer
    - Physically controls the device
    
    ## Instruction Set Architecture for I/O
    
    CPU must instruct carious I/O devices to read and write data
    
    **Two ways for I/O addressing:**
    
    - Special Input and Output Instructions
        - Separate I/O address space
        - Special instructions to access I/O devices
        - Also called port-mapped I/O
    - Memory-Mapped Input and Output
        - A portion of the memory address space dedicated to communication paths to Input or Output devices
        - I/O is similar to reading/writing memory.
    
    ## Special I/O Instruction Example (1)
    
    ![[Untitled 3 21.png|Untitled 3 21.png]]
    
    ## Special I/O Instruction Example (2)
    
    ![[Untitled 4 19.png|Untitled 4 19.png]]
    
    ## Memory Mapped I/O Example
    
    - Certain addresses are not regular memory; instead they correspond to registers in I/O devices.
    - This allows the same instructions to be used for I/O as are used for reading from and writing to memory.
    - e.g 0xFFFF0004 is the address for the keyboard. To read from the keyboard.
    
    ![[Untitled 5 19.png|Untitled 5 19.png]]
    
    ## Three I/O Techniques
    
    Data transfer to and from the peripherals may be done in any of the three possible ways
    
    - Three Techniques
        
        - ==Programmed I/O==
            - ==CPU controlled I/O==
        
        - Input Driven I/O
            - I/O hardware signals
        - Direct Memory Access Controllers (DMA)
            - Method for transferring data between main memory and a device that bypasses the CPU
    
    ## Option 1: Polling
    
    Polling: The process of periodically checking the status of and I/O device to determine the need to serve the device
    
    Run and I/O instruction:
    
    - Processor executes an I/O instruction by issuing a commands to the appropriate I/O controller
    - Each device is given a unique identifier or addess
    - I/O controller performs the requested action and sets the appropriate bits in I/O status registers
    - The processor periodically checks the status of the I/O controller until it finds the operations is completed
    - One word transfer per I/O instruction.
    
    Problem: wasteful to have processor spend most of its time ‘spin-waiting’ for I/O to be ready
    
    ## Option 2: Interrupt Driven I/O
    
    - Solution: Interrupt program when I/O ready, return when done with data transfer
        - No repeated CPU checking of the device
        - I/O controller interrupts when ready.
    - Read Operation
        - CPU issues a read command to an I/O controller
        - The I/O controller gets data from a peripheral whilst the CPU does other work
        - I/O controller interrupts the CPU when data ready
        - CPU requests data
        - I/O controller transfers data
    
    ## Interrupt Terminology
    
    - Interrupt request : a hardware signal sent to the processor
    - Interrupt lines : one or more special control lines to the CPU, e.g. IRQ0 - system timer
    - Interrupt handlers - OS
        - Program that services the interrupt
        - Also knows as an interrupt routine or part of device driver in the OS
    - Context Switch - OS
        - Saved registers of a program before control is transferred to the interrupt handler
        - Allows program to resume exactly where it left off when control return to interrupted program
    
    ## System information on Windows.
    
    ![[Untitled 6 16.png|Untitled 6 16.png]]
    
    ## Use of Interrupts
    
    Causes the CPU to alter its normal from of instruction execution
    
    - Frees CPU from waiting for events
    - Provides control for external I/O initiation
    
    Notify that an event has occurred:
    
    - Signal notifies that an external event
        - button click, printer ready or buffer full.
    - Indicate abnormal event (CPU originates for notification and recovery)
        - illegal operation, hardware error
    - Allocate CPU time generated by internal processor timer
        - time sharing
    
    ## Instruction Cycle with Interrupts
    
    - An I/O interrupt is asynchronous with respect to instruction execution:
        - I/O interrupt can happen in the middle of any given instruction
        - I/O interrupt does not prevent any instruction from completion
    
    ![[Untitled 7 15.png|Untitled 7 15.png]]
    
    ## Option 3: Direct Memory Access
    
    - Interrupt driven I/O and programmed I/O require active CPU intervention
        - Transfer rate is limited
        - CPU is tied up
    - DMA (Direct Memory Access) is the answer
        - Transferring large blocks of data
        - Direct transfer to and from memory
        - CPU not actively involved in transfer itself
    - DMA takes over from CPU for I/O
    
    ## DMA Controller
    
    ![[Untitled 8 15.png|Untitled 8 15.png]]
    
    ## DMA Operation
    
    DMA controller: a specialised controller that transfers data between an I/O device and memory independent of the CPU.
    
    - CPU instructs DMA controller
    - CPU carries on with other work
    - DMA controller deals with transfer
    - DMA controller sends ==interrupt== when finished
    
    ## DMA - Discussion
    
    - Without DMA
        - Every word travels over system bus twice: first to CPU, then again to destination
    - With DMA
        - Transfers data directly between memory and it’s destination
    - Both programmed I/O and interrupt I/O works best with lower-bandwidth device
    - DMA works best for high-performance devices, e.g. hard disks, graphics card, network card etc.
    
    ![[Untitled 9 14.png|Untitled 9 14.png]]
    
    ## About Computer performance
    
    Main factors influencing performance of computer system:
    
    - Processor
    - Memory
    - Bus
    - Input/Output modules and peripherals
    - System programs, e.g OS and compilers
    
    ## Response Time and Throughput
    
    - Response Time
        - The time between the start and completion of a task
        - Including all aspects e.g. processing, I/O, OS overhead, idle time. also referred to as execution time.
    - Throughput
    - PCs are more focused on response time, versus servers, more focused throughput
    - If mostly concerned with response time:
    
    ![[Untitled 10 14.png|Untitled 10 14.png]]
    
    ## CPU Execution Time
    
    - CPU Execution time (or CPU time) accounts for the time CPU is computing the given program, including operating system routines executed on the program’s behalf
        - Time spend on processing a given job, discount I/O time, other jobs’ shares
        - Comprises user CPU time and system CPU time
        - A true measure of processer/memory performance
    - CPU time depends on the program with is executed, including: types of instructions executed and their frequency of usage.
    
    ![[Untitled 11 12.png|Untitled 11 12.png]]
    
    ## CPU Clock and CPU Time
    
    Computers constructed using a clock that runs at a constant rate and determines when events can take place in the hardware. These discrete time intervals are called clock cycles.
    
    - Clock rate (frequency): cycles per second
        - e.g. 4.0GHz = 4000MHz = $4.0 * 10^9$﻿Hz
    - Clock cycle time: duration of a clock cycle
        - e.g. 250ps = 0.25ns
    
    ![[Untitled 12 12.png|Untitled 12 12.png]]
    
    - CPU time for a program
    
    ![[Untitled 13 11.png|Untitled 13 11.png]]
    
    ## Number of clock cycles for a program
    
    Could be assume that # of cycles equals # of instructions
    
    - This assumption is incorrect in general
    - Different instructions take different amount of time on different machines
        - Multiplication takes more time than addition
        - Floating point operations take longer than integer ones
        - Accessing memory takes more time than accessing registers
        - For example, MIPS has 3 instruction types:
            - Data movement, Arithmetic and Logic, and Control
    
    ## CPU Clocking (1/2)
    
    - Single-Cycle CPU: All stages of an instruction are completed within one clock cycle.
        - The clock cycle is made sufficient long to allow each instruction to complete all stages without interruption within one cycle.
        - An instruction cycle with five-stages:
    
    ![[Untitled 14 11.png|Untitled 14 11.png]]
    
    ## CPU Clocking (2/2)
    
    - Multiple-cycle CPU: Only one stage of instruction per clock cycle.
        - The clock is made as long as the slowest stage.
    
    ![[Untitled 15 8.png|Untitled 15 8.png]]
    
    - Several significant advantages over single cycle execution: Unused stages in a particular instruction can be skipped OR instructions can be pipelined (overlapped).
    
    ## Instruction Count and CPI
    
    - CPI: Clock Cycles Per Instruction
        - Average number of clocks cycles per instruction for a program
        - An overall metric for comparing two implementations of the same ISA
    
    Suppose there are n types instructions:
    
    - Total Instruction Count: number of machine instructions executed
    - CPI$_i$﻿: number of cycles required per instruction type i
    - Instruction count$_i$﻿: number of executed instructions of type i
    
    ![[Untitled 16 7.png|Untitled 16 7.png]]
    
    ## Calculating CPI Example
    
    ![[Untitled 17 7.png|Untitled 17 7.png]]
    
    ## Calculating CPI - another way
    
    Suppose we have n types instructions:
    
    - CPI$_i$﻿ for each individual type instruction (add, sub, lw, etc.)
    - Frequency$_i$﻿ of each individual type of instruction
    
    To get final CPI (the weighted sum):
    
    - multiply these two for each instruction and add them up
    
    ![[Untitled 18 7.png|Untitled 18 7.png]]
    
    ## Calculating CPI Example
    
    ![[Untitled 19 7.png|Untitled 19 7.png]]
    
    ## CPU Execution Time
    
    - CPI provides one way of comparing two different implementations of the same instruction set architecture;
    - Since the number of instructions executed for a program will be the same;
    - CPU execution time T needed to execute a program is
    
    ![[Untitled 20 7.png|Untitled 20 7.png]]
    
    ## Comparison Examples
    
    ![[Untitled 21 6.png|Untitled 21 6.png]]
    
    ## MIPS and FLOPS
    
    - MIPS: Millions Instructions Per Second (MIPS rate)
    
    ![[Untitled 22 6.png|Untitled 22 6.png]]
    
    MIPS doesn’t account for:
    
    - Differences in ISAs between computers
    - Differences in complexity between instructions
    
      
    
    - MFLOPS: Millions Floating-Point Operations Per Second
    
    ![[Untitled 23 6.png|Untitled 23 6.png]]
    
    ## Example - MIPS rate
    
    ![[Untitled 24 6.png|Untitled 24 6.png]]
    
    ## Doing Laundry
    
    - Ann, Brian, Cathy, Dave
    - each one has a load of dirty clothes
    
    ![[Untitled 25 5.png|Untitled 25 5.png]]
    
    ## Doing Laundry: Separating into stages
    
    - 4 Laundry Stages:
    
    ![[Untitled 26 5.png|Untitled 26 5.png]]
    
    ## Sequential Laundry
    
    ![[Untitled 27 4.png|Untitled 27 4.png]]
    
    ## Pipelined Laundry
    
    ![[Untitled 28 3.png|Untitled 28 3.png]]
    
    - Pipelining does not improve latency of single tasks but it improves throughput of entire workload
    - Multiple tasks operate simultaneously using different resources
    - Potential speedup = Number of pipe stages
    - Time to “fill” pipeline and time to “drain” it reduces speedup
    - Suppose new Folder takes 20 minutes. How much faster is pipeline?
    - Pipeline rate is limited by slowest pipeline stage
    - Unbalanced lengths of pipe stages reduce speedup
    
    ## Pipelining Introduction
    
    - Pipelining is a technique for implementing instruction-level parallelism within one processor.
    - Pipelining improves performance by increasing instruction throughput
        - Executes multiple instructions in parallel
        - Each instruction has the same latency
        - Potential speedup = Number of pipeline stages
    
    ## MIPS instruction cycle
    
    Five stages, one step per stage
    
    1. IF: ==I==nstruction ==F==etch from memory
    2. ID: ==I==nstruction ==D==ecode & Register Read
    3. EX: ==EX==ecute operations or calculate address
    4. MEM: Access ==MEM==ory operand
        1. Load: Read Data from MEMory
        2. Store: Write Data to MEMory
    5. WB: ==W==rite results ==B==ack to register
    
    ![[Untitled 29 3.png|Untitled 29 3.png]]
    
    - Every instruction executes in the same number of steps, also called pipeline “stages”, so some will sometimes go idle.
    
    ## Simplified MIPS32 Instruction Datapath
    
    ![[Untitled 30 3.png|Untitled 30 3.png]]
    
    - Datapath: the hardware that performs all the required operations, for example, ALU, registers, and internal buses
    
    ## Pipelined Execution Representation (option)
    
    ![[Untitled 31 3.png|Untitled 31 3.png]]
    
    Perform several operations in the same cycle, e.g.
    
    - Fetch one instruction while another one reads or writes data
    - Increment the PC and add registers at the same time
    
    ![[Untitled 32 3.png|Untitled 32 3.png]]
    
    ## Pipeline Hazards
    
    Situations that prevent starting the next logical instruction in the next clock cycle
    
    - Structural Hazards
        - Required resource is busy (i.e hardware support contraints)
        - e.g. Read and Write register in the same cycle
    - Data Hazard
        - Need to wait for previous instruction to complete its data read/write (i.e data not ready due to instruction dependency)
        - e.g An instruction uses the result of the previous
    - Control Hazard
        - Deciding on control action depends on previous instruction (i.e unable to determine next action)
        - e.g. One of the branch registers is used to store the result of a previous add
- Tutorial
- Further Reading