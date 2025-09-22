Working memory.

  

Abstact

  

SSDs have a speed of around 50 microseconds, whereas DRAM has a speed of 17 nanoseconds.

That is a tortoise compared to a fighter jet. Literally.

However DRAM is limited to a 2D array and can normally only store 1-bit per memory cell.

A stick of DRAM will have a few gigabytes of storage whereas an SSD will have terabytes in many cases.

I addition, DRAM requires a lot of power to constantly store and refresh the data held in the capacitors, therefore computers use SSDs and DRAM, by copying from the SSD to the DRAM and then pre-fetching the data from the DRAM.

==// What is a Die, a chip, a microchip. look that up, cache memory==

  

A stick of DRAM is also known as a DIMM (Dual inline memory module), with DRAM chips located on it, on most motherboards there are 4 DRAM slots and when plugged in the DRAM is directly connected to the CPU through 2 memory channels directly connected to the motherboard. The left two slots share a memory channel and so do the right two, this is why we alternate the DRAM in order to keep the channels as free as possible.

  

Inside of the CPU

  

Inside of the CPU we find the DRAM interface which manages and communicates with the DRAM, as well as an M.2 and SATA interface, by managing all these types of storage the CPU can manage the flow of data from the SSD to the DRAM to the CPU Cache to be processed by the cores

  

Back to the memory channels

  

For DDR5 the memory channel is divided up into two parts, the top part being channel A and the bottom part being channel B and independently transfer 32-bits at a time using 32 data wires. Using 21 additional wires, each memory channel carries an address specifying where to read or write data and using 7 control signal wires, commands are relayed. Addresses and commands are sent to and stored by all 4 chips on the memory channel, which work simultaneously in parallel, each chip only reads or writes 8-bits at a time. Additionally power for the DRAM is supplied by the motherboard and managed by the Power Management Chips on the stick itself

  

Inside the DRAM microchip

  

A 2GB DRAM Die is split up into 8 bank groups, each group with 4 banks each totalling 32 banks