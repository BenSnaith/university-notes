- Lecture Notes
    
    [Powerpoint](https://learn-eu-central-1-prod-fleet01-xythos.content.blackboardcdn.com/5d2cb9c32e9d7/15971516?X-Blackboard-S3-Bucket=learn-eu-central-1-prod-fleet01-xythos&X-Blackboard-Expiration=1700244000000&X-Blackboard-Signature=HEuwoVo%2FDnpnKQtXuUmNcDUrexUGz436C3CVu6hufj0%3D&X-Blackboard-Client-Id=163100&X-Blackboard-S3-Region=eu-central-1&response-cache-control=private%2C%20max-age%3D21600&response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27CS1CS-lec4-%2520CPU%2520memory%2520and%2520bus2023.pdf&response-content-type=application%2Fpdf&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEF8aDGV1LWNlbnRyYWwtMSJIMEYCIQDGSBFWvTcZQYBar4pMxmNbH5NKsGtqv7GApd8HfgsZ5AIhANEoJZGVfvUv8dptXeMRsr3nQNA0eGW7s%2FVMPRjFSun%2BKsYFCKj%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQAxoMNjM1NTY3OTI0MTgzIgz%2BVoRzVuJw3t02R1UqmgXhGAUACeUsM6Kg6%2FJz5BRZIhmaJP82sKY2Nim0ioYVHB%2FKa0cZKvt1kFAkjGfERdjl7fV%2FUg1OIRw7B4jCcFwpK0%2BmWV%2Fu684A0NPnD3B%2FEY9FD6IzD2wLbpM3J2vxQLqakPKdRyT%2Bb1DCg0%2BcQXbt2A%2Fd1vG0afUGHZTuLMIYS%2FfHsCAffYEBWACrQtkpKekzqxEIQ74PyhFAVADtlVTefrYt5yr4j%2FXroFw%2F1574AGj4MwQ95ggGXErNKNsOUHph4%2F7%2F5sI2rtLQwoa3ugWpHvjdJ%2Bp0GE6d0B8%2BlEY4Zx%2FJ1icJWb61sIwOjrbbrvX2zwEZAB3bmiC2OyY2Xrz84m39MPEENsQKHXayK34WRbZpr7DwldV%2Br6EizUtPdS0IZd0JtGpPW39fqMJPmvcTvrZyRo9QvBSey%2BaYxaLHeohv%2BqdVG2KqC79S%2Bp7560U43bMr%2F2VLZZz49ofq4WNNNfqVimPXWkNU0LkSWhng7gynETLzE%2FmpYg38NY3CLX0jKMqmo6Xkk%2FH0gsrTrT1WxEaVmExZKRhDB2wK%2B9owNJgZQb2%2BpY374SBIoAK31hwGOakzxj43sf%2BgeiVoqR7pmA4Y7Rc3CXBc%2BAFGV3z5uTmhzcpTDD%2FBFqtBqH5G%2BHERnPd0WN2eRhWyv3BIgmVGxhLJNfSEMpPJSddxPknJsVytqOveE1H9mmL%2FqvBB3P%2BEpNZGWqPHcNmT1Ring9vX4flREfgVdmeoPHBZYTK4kruh%2FxnF6htvsvHiocuOnAIubPtqbc%2FWk5wtyRI26TADU9EIrZZpu3MTUaIO3cZFmyKDML7vJgY7FMrsIesxzFAnZGFtHHzTGVBYQ8ta9Ig48JZh%2BK9Qrl5Y7wI1jWQrfRFY7XC9PbVKjZcw6%2B%2FdqgY6sAGhZ2ZqII3sCj%2BwhYKDSiYQeFKtO0jTeega83HYySFAv1beiM8J%2FV1sYLwkCA2L5eRS1aEJRS9u7jqCkvzN0gMU%2ByGN%2BqaxIbh9LDYuc5UckSIbOAZfHkYWqI97I2lNZJQwJ2%2B1nEFxQWM9PAQGlao5boN71REvyAHaN%2FNPhkWGSKiccGWCeeC3Fe9Lt9fJ5q2zeXXYQqUOQ4qMq1K9EPgRiFrlaBQeQcIIvDNMOrUKeQ%3D%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20231117T120000Z&X-Amz-SignedHeaders=host&X-Amz-Expires=21600&X-Amz-Credential=ASIAZH6WM4PLXWXJ4CE6%2F20231117%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Signature=259546538480db5b1fcbd8e0651a622384b721e3da4b9ca0baf98c8692b3f702)
    
    ![[Untitled 42.png|Untitled 42.png]]
    
    ## CPU design
    
    ![[Untitled 1 22.png|Untitled 1 22.png]]
    
    - Consists of ALU, CU registers and interconnection components etc.
    - Many varieties of design but most with the Von Neumann architecture.
    - Integrated Circuit (IC) implementing billions of transistors on one chip
    - Digital logic is the underlying technology of designing CPU by logic gates an digital circuitr.
    
    ## ALU and CU
    
    - Control Unit (CU): Contains circuitry that uses electrical signals to direct the entire computer, “brain within the brain”
        - Aid to load data/instructions into CPU from other storage, interpret then, and instruct to execute stored program instructions.
        - Manages and coordinates all the units of the computer.
        - With controllers from translating, pipelining, multicycle etc.
    - Arithmetic & Logic Unit (ALU): A digital circuit that performs Arithmetic (add, sub, etc,) and Logical (and, or, not) operations.
        - Load data from input registers and store results in an output register.
        - ALU normally have full adder(s) and other calculation circuits.
    
    ## Transistors → Logic Gates
    
    - Logic gate: electronic circuit that produces an output signal as a simple Boolean operation on its input signals.
    - The basic building blocks of any digital system.
    
    ![[Untitled 2 22.png|Untitled 2 22.png]]
    
    ## Logic gates → Adder
    
    - 1-bit Half Adder
        - Adds two single binary digits A and B. It has two outputs, sum (S) and carry (C)
    
    ![[Untitled 3 20.png|Untitled 3 20.png]]
    
    - 1-bit Full Adder and 4-bit Full Adder
        - Adds two single binary digits A and B also C the value carried in.
    
    ![[Untitled 4 18.png|Untitled 4 18.png]]
    
    ## Multiplexer - data selector
    
    Multiplexer is a combinational logic circuit which allows only one input at a particular time to general the output, i.e Selects between several input signals and forwards it to a single output line
    
    ![[Untitled 5 18.png|Untitled 5 18.png]]
    
    In a CPU, data being written to memory might come from one of the sources — from a register, from the result of a calculation, etc — so a multiplexer would be used to select data from the appropriate source.
    
    ## Decoder
    
    A decoder is a combinational logic circuit that converts binary information from n input lines to a maximum of 2$^n$﻿ unique output lines.
    
    ![[Untitled 6 15.png|Untitled 6 15.png]]
    
    One example of using decoders in computers is to decode addresses for memory.
    
    1. i.e 32-bit for 2$^3$﻿$^2$﻿ memory unit ; 64-bit for 2$^6$﻿$^4$﻿
    
    ## Registers
    
    - Small storage locations within the CPU
    - A collection of registers known as a register file
    - Size in bits or bytes (not MB like memory), typically several dozen in current CPUs
    - Size and numbers all depend on the CPU design
    - Usages and Registers
        - Scratchpad for currently executing program;
        - Holds data needed quickly or frequently
        - Stores information about status of CPU and currently executing program e.g. Address of next program instruction, Signals from external devices
        - Hold intermediate results or data values, e.g. loop counters.
    
    ## Special-Purpose Registers
    
    ![[Untitled 7 14.png|Untitled 7 14.png]]
    
    - ==**Program Counter (PC) Register**==
        - ==Instruction pointer==
    - ==**Instruction Register (IR)**==
        - ==Stores instructions fetched from memory==
    - ==**Status Registers**==
        - ==Status of CPU and currently executing programs==
        - ==Flags (1-bit Boolean variable) to track sth like arithmetic carry and overflow, power failure, internal computer error==
    - ==**Memory Address Register (MAR)**==
    - ==**Memory Data Register (MDR)**==
        - ==Memory Buffer Register (MBR)==
    
    ==**General-purpose registers:**== ==used to store temporary data and address within the microprocessor. e.g. accumulator==
    
    ## Instruction and Instruction Set
    
    - The language understood by the computer’s hardware, referred to as its machine language.
    - Instruction:
        - The words of the computer’s language
        - Instructions are encoded in binary
        - An elementary operation in a programming language
    - Instruction Set:
        - The complete collection of instructions that are understood by a CPU
        - The set of operations that the computer can perform
        - **RISC (Reduced Instruction Set Computer) e.g ARM, MIPS**
        - **CISC (Complex Instruction Set Computer) e.g X86**
    
    ## Instruction Representation
    
    - Instruction format:
        - The way the different operations are encoded into binary numbers
        - Contains two types of information
            - What has to be done by the instruction: **operation code (opcode)**
            - With what data to do it: **data field (oprand)**
    - In machine code each instruction has a unique bit pattern
    - For human consumption a symbolic representation is used: **assembly language**
        - e.g add, sub, load
    
    ## Instruction Set Architecture (ISA) Examples.
    
    - MIPS
        - Stanford MIPS commercialized by MIPS technologies was owned by Imagination Technologies but sold recently
        - Small instruction set: See MIPS reference tear-out card
        - Large share of embedded core market: in consumer electronics, network/storage equipment, cameras, printers
    - X86
        - A large instruction set, variable-length instruction
        - Instruction set evolves with backward compatability
        - Dominant in PC
    - ARM
        - Small instruction set created by British company ARM Holdings
        - Dominant in smart phones.
    
    ## MIPS Architecture
    
    - Registers
        - 32-bit general-purpose registers
        - Preceded by $ in assembly language instruction
        - Special registers and floating point registers
    - Instructions
        - Instructions are all 32-bits i.e fixed length
        - Three types of instruction formats: R, I, J
        - The instruction set is small: a typical RISC
    - Data Types
        - Byte (8-bit), halfword (2 bytes), word (4 bytes)
        - An integer requires 1 word (4 Bytes) of storage
        - A character requires 1 byte of storage
    - Reference Sheet
        - [http://inst.eecs.berkeley.edu/~cs61c/resources/MIPS_Green_Sheet.pdf](http://inst.eecs.berkeley.edu/~cs61c/resources/MIPS_Green_Sheet.pdf)
    
    ## Instruction Fetch-Execute Cycle
    
    - Fetch the instruction
    - Increment the Program Counter
    - Decode the instruction
    - Fetch the operands
    - Execute the operation
    - Store the results
    - Repeat forever
    
    ![[Untitled 8 14.png|Untitled 8 14.png]]
    
    ## Memory Connection
    
    - Receives and sends data
    - Receives addresses (of locations)
    - Receives control signals
    
    ![[Untitled 9 13.png|Untitled 9 13.png]]
    
    ## Memory
    
    - Memory consists of a number of locations each of which can store a piece of information
    - Each location has a number, called its address by which programs can refer to it
    - All memory locations in a memory contain the same number of bits
    - **Word:** the natural unit of organisation of memory
        - The size of word is typically equal to the number of bits used to represent an integer and to the instruction length
        - Words are typically a group of bytes
        - Typically 32-bits or 64-bits for modern general-purpose computers.
    
    ![[Untitled 10 13.png|Untitled 10 13.png]]
    
    ## Addressing Unit: Byte & Word
    
    In some systems, addressable unit is the word. However, most systems allow addressing at the byte level, therefore K bits of an address allow 2$^k$﻿ addressable units.
    
    - Byte-addressable: capable of reading/writing any individual byte.
    
    ![[Untitled 11 11.png|Untitled 11 11.png]]
    
    - Word-addressable: capable of reading/writing one word.
    
    ![[Untitled 12 11.png|Untitled 12 11.png]]
    
    ## Byte ordering
    
    Byte ordering (endianness): the sequential order of multi-bytes values. It is another major architectural consideration.
    
    - BIG-ENDIAN: the most significant byte of a multi-byte data items always has the lowest address, while the least significant byte has the highest address e.g. ARM processor
    - LITTLE-ENDIAN: the least significant byte of multi-byte data item always has the lowest address, while the most significant byte has the highest address e.g. Intel Processor
    - Example : **1A3628DC****$_1$**﻿**$_6$**﻿
    
    ![[Untitled 13 10.png|Untitled 13 10.png]]
    
    ## RAM: Random Access Memory
    
    - Random: any memory location can be accessed in the same amount of time regardless of its position in the memory
    - DRAM (Dynamic RAM)
        - Most common, cheap, less electrical power, less heat, smaller space
        - Slower and Volatile: must be refreshed (recharged with power)
        - Used for main memory
    - SRAM (Static RAM)
        - Faster and more expensive than DRAM
        - Volatile
        - Does not need refresh circuits
        - Used for cache memory for high-speed memory access
    
    ## Transistor/Capacitor → Memory Cell
    
    ![[Untitled 14 10.png|Untitled 14 10.png]]
    
    ## A Four-Word Memory: Four bits per Word in a 2D Organisation
    
    ![[Untitled 15 7.png|Untitled 15 7.png]]
    
    ## DIMM example
    
    256MB Dual In-Line Memory Module organised for 64-bit word with 16 16M x 8-bit RAM chips (eight chips each side)
    
    A newer example:
    
    **DDR4 SDRAM 16 GB ( 2 x 8 GB ) DIMM 240-pin:**
    
    **DDR4:** Double Data Rate Type 4
    
    **SDRAM:** synchronous dynamic random-access memory
    
    ![[Untitled 16 6.png|Untitled 16 6.png]]
    
    ## MAR and MDR
    
    To read
    
    - The address is put in MAR
    - The memory is enabled for a read
    - The value is put in MDR
    
    To write
    
    - The address is put in MAR
    - The data is put in MDR
    - The Write Enables signal is asserted
    - The value in MDR is written to the location specified
    
    ![[Untitled 17 6.png|Untitled 17 6.png]]
    
    ## Memory Enhancements
    
    - Memory is slow in comparison to CPU processing speed!
        - 1GHZ CPU: 1 cycle in 1 nanosecond
        - RAM: access time normally 50 nanoseconds
    - Method to improve memory accesses
        - Wide Path Memory Access
            - Retrieve multiple bytes instead of 1byte/word at a time
        - Memory Interleaving
            - Partition memory into subsections, each with its own address register and data register
        - Cache Memory
    
    ## Memory caching
    
    - Mismatch between processor and memory speeds leads us up to add a new level: a memory cache
    - Implemented by the same IC technology as CPU: e.g. SRAM, faster but more expensive than DRAM
    - Caches work on the principles of temporal and spatial locality
        - Temporal locality: if you use it now, chances are we will want to use it again soon
        - Spatial locality: if we use a piece of memory, chances are we will use the neighboring pieces soon
    
    ## Cache
    
    - Cache is small amount of fast memory sitting between normal main memory and CPU
    - It may be located within the CPU chip or module
    - Cache is a copy of a subset of main memory
    - Cache controller is used to manage the retrieval, storage, and delivery of data to and from cache memory
    - Cache operations:
        - CPU requests contents of memory location
        - Check cache for this data
        - If present, get from cache (fast)
        - If not present, read required block from main memory to cache
        - Then deliver from cache to CPU
    
    ## Cache terminology
    
    - Blocks: The minimum unit of information that can be either present or not present in the cache, also called cache lines; normally 8 to 64 bytes.
    - Tags: a field that contains the address information required to identify a block.
    - Cache hit: cache block is valid and contains proper address so read desired word.
    - Cache miss: nothing in cache is the appropriate block, so fetch from memory.
    - Hit Ratio: ratio of hits out of total requests.
    
    ## Cache and Main Memory
    
    ![[Untitled 18 6.png|Untitled 18 6.png]]
    
    ## Cache operations
    
    - Block replacement policy: governs the choice of which block is freed up for the new block and fetch desired data from memory when cache miss.
    - Write policy: how to update a block with writing operations
        - Write Through
            - All writes go to main memory as well as cache
            - Multiple CPUs can monitor main memory traffic to keep local (to CPU) cache up to date
            - Lots of traffic
            - Slows down writes
        - Write Back
            - Updates initially made in cache only
            - Update bit for cache slot is set when update occurs
            - If block is to be replaced, write to main memory only if update bit is set
            - I/O must access main memory through cache
    
    ## Performance Advantages
    
    - Hit ratios of 90% common
    - 50%+ improved execution speed
    - Caching works due to the locality of reference
        - Most memory references confined to small region of memory at any given time
        - Well-written program in small-loop, procedure or function
        - Data likely in array
        - Variable stored together
    
    ## Step-by-Step Use of Cache - Hit
    
    ![[Untitled 19 6.png|Untitled 19 6.png]]
    
    ## Step-by-Step Use of Cache - Miss
    
    ![[Untitled 20 6.png|Untitled 20 6.png]]
    
    ## Multilevel Cache Example
    
    ![[Untitled 21 5.png|Untitled 21 5.png]]
    
    ## Memory Hierarchy
    
    - Registers
        - In CPU ( less than 1KB )
        - Registers accessed on nanosecond timescale
    - Cache
        - One or more levels with top level(s) within CPU
        - Sizes from n KB to n MB
    - Main Memory
        - Larger capacity (~GB)
        - Access time ~ 50-100 ns
    - External Memory
        - Backing store
        - Hard Disk and Tape (huge capacity, virtually limitless)
        - Slow: runs milliseconds
    
    ## The Memory Hierarchy
    
    ![[Untitled 22 5.png|Untitled 22 5.png]]
    
    ## Bus
    
    - Bus: a shared communication channel
        - Parallel set of wires for data and synchronization
    - Group of electrical conductors for carrying signals from one location to another
        - Bus line: each conductor in the bus
        - Bus width: the number of channels/lines in one bus, e.g. 32-bit bus
    - Three kinds of signals
        - Data, Address, Control Signals
    
    ![[Untitled 23 5.png|Untitled 23 5.png]]
    
    ## Data Bus
    
    - Carries Data
        - Remember that there is no difference between “data” and “instruction” at this level
        - two-way transport
    - Bus Width
    - Data Bus Width is a key determinant of performance
        - 8, 16, 32, 64 bit
        - e.g. If data bus is 16 bits wide & each instruction is 32 bits long — processor must access the memory twice during each instruction cycle!
    
    ## Address Bus
    
    - Identify the source or destination of data
    - A number of wires indicate the address of data to be accessed
    - Address bus width determines maximum memory capacity of system (the number of memory location the CPU can address)
    
    ## Control Bus
    
    - Control timing and information
        - Controls access to the data and address lines
        - Timing signals indicate the validity of data and address information
    - Typical control lines include
        - Memory read/write signal
        - I/O Port read/write signal
        - Transfer Acknowledgement
        - Bus request/grant
        - Interrupt request/acknowledgement
        - Clock signals
    
    ## A Memory Read Operation
    
    ![[Untitled 24 5.png|Untitled 24 5.png]]