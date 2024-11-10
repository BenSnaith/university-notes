- Lecture Notes
    
    [Powerpoint](https://learn-eu-central-1-prod-fleet01-xythos.content.blackboardcdn.com/5d2cb9c32e9d7/16220757?X-Blackboard-S3-Bucket=learn-eu-central-1-prod-fleet01-xythos&X-Blackboard-Expiration=1700244000000&X-Blackboard-Signature=p%2Fs4pDvd7W%2FaVH8Eb9G6c0xIApLcRsYQOD8yH6n2fHs%3D&X-Blackboard-Client-Id=163100&X-Blackboard-S3-Region=eu-central-1&response-cache-control=private%2C%20max-age%3D21600&response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27CS1CS-Lec6-MIPS.pdf&response-content-type=application%2Fpdf&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEF8aDGV1LWNlbnRyYWwtMSJIMEYCIQDGSBFWvTcZQYBar4pMxmNbH5NKsGtqv7GApd8HfgsZ5AIhANEoJZGVfvUv8dptXeMRsr3nQNA0eGW7s%2FVMPRjFSun%2BKsYFCKj%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQAxoMNjM1NTY3OTI0MTgzIgz%2BVoRzVuJw3t02R1UqmgXhGAUACeUsM6Kg6%2FJz5BRZIhmaJP82sKY2Nim0ioYVHB%2FKa0cZKvt1kFAkjGfERdjl7fV%2FUg1OIRw7B4jCcFwpK0%2BmWV%2Fu684A0NPnD3B%2FEY9FD6IzD2wLbpM3J2vxQLqakPKdRyT%2Bb1DCg0%2BcQXbt2A%2Fd1vG0afUGHZTuLMIYS%2FfHsCAffYEBWACrQtkpKekzqxEIQ74PyhFAVADtlVTefrYt5yr4j%2FXroFw%2F1574AGj4MwQ95ggGXErNKNsOUHph4%2F7%2F5sI2rtLQwoa3ugWpHvjdJ%2Bp0GE6d0B8%2BlEY4Zx%2FJ1icJWb61sIwOjrbbrvX2zwEZAB3bmiC2OyY2Xrz84m39MPEENsQKHXayK34WRbZpr7DwldV%2Br6EizUtPdS0IZd0JtGpPW39fqMJPmvcTvrZyRo9QvBSey%2BaYxaLHeohv%2BqdVG2KqC79S%2Bp7560U43bMr%2F2VLZZz49ofq4WNNNfqVimPXWkNU0LkSWhng7gynETLzE%2FmpYg38NY3CLX0jKMqmo6Xkk%2FH0gsrTrT1WxEaVmExZKRhDB2wK%2B9owNJgZQb2%2BpY374SBIoAK31hwGOakzxj43sf%2BgeiVoqR7pmA4Y7Rc3CXBc%2BAFGV3z5uTmhzcpTDD%2FBFqtBqH5G%2BHERnPd0WN2eRhWyv3BIgmVGxhLJNfSEMpPJSddxPknJsVytqOveE1H9mmL%2FqvBB3P%2BEpNZGWqPHcNmT1Ring9vX4flREfgVdmeoPHBZYTK4kruh%2FxnF6htvsvHiocuOnAIubPtqbc%2FWk5wtyRI26TADU9EIrZZpu3MTUaIO3cZFmyKDML7vJgY7FMrsIesxzFAnZGFtHHzTGVBYQ8ta9Ig48JZh%2BK9Qrl5Y7wI1jWQrfRFY7XC9PbVKjZcw6%2B%2FdqgY6sAGhZ2ZqII3sCj%2BwhYKDSiYQeFKtO0jTeega83HYySFAv1beiM8J%2FV1sYLwkCA2L5eRS1aEJRS9u7jqCkvzN0gMU%2ByGN%2BqaxIbh9LDYuc5UckSIbOAZfHkYWqI97I2lNZJQwJ2%2B1nEFxQWM9PAQGlao5boN71REvyAHaN%2FNPhkWGSKiccGWCeeC3Fe9Lt9fJ5q2zeXXYQqUOQ4qMq1K9EPgRiFrlaBQeQcIIvDNMOrUKeQ%3D%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20231117T120000Z&X-Amz-SignedHeaders=host&X-Amz-Expires=21600&X-Amz-Credential=ASIAZH6WM4PLXWXJ4CE6%2F20231117%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Signature=ede875c941d92ce8a02030bbf0698dc991a048e213c96562beddc603015ab08c)
    
    ## Levels of Representation/Interpretation
    
    ![[Untitled 44.png|Untitled 44.png]]
    
    Compiler: Translates a high-level programming language to a lower-level language, e.g. Assembly, Object Code or Machine Code.
    
    - Recognise legal (and illegal) programs
    - Generate correct code
    - Manage storage of all variables and code
    - Agree on format for object (or assembly) code
    
    Assembler: translate assembly language into machine code.
    
    ## MIPS Architecture
    
    MIPS - Microprocessor without Interlocked Pipeline Stages
    
    MIPS32:
    
    - Registers:
        - 32, 32-bit general-purpose registers
        - Preceded by $ in assembly language instruction
        - Special purpose and Floating-point registers
    - Instructions:
        - Instructions are all in 32 bits i.e. fixed length
        - Three types of instruction formats: R, I, J
        - The instruction set is small: a typical RISC
    - Data types:
        - Byte (8 bits), half-word (2 bytes), word (4 bytes)
        - An integer required 1 word of storage
        - A character requires 1 byte of storage
    - [Reference Sheet](https://inst.eecs.berkeley.edu//~cs61c/resources/MIPS_Green_Sheet.pdf)
    
    ## MIPS registers
    
    |Number|Name|Purpose|
    |---|---|---|
    |0|$zero|Always 0. Writes to this registers are ignored.|
    |1|$at|Reserved by the assembler.|
    |2-3|$v0-$v1|Expression and function result variables|
    |4-7|$a0-$a3|Arguments for function calls|
    |8-15|$t0-$t7|Temporary Values|
    |16-23|$s0-$s7|These values must be saved before being accessed by the called function|
    |24-25|$t8-$t9|Temporary Values|
    |26-27|$k0-$k1|Reserved for use by the OS|
    |28|$gp|Global Pointer — points to the middle of the 64K memory block in the static data segment|
    |29|$sp|Stack pointer|
    |30|$s8|Saved value / frame pointer. Must be saved before being used|
    |31|&ra|Return address. Must be saved before being used|
    
    ## MIPS registers
    
    - Each MIPS register is 32 bits wide (4 bytes)
        - Groups of 32 bits are called a word in MIPS
    - 32 registers in MIPS
        - Registers are numbered from 0 to 31
        - Each register can be referred to by number or name
    - Number references:
        - `$0, $1, …. $30, $31`
    - Register names: e.g.
        - `$t0, $t1, …, $t9` for temporary values
        - `$s0, $s1, …, $s7` for saved variables
    
    ## Assembly Variables: Registers
    
    - Unlike C or Java, **assembly cannot use variables**
    - Registers are used as MIPS assembly operands
        - Limited number of special locations built directly into the hardware
        - Operations can only be performed on these!
        - The registers have no type: Operations determines how register controls are treated.
    - Since registers are directly in hardware, they are very fast.
    - Since registers are in hardware, there are a pre-determined number of them
    
    ## About MIPS32 Memory
    
    - Memory is byte-addressed, word size is 4 bytes.
    - Alignment restriction: MIPS requires that all words start at byte addresses that are multiples of 4 bytes
    - Word address is the left-most byte address. i.e. word addresses are 4 bytes apart and the last two bits are always 00 in binary
    - Word aligned restriction makes the hardware simpler and faster.
    
    ![[Untitled 1 24.png|Untitled 1 24.png]]
    
    ## Types of Instructions
    
    - Arithmetic and Logic instruction
        - Perform arithmetic or logical operations on data
        - e.g., `add $t0, $s1, $s2 #$t0 gets $s1 + $s2`
    - Data movement
        - Move data back and forth between CPU, memory or I/O
        - e.g., `lw $t0, 32($s3) \#load word`
    - Control instructions
        - Transfer control from one section of the program to another
        - e.g. `beq $s0,$t0,L1`
        - `\#if($s0==$t0) branch to the instruction labelled L1;`
    
    ## Instruction Formats
    
    - MIPS defines 3 basic types of instruction:
        - l-format: used for instructions with immediates (basically ints), e.g., `lw` and `sw` (since offset counts as immediate), and branches (`beq` and `bne`)
        - J-format: used for `j` and `jal`
        - R-format: used for all other instructions
    
    ![[Untitled 2 24.png|Untitled 2 24.png]]
    
    ## R-format Instructions
    
    ![[Untitled 3 22.png|Untitled 3 22.png]]
    
    - op: operation code (opcode). partially specifies what instruction it is
        - This number is 0 for all R-Format instructions
    - rs (Source Register): generally specify register containing first operand
    - rt (Target Register): generally specify register containing second operand
    - rd (Destination Register): generally used to specify register which will receive result of computation
    - shamt: shift amount (is 00000 for now)
    - funct: function code (combined with opcode to specify the instruction
    
    ## R-Format Examples
    
    Two Examples:
    
    - add $8, $9, $10
        - opcode = 0
        - funct = 32
        - rd = 8 (destination)
        - rs = 9 (first op)
        - rt = 10 (second op)
        - shamt = 0 (not a shift)
    - sub $s2, $t0, $t1
        - opcode = 0
        - funct = 34
        - rd = 18
        - rs = 8
        - rt = 9
        - shamt = 0
    - MIPS instruction: `add $8,$9,$10`
    
    Decimal number per field representation:
    
    |   |   |   |   |   |   |
    |---|---|---|---|---|---|
    |0|9|10|8|0|32|
    
    Binary number per field representation:
    
    |   |   |   |   |   |   |
    |---|---|---|---|---|---|
    |000000|01001|01010|01000|00000|100000|
    
    hex representation: 012A 4020$_1$﻿$_6$﻿
    
    decimal representation: 19,546,114
    
    `add $t0, $s1, $s2`
    
    Field mapping:
    
    |   |   |   |   |   |   |
    |---|---|---|---|---|---|
    |Add op|$s1|$s2|$t0|0|Add funct|
    
    Decimal Representation:
    
    |   |   |   |   |   |   |
    |---|---|---|---|---|---|
    |0|17|18|8|0|32|
    
    Binary Representation:
    
    |   |   |   |   |   |   |
    |---|---|---|---|---|---|
    |000000|10001|10010|01000|00000|100000|
    
    Hex Representation:
    
    02324020
    
    ## I-format Instruction
    
    ![[Untitled 4 20.png|Untitled 4 20.png]]
    
    - op: opcode uniquely specifies an instruction in I-format, note that there’s no funct field
    - rs: specified a register operand
    - rt: specifes register which will receive result of computation or other operand for some instructions
    - immediate:
        - for addi, the 16-bit immediate sign-extended to 32 bits. Thus it’s treated as a signed integer
        - 16 bits can be used to represent immediate up to 2$^1$﻿$^6$﻿ different values
        - This is large enough to handle the offset in a typical lw or sw
    
    ## I-format Example
    
    MIPS Instruction: addi $21, $22, -50
    
    - opcode = 8
    - rs = 22
    - rt = 21
    - immediate = -50
    
    Decimal field representation
    
    |   |   |   |   |
    |---|---|---|---|
    |8|22|21|-50|
    
    Binary field representation
    
    |   |   |   |   |
    |---|---|---|---|
    |001000|10110|10101|1111111111001110|
    
    Hex: 22D5FFCE
    
      
    
    MIPS Instruction: `lw $s2,8($s1)`
    
    Decimal Field representation
    
    |   |   |   |   |
    |---|---|---|---|
    |35|17|18|8|
    
    Binary Field representation
    
    |   |   |   |   |
    |---|---|---|---|
    |100011|10001|10010|0000000000001000|
    
    Hex: 82320008
    
    ## J-format Instructions
    
    ![[Untitled 5 20.png|Untitled 5 20.png]]
    
    - Used by jump instructions
        - 6 bits for the operation field
        - 26 bits for the address field
        - e.g. j 10000
    - For general jumps (j and jal) we may jump to anywhere in memory
        - j label and jal label
    
- Tutorial
    
    Q1. What is the binary code of the following MIPS R-format instruction?
    
    sub $t2, $t0, $t1
    
    **A1. 0000|00 01|000 0|1001| 0101|0 000|00 10|0010**
    
    **0x01095022**
    
    Q2. What is the binary code for the following MIPS R-format Instruction
    
    beq $s1, $s0, 4
    
    **A2. 0001|00 10|001 1|0000| 0000|0 000|00 00|0100**
    
    **0x12300004**
    
    Q3. The following binary number represents one MIPS instruction, translate it.
    
    1010 1110 0000 1011 0000 0000 0000 0100
    
    0xAD0B0004
    
    1010 11|10 000|0 1011| 0000 0000 0000 0100
    
    A3.
    
    sw $t3, 4x0($t0)
    
- Further Reading