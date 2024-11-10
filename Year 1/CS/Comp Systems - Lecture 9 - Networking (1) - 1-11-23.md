- Lectures Notes
    
    ## Packet Switching
    
    - Messages that are being transported around networks are divided up into packets rather than sending the entire item all at once.
    
    ## Efficient Message Transmission
    
    - Challenge: a simple approach, like store-and-forward, large messages block small ones
    - Break each message into packets
    - Can allow the packets from a single message to travel over different paths dynamically adjusting for use
    - Use special-purpose computers, called routers, for traffic control.
    
    ## Uses of networks
    
    ![[Untitled 37.png|Untitled 37.png]]
    
    ## The role of networks
    
    Fundamentally, the role of a network is to accept data from the sender host and transmit it to the receiving host.
    
    ## Why have a network?
    
    - Every large organisation will have computers which their employees use to track inventory, contact suppliers and do a lot of other functions that are vital to business operations, Networks are used so that certain pieces of data can be accessed by all or certain people within the company.
    - Can share resources such as printers.
    
    ## Network security
    
    - Internal
    - External
    
    ## Types of network
    
    ![[Untitled 1 17.png|Untitled 1 17.png]]
    
    ## Clusters
    
    - A cluster network is two or more computing devices working together for a common computing purpose e.g.
        - Load-balancing cluster
        - High-availability cluster
        - High-performance cluster
    
    ## Virtualized networks
    
    - Virtualization is the basic act of decoupling an infrastructure service from the physical assets on which that service operates
    
    ![[Untitled 2 17.png|Untitled 2 17.png]]
    
    ## The layered model
    
    What is a layered model?
    
    - Models help us to visualize different aspects of complex abstract systems
    - Almost all communication can be broken down into independent layers that work interdependently
    - The ‘layers’ (and protocols between them) conceptually represent negotiations between aspects of communication: Content logical (encoding) and physical delivery of messages
    
    ![[Untitled 3 15.png|Untitled 3 15.png]]
    
    ## 2 Models for Network Communications
    
    - OSI 7-Layer Model
        - International Standards Organization’s Open Systems Interconnection Model.
    - TCP/IP Model
        - Developed by the Department of Defense
    
    ![[Untitled 4 14.png|Untitled 4 14.png]]
    
    ## The OSI Layered Model
    
    - OSI — Open System Interconnection
    - Layered Approach
    - Allows better interoperability between software and hardware
    - Allows design of elaborate but highly reliable protocol stacks
    
    ## The Physical Layer
    
    - Defines all electrical and physical specifications for devices
    - Major Functions
    - Example — Radio, SCSI (Small Computer System Interface), hubs, repeaters.
    
    ![[Untitled 5 14.png|Untitled 5 14.png]]
    
    ## The Data Link Layer
    
    - Controls data transfer between network entities
    - Performs error detection & correction
    - Uses physical / flat addressing scheme
    - Example - Ethernet, Bridges & Switches
    
    ![[Untitled 6 11.png|Untitled 6 11.png]]
    
    ## The Network Layer
    
    - Performs network routing, flow control, segmentation, and error control functions
    - The router operates at this layer
    - Uses local addressing scheme
    - Example — IP, Token Ring
    
    ![[Untitled 7 10.png|Untitled 7 10.png]]
    
    ## The Transport Layer
    
    - Provide transparent transfer of data between end users
    - Controls reliability of a given link
    - Some protocols are stateful and connection oriented (cookies)
    - Tracks packets & retransmits those that fail
    - Example — TCP / UDP
    
    ![[Untitled 8 10.png|Untitled 8 10.png]]
    
    ## The Session Layer
    
    - Provides mechanism for managing the dialogue between end-user application processes
    - Provides for either duplex or half-duplex operation
    - Responsible for setting up and tearing down TCP/IP sessions
    - Example - NetBIOS
    
    ![[Untitled 9 9.png|Untitled 9 9.png]]
    
    ## The Presentation Layer
    
    - Controls syntactical differences in data representation within end-user systems
    - MIME encoding is done at this layer
    - Example — XML
    
    ![[Untitled 10 9.png|Untitled 10 9.png]]
    
    ## The Application Layer
    
    - Provide semantic conversion between associated application processes
    - Interfaces directly to and performs common application services for the application processes
    - Example — Telnet, Virtual Terminal
    
    ![[Untitled 11 7.png|Untitled 11 7.png]]
    
    ## TCP/IP Layered Model
    
    - Transmission Control Protocol and Internet Protocol
    - TCP/IP is suite of protocols, also known as the Internet Protocol Suite
    - It was originally developed for the US Department of Defense, Advanced Research Project Agency (DARPA) network, but it was now the basis for the Internet
    
    ![[Untitled 12 7.png|Untitled 12 7.png]]
    
    ## TCP/IP Model Layers
    
    ![[Untitled 13 6.png|Untitled 13 6.png]]
    
    ## What does each layer do?
    
    - As with the OSI model, the TCP/IP suite uses a layered model
    - TCP/IP model has four or five - depending on who you talk to and which books you read
    - Some people call it a four-layer suite - Application, Transport, Internet and Network Access others split the Network Access layered into its physical and Datalink components.
    
    ## Network Access Layer
    
    - The combination of datalink and physical layers deals with pure hardware (wires, satellite links, network interface cards etc.)
    - Access methods such as CSMA/CD (carrier sensed multiple access with collision detection)
    - Ethernet exists at the network access layer - its hardware operates at the physical layer and its medium access control method (CSMA/CD) operates at the datalink layer.
    
    ![[Untitled 14 6.png|Untitled 14 6.png]]
    
    ## Internet Layer
    
    - This layer is responsible for the routing and delivery of data across networks
    - It allows communication across networks of the same and different types and carries out translations to deal with dismissal data addressing schemes. IP (Internet Protocol) and ARP (Address Resolution Protocol) are both to be found at the Internet layer.
    
    ![[Untitled 15 4.png|Untitled 15 4.png]]
    
    ## Transport Layer
    
    - The transport layer is similar to the OSI transport model, but with elements of the OSI session layer functionality
    - The two protocols found at the transport layer are:
        - TCP (Transmission Control Protocol): reliable, connection-oriented protocol that provides error checking and flow control through a virtual link that it establishes and finally terminates. Examples included FTP and Email
        - UDP (User Data Protocol): unreliable, connectionless protocol that not error check or offer any flow control. Example include SNMP
    
    ![[Untitled 16 4.png|Untitled 16 4.png]]
    
    ## Application Layer
    
    - This layer is broadly equivalent to the application, presentation and session layers of the OSI model
    - It gives an application access to the communication environment.
    - Example — Telnet, HTTP (Hyper Text Transfer Protocol), SMTP (Simple Mail Transfer Protocol)
    
    ![[Untitled 17 4.png|Untitled 17 4.png]]
    
    ## Network Topology
    
    ![[Untitled 18 4.png|Untitled 18 4.png]]
    
    ## Network Infrastructure
    
    - A network infrastructure is an interconnected group of computer systems linked by the various parts of a telecommunications architecture
    - Specifically, this infrastructure refers to the organization of its various parts and their configuration — from individual networked computers to routers, cables, wireless access points, switches, backbones, network protocols, and network access methodologies
    
    ## Simple Network Infrastructure
    
    - The simplest form of network infrastructure typically consists of one or more computers, a network or Internet connection, and a hub to both link the computers to the network connection and tie the various systems to each other. The hub merely links the computers but does not limit data flow to or from any one system
    
    ## Switches and Routers
    
    - To control or limit access between systems and regulate information flow, a switch replaces the hub to create network protocols that define how the systems communicate with each other
    - To allow the network created by these systems to communicate to others, via the network connection, requires a router, which bridges the networks and basically provides a common language for data exchange, according to the rules of each network.
    
    ## Tying this all together
    
    - Most networks are designed as a stack of layers, each one built upon the one below it. Why?
    
    ![[Untitled 19 4.png|Untitled 19 4.png]]
    
    - Each layer provides services to the higher levels
    - Each layer behaves as a black box
    - Layer _n_ on one machine talks to layer _n_ on another machine
    - The corresponding layer in the layered structure are called peers.
    
    ## Tying this all together
    
    - The communication between peers must follow certain rules, known as protocols
    - No data are directly transferred between layers, Actual communication is through a physical medium below layer 1.
    
    ## OSI 7-Layer Model
    
    ![[Untitled 20 4.png|Untitled 20 4.png]]
    
    ## Reasons for layering
    
    - Simplifies the network model
    - Enables programmers to specialize in a particular level or layer of the networking model
    - Provides design modularity
    - Encourages interoperability
    - Allows for standardized interfaces to be produced by networking vendors
    
    ## 7: Application Layer
    
    - The layer where users communicate to the computer
    - Contains protocols and utilities that provides services to network applications
    - E-mail:
        - Message formats such as RFC 822
        - SMTP, POP3 (Post Office Protocol 3), IMAP (Internet Message Access Protocol)
    - WWW:
        - HTML (HyperText Markup Language), XML (eXtensible Markup Language), XSL (eXtensible Style Language)
        - HTTP (The HyperText Transfer Protocol)
    
    ## 6: Presentation Layer
    
    - The presentation layer prepares the data from the application layer for transmission over the network or from the network to the application layer
    - Include protocols specifying how to represent data (MPEG, JPEG, PIC, WAV)
    - Responsible for data translation, formatting, encryption, compression
    - We need these services because different computers use different internal representation for data (Integers and Characters)
    
    ## 5: Session layer
    
    - Enables two applications of the layer to have an ongoing conversation
    - Provide following services
        - Communication setup and teardown
        - Control for data exchange
        - Data synchronization definition
        - Failure recovery
    - Examples:
        - Structured Query Language (SQL)
        - X Windows
        - AppleTalk Session Protocol (ASP)
    
    ## 4: Transport Layer
    
    - Provides
        - end-to-end error free data transport services
        - establishes a logical connection
        - data segmentation into maximum transmission unit size
        - messaging service for session layer
    - Protocols in this layer can be
        - connection-oriented : require an acknowledgement of the receipt of data packets
        - connectionless : do not require an acknowledgement of the receipt of data packets
    
    ## Connection Oriented Protocols
    
    ![[Untitled 21 3.png|Untitled 21 3.png]]
    
    ## Flow Control
    
    - The segments delivered back to the sender upon their reception
    - Any segment not acknowledged are retransmitted
    - Segments are sequence back into their proper order upon arrival at their destination
    - Manageable data flow is maintained in order to avoid congestion
    
    ![[Untitled 22 3.png|Untitled 22 3.png]]
    
    ## Windowing
    
    - The quantity of data segment (in bytes) is sent without receiving an acknowledgment (ack) is called a window
    
    ![[Untitled 23 3.png|Untitled 23 3.png]]
    
    ## Acknowledgement (ack)
    
    ![[Untitled 24 3.png|Untitled 24 3.png]]
    
    ## 3: Network Layer
    
    - Provides services
        - to manage devices addressing
        - to track the location of devices on the network
        - to determine the best way to move data to the network
    - The network layer must transport traffic between devices that are not directly connected.
    - Routers are specified at this layer.
    
    ## 2: Data Link Layer
    
    - Services
        - Identification of the source and destination nodes via their physical address (Media Access Control (MAC) address)
        - Definition of how data is packaged for transport as frames
        - Error detection
        - Flow control of information sent across the link
    - Has two sublayers:
        - Media Access Control (MAC) 802.3
        - Logical Link Control (LLC) 802.2
    
    ## 1: Physical Layer
    
    - This layer communication directly with the various types of actual communication media
    - Services
        - definition of the physical characteristics of the network hardware, including cable and connector
        - Encoding
        - Transmission of signals on the wire
    
    ## Network devices: repeaters
    
    - The number of nodes on a network and the length of cable used influence the quality of communication on the network
    - Attenuation
    - Repeaters work against attenuation by repeating signals that they receive on a network
    - Why are repeaters Layer 1 devices.
    
    ![[Untitled 25 3.png|Untitled 25 3.png]]
    
    ## Network devices: hubs
    
    - Generic connection device used to tie several networking cables together to create a link between different stations on a network.
    
    ![[Untitled 26 3.png|Untitled 26 3.png]]
    
    ## More on hubs
    
    - Hubs that are plugged into electric power are called active hubs
    - A hub that merely connects different cables on a network and provides no signal regeneration is called a passive hub and is not a repeater.
    - “Hub” is a generic term applied to many different network-connection devices
    - If a hub in some way segments or subdivides the traffic on a network, it is an intelligent, or switching hub.
    
    ## Network Segmentation
    
    - Segmentation - Process of breaking a network into smaller broadcast or collision domains
    - Ethernet network, which are characterized by IEEE 802.3 standard, define the use of a Carrier Sense Multiple Access with Collision Detection (CSMA/CD) access method
        - Backoff algorithm : Mathematical calculation performed by computers after a collision occurs on a CSMA/CD network
        - Backoff period : Random time interval used after a collision has been detected on an Ethernet network
    
    ## Layer 2 Devices: Bridges
    
    - Operate at the Data Link layer of the OSI model
    - Filters traffic between network segments by examining the destination MAC address
        - Based on this destination MAC address, the bridge either forwards or discards the frame
        - When a client sends a broadcast frame to the entire network, the bridge will always forward the frame
    
    ## Network Segmentation via Bridges
    
    ![[Untitled 27 2.png|Untitled 27 2.png]]
    
    ## More on bridges
    
    - Transparent Bridges: Also called learning bridges because they build a table of mac addresses as they receive frames
        - This means that they “learn” which addresses are on which segments
        - Ethernet networks mainly use transparent bridges
    - Source-routing bridges: Rely on the source of the frame transmission to provide the routing information
        - Usually employed by Token Ring networks
    - Translation Bridges: Can connect networks with different architectures
    
    ## Layer 2 Devices: Switches
    
    - Increase network performance by reducing the number of packets transmitted to the rest of the network
    - Like bridges, operate at the Data Link layer of the OSI model
    - In an Ethernet network, computers are usually connected directly to a switch
    - Virtual circuit
        - Private connections between two points created by a switch that allows the two points to use the entire availabe bandwidth between those two points without contention