Computer memory stores information, such as data and programs for immediate use in the computer. The term memory is often synonymous with the term primary storage or main memory.

Computer memory operates at a higher speed when compared to storage which is slower but less expensive and higher in capacity. Besides storing opened program, computer memory serves as a disk cache and write buffer to improve the reading a writing performance. OSs borrow both RAM capacity for caching so long as not needed by running software. If needed the, contents of the computer memory can be transferred to storage; a common way of doing this is through memory management technique called virtual memory.

Modern computer memory is implemented as semiconductor memory, where data is stored within memory cells built from MOS transistors and other components on an integrated circuit. There are two main kinds of semiconductor memory: volatile and non-volatile

# Volatile

Volatile memory is computer memory that requires power to maintain the stored information. Most modern semiconductor volatile memory is either static RAM (SRAM) or dynamic RAM (DRAM) DRAM dominates for desktop system memory. SRAM is used for CPU cache. SRAM is also found in small embedded systems requiring little memory.

SRAM retains its contents as long as the power is connected and may use a simpler interface, but requires six transistors per bit. Dynamic RAM is more complicated for interfacing and control, needing regular refresh cycles to prevent losing its contents, but uses only one transistor and one capacitor per bit, allowing it to reach much higher densities and much cheaper per-bit costs.

# Non-volatile memory

NV memory can retain the stored information even when not powered.

# Management

Proper management of memory is vital for a computer system to operate properly. Modern OS’ have complex systems to properly manage memory. Failure to do so can lead to bugs, slow performance, or takeover by viruses and malware.

### Bugs

- Memory leak

This occurs when a program requests memory from the OS and never returns the memory when it is finished with. A program with this bug will gradually require more and more memory until the OS runs out.

- Segmentation Fault

This results when a program tries to access memory that it does not have permission to access, generally a program doing so will be terminated by the OS

- Buffer Overflow

This occurs when a program writes data to the end of its allocated space and then continues to write data beyond this to memory that has been allocated for other purposes. This may result in erratic program behavior, including memory access errors, incorrect results, a crash or a breach of OS security and are the basis for malware.

### Virtual Memory

This is a system where physical memory is managed by the OS typically with assistance from a memory management unit. It allows multiple types of memory to be used. For example, some data can be stored in RAM while other data is stored on a hard drive, functioning as an extension of the cache hierarchy. This offers several advantages. Computer programmers no longer need to worry about where their data is physically stored or whether the user’s computer will have enough memory. This OS will place actively used data in RAM, which is much faster than hard disks. When the amount of RAM is not sufficient to run all the current programs, it can result in a situation where the computer spends more time moving data from RAM to disk and back than it does accomplishing tasks; this is known as thrashing.

### Protected memory

This is a system where each program is given an area of memory to use and is prevented from going outside that range. if the OS detects that a program has tried to alter memory that does not belong to it, the program is terminated. This way, only the offending program crashes, and other programs are not affected by the misbehavior.