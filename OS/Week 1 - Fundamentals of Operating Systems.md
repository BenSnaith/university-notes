### Let's Start

Can you describe "Operation System" in one sentence?

### What it Operating Systems

A layer of software needs to manage components, this is the **Operating System (OS)**.

### Operating System Concepts

 - A program which controls the execution of application programs.
 - Interacts as an interface between application programs and computer hardware.
 - Primary objectives of an OS:
	 - Manage hardware resources
	 - User Interface
	 - Stable and Secure environment

### Computer System Structure

Computer systems can be divided into four components:

 - Hardware
	 - Provides basic computing resources CPU, memory, I/O devices.
 - Operating System
	 - Controls and coordinates use of hardware among various applications and users.
 - Application Programs
	 - Define the ways in which the system resources are used to solve the computing problems of the users
	 - Word processors, compilers, web browsers, database systems, video games.
 - Users
	 - People, machines, other computers.

### Where does OS fit in the Computer System?

![[Pasted image 20260119122738.png]]

### Functions of an Operating System

 - Manage Resources
 - Manage Processes
 - Manage Memory
 - Manage File System
 - Manage Devices
 - Provides User Interface
 - Provides Security and Protection
 - Networking

### Operating System Mode

![[Pasted image 20260119122840.png]]

The **User Mode** is concerned with the action interface between the user and the system, it controls things like running applications and accessing files.

The **Kernel Mode** is concerned with everything running in the background, it controls things like accessing system resources, controlling hardware functions and processing program instructions. **System Calls** are used to change mode from User to Kernel.

### Kernel

A software code that controls complete system, when the operating system boots, kernel is the first part of OS to load into main memory, it executes processes and handle interruptions in kernel space.

The user performs its task in the user area of memory. This memory separation is made to prevent the user data and kernel data from interfering with each other. Kernel does not interact directly with user, but it interacts using SHELL and other programs and hardware.

Kernel Includes;

 1. **Scheduler**; it allocates the Kernel's processing time to various processes.
 2. **Supervisor**; it grants permissions to use computer system resources to each process.
 3. **Interrupt Handler**; it handles all requests from the various hardware devices which compete for kernel services.
 4. **Memory Manager**; allocates space in memory for all users of kernel service.

The Kernel provides services for process management, file management, I/O management, memory management.
System calls are used to provide these types of resources.

### System Call

A System Call is a programmatic way in which a computer program / user application requests a service from the kernel of the operating system on which it is executed.

Application program is just a user-process. Due to security reasons, user applications are not given access to privileged resources (the ones controlled by OS).

When they need to do any I/O or have some more memory or spawn a process or wait for signal / interrupt, it requests operating system to facilitate all these. This request is made through a System Call.

System calls are also called software-interrupts.

### Common Functions of Interrupts

Interrupt transfers control to the interrupt service routine generally, through the interrupt vector, which contains the addresses of all the service routines. Interrupt architecture must save the address of the interrupted instruction and incoming interrupts are disabled while another interrupt is being processed to prevent a lost interrupt. A trap of execution is a software generated interrupt caused either by an error or a user request. An operating system is interrupt driven.

### System Calls

 - Programming interface to the services provided by the OS.
 - Typically written in a high-level language (C or C++).
 - Mostly accessed by programs via a high-level application programming interface (API) rather than direct system call use.
 - Three most common APIs are:
	 - Win32 API for Windows
	 - POSIX API for POSIX-based systems (including virtuall all versions of UNIX, Linux, and Mac OS X)
	 - Java API for the Java Virtual Machine (JVM)

### Example of how system calls are used

![[Pasted image 20260119125005.png]]

## Example of Standard API

![[Pasted image 20260119125030.png]]

### API System Calls - OS Relationship

![[Pasted image 20260119125100.png]]

### Types of System Calls

![[Pasted image 20260119125122.png]]

### Standard C Library Example

![[Pasted image 20260119125144.png]]

### Operating System Goals

 - Efficiency
 - Robustness
 - Scalability
 - Extensibility
 - Portability
 - Security
 - Protection
 - Interactivity
 - Usability

### Operating System Environments

Operating systems intended for high-end environments;
 - Special design requirements and hardware support needs:
	 - Large main memory.
	 - Special-purpose hardware.
	 - Large numbers of processes.
Embedded Systems
 - Characterised by small set of specialised resources.
 - Provide functionality to devices such as cell phones and PDAs.
 - Efficient resource management key to building successful operating system.
Real-time Systems
 - Require that tasks be performed within particular (often short) time frame
	 - Autopilot feature of an aircraft must constantly adjust speed, altitude and direction.
 - Such actions cannot wait indefinitely -- and sometimes cannot wait at all.

### Virtual Machine Environments

Virtual Machines (VMs)
 - Software abstraction of a computer.
 - Often executes on top of native operating system.
Virtual Machine Operating System
 - Manages resources provided by virtual machine.
Applications of virtual machines
 - Allows multiple instances of an operating system to execute concurrently emulation.
	 - Software or hardware mimics functionality of hardware or software not present in system.
 - Promote portability.

### Virtual Machine Schematic

![[Pasted image 20260119130527.png]]

### Operating System Architectures

Today's operating systems tend to be complex.
 - Provide many services.
 - Support a variety of hardware and software.
 - Operating system architectures help manage this complexity:
	 - Organise operating system components.
	 - Specify privilege with which each component executes.

### Monolithic Architecture

Monolithic Operating System
 - Every component contained in Kernel.
	 - Any component can directly communicate with any other.
 - Tend to be highly efficient.
 - Disadvantage is difficulty determining source of subtle errors.

![[Pasted image 20260119132112.png]]

### Layered Architecture

Layered approach to operating systems
 - Tries to improve on monolithic kernel designs.
	 - Groups components that perform similar functions into layers.
 - Each later communicates only with layers immediately above and below it.
 - Processes requests might pass through many layers before completion.
 - System throughput can be less than monolithic kernels.
	 - Additional methods must be invoked to pass data and control.

![[Pasted image 20260119132123.png]]

### Microkernel Architecture

Microkernel Operating System architecture
 - Provides only small number of services.
	 - Attempt to keep kernel small and scalability.
 - High degree of modularity.
	 - Extensible, portable and scalability.
 - Increased level of intermodular communication
	 - Can degrade system performance.

![[Pasted image 20260119132131.png]]

### Networked and Distributed Operating Systems

Network Operating System
 - Runs on one computer.
 - Allows its processes to access resources on remote computers.
Distributed Operating System
 - Single operating system.
 - Manages resources on more than one computer system.
 - Goal Include:
	 - Transparent Performance
	 - Scalability
	 - Fault Tolerance
	 - Consistency

### Hybrid Systems

 - Most modern operating systems are actually not one pure model
	 - Hybrid combined multiple approaches to address performance.
	 - Linux and Solaris kernels in kernel address space, so monolithic, plus module for dynamic loading of functionality
	 - Windows mostly monolithic, plus microkernel for different subsystem personalities
 - Apple Mac OS X hybrid, layered, Aqua UI plus Cocoa programming environment.
	 - Below is kernel consisting of Mach microkernel and BSD Unix parts, plus I/O kit and dynamically loadable modules (called kernel extensions).

### MacOS and iOS Structure

![[Pasted image 20260119133303.png]]