… via [wikipedia.org/wiki/Central_processing_unit](http://wikipedia.org/wiki/Central_processing_unit)

# Central processing unit.

A central processing unit — also called a central processor or main processor — is the most important processor in a given computer. Its electronic circuitry executes instructions of a computer program, such as arithmetic, logic, controlling, and I/O operations. This role contrasts with that of external components such as main memory and I/O circuitry, and specialized coprocessors such as graphics processing units (GPUs).

The form, design, and implementation of CPUs have changed over time, but their fundamental operation remains almost unchanged. Principal components of a CPU include the ALU that performs Arithmetic and Logic operations, Processor registers that supply operands (==the numbers / things being operated on==) to the ALU and stores the results of ALU operations, and a control unit that orchestrates the fetching (from memory) decoding and execution by directing the coordinated operations of the ALU, registers and other components.

Most modern CPUs are implemented on integrated circuit (IC) microprocessors, with one or more CPUs on a single IC chip. Microprocessor chips with multiple CPUs and multi-core processors. The individual physical CPUs, processor cores, can also be multithreaded to create additional virtual or logical CPUs.

An IC that contains a CPU may also contain memory, peripheral interfaces, and other components of a computer; such integrated devices are variously called microcontrollers or systems on a chip (SoC).

# CPU Operation

The fundamental operation of most CPUs, regardless of the physical form they take, is to execute a sequence of stored instructions that is called a program. The instructions to be executes are kept in some kind of computer memory. Nearly all CPUs follow the fetch, decode and execute steps in their operation, which are collectively known as the instruction cycle.

After the execution of an instruction, the entire process repeats, with the next instruction cycle normally fetching the next-in-sequence instructions because of the incremented value in the program counter. If a jump instruction was executed, the program counter will be modified to contain the address of the instruction that was jumped to and program execution continues normally. In more complex CPUs, multiple instructions can be fetched, decoded and executed simultaneously. This section describes what is generally referred to as the classic RISC pipeline, which is quite common among the simple CPUs used in many electronic devices. It largely ignores the important role of CPU cache, and therefore the access stage of the pipeline.

Some instructions manipulate the program counter rather than producing results data directly; such instructions are generally called “jumps” and facilitate program behavior like loops, conditional program execution, and existence of functions. In some processors, some other instructions change the state of bits in a “flags” register. These flags can be used to influence how a program behaves, since they often indicate the outcome of various operations. For example, in such processors a “compare” instruction evaluates two values and sets or bits in the flags register to indicate which one is greater or whether they are equal; one of these flags could be used by a later jump instruction to determine program flow.

## Fetch

Fetch involves retrieving an instruction (which is represented by a number or sequence of numbers) from program memory. The instruction’s location (address) in program memory is determined by the program counter, which stores a number that identified the address of the next instruction to be fetched. After an instruction is fetched, the PC is incremented by the length of the instruction so that it will contain the address of the next instruction in the sequence. Often, the instruction to be fetched must be retrieved from relatively slow memory, causing the CPU to stall while waiting for the instruction to be returned. This issue is largely addressed in modern processors by caches and pipeline architectures.

## Decode

The instruction that the CPU fetched from memory determines what the CPU will do. In the decode step, performed by binary decoder circuitry known as the instruction decoder, the instruction is converted into signals that control other parts of the CPU.

The way in which the instruction is interpreted is defined by the CPU’s instruction set architecture (ISA). Often, one group of bits (that is, a field) within the instruction, called the opcode, indicates which operation is to be performed, while the remaining fields usually provide supplemental information required for the operation, such as the operands. Those operands may be specified as a constant value, or as the location of a value that may be processor value registry or a memory address, as determined by some addressing mode.

## Execute

After the fetch and decode steps, the execute step is performed. Depending on the CPU architecture, this may consist of a single action or a sequence of actions. During each action, control signals electrically enable or disable various parts of the CPU so they can perform all or part of the desired operation. The action is then completed, typically in response to a clock pulse. Very often the results are written to an internal CPU register for quick access by subsequent instructions, In other cases results may be written slower, but less expensive and higher capacity memory.