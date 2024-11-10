The motherboard is the main Printed Circuit Board (PCB) in a general purpose computer. It holds and allows communication between many of the crucial electronical components in a computer, such as the CPU, the Memory, the Peripherals.

A Motherboard is specifically a PCB with expansion capabilities, as the name suggests it is the mother of all the attached components, including daughterboards; sound cards, video cards, network cards etc.

A mainboard is a PCD with no capability to expansion, such as in TVs or printers and other embedded systems.

# Design

A motherboard provides an electrical connection by which other components can communicate, it also contains the CPU and host other subsystem devices.

A typical desktop computer has it microprocessor, main memory and other essential components connected to the motherboard. Other components such as external storage, controllers for video display and sound, and peripheral devices may be attached to the motherboard as plug-in cards or via cables; in modern microcomputers it is increasingly common to integrate some of these peripherals into the motherboard itself.

An important component of a motherboard is the microprocessor’s supporting chipset (set of electrical components), which provides the supporting interfaces between the CPU and the various buses and external components. This chipset determines, to an extent, the features and capabilities of the motherboard

Modern motherboards include:

- CPU sockets in which one or more microprocessors may be installed.(sometimes the CPU is soldered.)
- Memory slots into which the system’s main memory is to be installed, typically in the form of DIMM (Dual In-line Memory Module) commonly called a RAM stick containing DRAM chips.(Dynamic Random-Access Memory.)
- The chipset which forms an interface between the CPU, main memory and peripheral buses.
- Non-volatile memory chips containing the system’s firmware or bios
- The clock generator which produces the system clock signal to synchronize various components
- Slots for expansion cards
- Power connectors, which receive electrical power from the power supply and distribute it across the components, some graphics cards require more power than the motherboard can supply and thus dedicated connectors have been introduced to attach them directly to the power supply.
- Connectors for hard disk, optical disk drives, or solid-state drives, typically SATA (common bus interface) and NVMe now.

In addition nearly all motherboards include logic and connectors to support commonly used input devices, such as USB for mouse devices and keyboards. Early personal computers such as the Apple II or IBM PC included only this minimal peripheral support on the motherboard.

Most modern motherboards nearly always include heat sinks and mounting points for fans to dissipate excess heat.

# Form factors

- ATX — the standard form factor for most desktop computers, must buy an ATX case to correctly fit the motherboard and mount correctly.
- microATX — Smaller than the regular ATX, requires a specific case and is also commonly used in laptops due to the smaller form factor.

![[Untitled 3.png|Untitled 3.png]]

# CPU sockets

A CPU socket or slot is an electrical component that attaches to a PCB board and is designed to house a CPU (microprocessor). It is a special type of integrated circuit socket designed for very high pin counts. A CPU socket provides many functions, including a physical structure to support the CPU, Heat sink and facilitate replacement, and most importantly, forming an electrical interface between the CPU and PCB.

# Integrated peripherals

With the steadily declining costs and size of integrated circuits, it is now possible to include support for many peripherals on the motherboard. By combining many functions on one PCB, the physical size and total cost of the system may be reduced; highly integrated motherboards are thus especially popular in small form factor and budget computers.

- Disk controllers for SATA drives, and historical PATA drives
- Historical floppy-disk controller
- Integrated graphics controller supporting 2D and 3D graphics, with VGA, DVI, HDMI, DisplayPort, and TV output
- Integrated sound card
- Ethernet network controller
- USB controller
- Wireless network interface controller
- Bluetooth controller
- Temperature, voltage and fan-speed sensors

# Peripheral card slots

A typical motherboard will have a different number of connections depending on its standard and form factor.

A standard, modern ATX motherboards will typically have two or three PCI-Express x16 connectors for a GPU, one or two legacy PCI slots for various expansion cards, and one or two PCI-E x1. A standard EATX motherboard will have two or four PCI-E x16 connections for GPUs, and a varying number of PCI and PCI-E x1 slots. It can sometimes have a PCI-E x4 slot.

Newer motherboards have M.2 slots for SSDs or Wireless network interface controllers.

# Temperature and reliability

Motherboards are generally air cooled with heat sinks often mounted on larger chips in modern motherboards. Improper cooling can cause damage to the internal components. before the 1990’s, passive cooling mounted to the power supply was sufficient, however now most require CPU fans mounted to heat sinks due to rising clock speed and power consumption, most have connectors for additional fans mounted to the case, and integrated sensors to regulate the internal temperatures.

# Spurious crashes

A 2003 study found that most random PC crashes are caused by aging capacitors on motherboards. termed capacitor plague.

# Capacitors

Most modern motherboards electrolytic capacitors to filter the DC power distributed across the board. These capacitors age at a temperature dependent rate, as their water based electrolytes slowly evaporate. This can lead to a loss of capacitance and subsequent motherboard malfunctions due to voltage instabilities.

Mid-High range motherboards use solely solid capacitors exclusively. For every 10c less, their average lifespan is multiplied approx by three, resulting in a 6x higher life span that electrolytic capacitors.

# Bootstrapping

Motherboards contain a ROM that stores to initialize hardware devices and boot and operating system from a peripheral device.

At power-up the CPU would load its program counter with the address of the Boot ROM on the Motherboard and start executing the instructions. These instructions initialize and test the hardware Power-on Self Test (PoST), display system info on the screen, perform ram checks and then attempt to boot an operating system from a peripheral drive, if no peripheral drive containing an OS is available then the computer would perform tasks on other ROM stores and display an error.

When the computer is powered on, the boot firmware tests and configures memory, circuitry, and peripherals.

  

- **PCI (2)**

Slots for older expansions cards such as sound cards, network cards, connector cards.

Largely been replaced by PCI-Express x1 (number specified lanes)

- **PCI Express x1 (3)**

Slot for modern expansion cards such as sound cards, network cards, connector cards and certain low-end graphics cards.

- **PCI Express x16 (4)**

Slot for discrete graphics cards and high bandwidth devices such as top-end solid state drives.

- **Northbridge (5)**

Also known Memory Controller Hub

Chipset that allows the CPU to communicate with the RAM and GPU

Beginning from Intel Sandy Bridge in 2011, this motherboard component is no longer present as it has been integrated within the CPU itself.

- **CPU Socket (6)**

Insert CPU here.

- **ATX 12v Power Connector (7)**

Connects to the 4-pin power cable of a PSU which provides power to the CPU

![[Untitled 1 2.png|Untitled 1 2.png]]

- **Front Panel USB 2.0 Connectors (8)**

Connects to USB2.0 ports at the front or top of the computer.

- **Front Panel Connectors (9)**

Connects to the power switch, reset switch, power LED, hard drive LED and front audio ports of a case.

- **IDE Connector (10)**

Connects to older hard drive disks and optical drives for data transfer.

Largely been replaced with SATA

- **CMOS Battery (11)**

Supplies power to store the BIOS settings and keep the real-time clock running.

Usually looks like a watch battery.

- **Southbridge (12)**

Also knows and the Input/Output Controller Hub.

Chipset that allows the CPU to communicate with the PCI, PCI-E x1, SATA connectors, USB ports, Ethernet ports and on board audio.

- **SATA Connectors (13)**

Connects to modern hard disk drives, solid state drives and optical drives for data transfer.

- **Fan Headers (14)**

Supplies power to the CPU heat sink fan and computer case fans.

- **RAM Slots (15)**

Insert RAM.

- **ATX Power Connector (16)**

Connects to the 24-pin ATX power cable of a PSU which supplies power the the motherboard

- **mSATA Connector (17)**

Connects to a mSATA SSD, in most cases, this SSD is used as cache to speed up HDDs, but its possible to repurpose as a regular HDD.

- **Front Panel USBC 3.0 Connector (18)**

Connects to USB 3.0 ports at the front or top of the case.

- **Power and Reset Button (19)**

![[Untitled 2 2.png|Untitled 2 2.png]]