- Lecture Notes
    
      
    
    ![[Untitled 40.png|Untitled 40.png]]
    
    ![[Untitled 1 20.png|Untitled 1 20.png]]
    
    ![[Untitled 2 20.png|Untitled 2 20.png]]
    
    ## The CPU
    
    - The central processing unit or ‘brain’
    - It is responsible for fetching, decoding and executing program instructions as well as performing mathematical and logical calculations
    - Speed is measured in GHz (gigahertz)
    - 32 or 64 bit
    - Multiple cores
    - AMD and Intel major manufacturers
    - Pins on bottom fit into ZIF (zero insertion force) sockets
    - Require a heat sink and fan to cool
    
    ## What it does…
    
    - Fetch
    - Decode
    - Execute
    - INCREMENT COUNTER
    - Writeback
    
    ## Motherboard chipset
    
    - Control movement of data between the CPU, memory, storage and input and output devices.
    - Northbridge - Fast for CPU, memory and graphics.
    - Southbridge - Slower for disks and I/O devices.
    - Requires cooling - fan, water
    
    ## Computer Bus
    
    A bus is a communication system that transfers data between components inside a computer.
    
    - In some systems it’s a single bus combining the functions of a data bus to carry information, an address bus to determine where it should be send, and a control bus to determine its operation.
    - The technique was developed to reduce costs and improve modularity, and although popular in the 1970s and 80s, more modern computers use a variety of separate buses adapted to more specific needs.
    
    ![[Untitled 3 18.png|Untitled 3 18.png]]
    
    ## Northbridge and Southbridge
    
    - The Northbridge connects directly to the CPU & to the ‘working’ memory, so it has to be fast.
    - The Southbridge is slower, dealing with I/O and communication to storage off of the motherboard.
    
    ## Memory
    
    - ROM
        - Read only memory
        - Stores the firmware to start the computer
        - Non-volatile
    - RAM
        - Random access memory
        - Fast storage for programs and data when the computer is running
        - Volatile
    - EPROM
        - Erasable Programmable ROM
        - Like normal ROM it retains its contents when power is off, but you can amend its contents.
        - Early ones erased by UV light, but they were expensive to construct & really need to be hauled out to be erased, so now electrically-erasable ones are used instead.
    
    ## RAM
    
    - Random Access Memory
    - Computer memory that can be written to and accessed in any order.
    - Used to contain both instructions and data for whatever you are doing on the computer that the time.
    - Fast communication between RAM & the CPU that acts on the instructions
    
    ## Power Supply
    
    - The PC components works at a much lower voltage so we use a step-down transformer
    - In early home computers - the Amstrad (Alan Sugar) the power supply was in the monitor as a cost-cutting measure - no separate one for the system box, it drew its power from the monitor.
    
    ## Graphics Cards
    
    - A graphics cards has it’s own computing power - a graphics co-processor - designed specifically for image handling. They are useful for graphics-intensive applications - like playing games!
    
    ## I/O Devices
    
    ![[Untitled 4 17.png|Untitled 4 17.png]]
    
    Input
    
    - Keyboard
    - Mouse
    - Touchscreen
    - Light pen
    - Tablet
    - Microphone
    - Trackball
    - Webcam
    
    Output
    
    - Screen
    - Printer
    - Loudspeaker
    - Headphones (can combine input and output, mic and headphones)
    
    ## Bluetooth
    
    ![[Untitled 5 17.png|Untitled 5 17.png]]
    
    ## USB
    
    - Universal Serial Bus is an industry standard that establishes specifications for cables and connectors and protocols for connection, communication and power supply between computers, peripherals and other computers.
    
    ## Rear Connectors
    
    ![[Untitled 6 14.png|Untitled 6 14.png]]
    
    ## Early storage
    
    - Early storage: the punch card, paper tape, early electronic disk packs.
    - Sinclair ZX81 had 1 Kilobyte of RAM, add on pack gave it 16 Kilobyte
    - 1 Gigabyte hard drives cost £1,000 in 1990
    
    ## Main storage today
    
    - Hard disk - now available up to several TB
    - Portable storage - memory sticks up to portable hard disks
    - CD and DVD writers/re-writers
    - Server-based storage
    - Cloud storage
    
    ## Hard disks
    
    - File systems control the actual physical organization of data within the storage medium.
    - They also handle the logical organization of that data.
    
    ## File System & Disk Layout
    
    - A file system can be defined as a way to store, retrieve & update data during and after the operation of a program
    - It organizes data in an efficient manner, and is turned to the device on which the data is being stored, working in conjunction with the operating system.
    
    ## Physical
    
    ![[Untitled 7 13.png|Untitled 7 13.png]]
    
    ![[Untitled 8 13.png|Untitled 8 13.png]]
    
    ![[Untitled 9 12.png|Untitled 9 12.png]]
    
    ## Logical
    
    ![[Untitled 10 12.png|Untitled 10 12.png]]
    
    ## Disk Format
    
    - When you install a new hard disk you have to FORMAT it.
    - It’s like getting a library ready to receive books: you put up shelves and get a catalogue set up.
    - All disks are divided in 512-byte sectors. That is the standard size for the smallest disk unit. You could easily format with a different sector size, but that is not done. A sector is then the smallest disk unit and it holds 512 bytes of data.
    - Sectors are created when the circular disk is organized in concentric tracks. Each track is divided into sectors. Each sector holds 512 bytes…
    - But many files are much larger than that!!
    
    ## Clusters
    
    - This is an ‘administrative’ concept.
    
    ![[Untitled 11 10.png|Untitled 11 10.png]]
    
    - The number of sectors in a cluster depends on the size of the disk.
    
    ## File Allocation Table (FAT)
    
    - The FAT reserves some space for itself
    - The rest of the disk is left available for files
    
    ## Fundamental areas on a disk
    
    ![[Untitled 12 10.png|Untitled 12 10.png]]
    
    ## Boot Record
    
    - The first disk sector is always reserved for the boot record. It contains information about the disk or its partitions. A physical hard disk can be divided into different partitions. DOS, Windows 95 and NT treat each partition as a separate drive.
    - The boot record information enables the file system to handle the disk. At the same time, It includes a small program to use during system start-up.
    
    ## FAT Areas
    
    - After the boot record, we get to the FAT areas. There are usually two identical FATs. FAT number 2 is simply a spare copy of number 1, since FAT is essential for the function of the disk. The FAT file administration is actually a very simple system, but complicated to describe.
    - The FAT consists of a table of information about each cluster on the disk - there are 4 options
    
    ![[Untitled 13 9.png|Untitled 13 9.png]]
    
    ## Root directory
    
    This contains information about the files stored on the drive:
    
    - File name
    - Size in bytes
    - Date created/last revied
    - Location of the FIRST cluster it’s located in
    
    ## File Fragmentation
    
    ![[Untitled 14 9.png|Untitled 14 9.png]]
    
    Originally, to save space, new files were written to the first available space, so fragmentation occurred quickly. Later implementations fill the disk first, but then go back to fill the gaps so fragmentation occurs eventually.
    
    ## Defragmentation
    
    This reorganizes the disorganized files so they can be accessed more efficiently.
    
    ## Partitions
    
    ![[Untitled 15 6.png|Untitled 15 6.png]]