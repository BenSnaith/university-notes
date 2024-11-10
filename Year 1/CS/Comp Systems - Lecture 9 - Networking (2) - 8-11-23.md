- Lecture Notes
    
    ## Network Protocols
    
    - DHCP
    - SMTP
    - POP3
    - IMAP
    - HTTP
    - NNTP
    - FTP
    - RIP
    - SNMP
    
    ## DHCP
    
    - The Dynamic Host Configuration Protocol (DHCP) is used to assign IP addresses to host computers on a network running TCP/IP. Before the introduction of DHCP, network admins had to assign IP addresses to host computers manually. This process was both time-consuming and error-prone
    - Each host must have a unique IP address & DHCP maintains a database
    - The DHCP Server service assigns IP addresses to individual hosts and maintains the database of IP address information, including IP addresses that are assigned, IP addresses that are available and other configuration information that can be supplied to clients along with the IP address
    - The DHCP Client service interacts with the Server service by requesting an IP address and in configuring other related information including the subnet mask and default gateway, which we will look at in detail later.
    
    ## SMTP
    
    - The Simple Mail Transport Protocol (SMTP) is used to transmit e-mail between e-mail servers and from e-mail clients (such as Outlook) to e-mail servers (such as Microsoft Exchange). Most e-mail clients use other protocols, such as POP3 or IMAP, to retrieve e-mail from the server
    - SMTP operates at the Application Layer and relies on the services of the underlaying layers of the TCP/IP protocol suite to provide data transfer services.
    
    ## POP3
    
    - Post Office Protocol (POP3) is a widely used e-mail application protocol that can be used to retrieve e-mail from and e-mail server for a client application such as Microsoft Outlook
    - POP servers configure mailboxes (actually directories or folders) for each e-mail account name. The server receives the mail for a domain and sorts it into these individual folders. A user then uses a POP client program (such as Outlook or Eudora) to connect to the POP server and download all the mail in that user’s folder to the user’s computer. When the mail messages are transferred to the client machine. they are normally deleted from the server.
    
    ## IMAP
    
    - Internet Message Access Protocol (IMAP) is used, like POP3, to retrieve mail from a server, and creates a mailbox for each user account. Unlike POP3, the client program can access the mail and let the user read, reply to or delete it while it is still on the server.
    - This s convenient for users because they never have to download mail to their client computers (saving space on their hard disks), and because they can connect to the server and have all their mail available to them from any computer, anywhere. If you use POP3 to retrieve your mail, any old mail that you’ve already downloaded is sitting on the computer you were using when you retrieved it, so if you’re using a different computer, you won’t be able to see it.
    
    ## HTTP
    
    - Hypertext Transport Protocol (HTTP) is the protocol used to transfer files used on the Internet to display Web pages. When you type an Internet address (a Uniform Resource Locator or URL) into your browser’s address window, it uses the HTTP protocol to retrieve and display the files located at that address
    - A URL normally contains a server name, a second level domain name, and a top-level domain name, with the parts of the address separated by dots. Individual folder and file names separated by slashes may follow
    
    ## NNTP
    
    - The Network News Transport Protocol (NNTP) is similar to SMTP, it that it allows servers and clients to exchange information, but in this case the information is exchanged in the form of news articles. NNTP was originally implemented on the Internet’s predecessor network, ARPANET
    - The collection of newsgroups is known as Usenet and it has grown into a huge network of servers hosting newsgroups. Today there are thousands of newsgroups devoted to discussion of every topic imaginable (and some that are unimaginable)
    - NNTP is implemented as an Application layer client/server protocol
    
    ## FTP
    
    - File Transfer Protocol (FTP) is used to transfer files from one host to another, irrespective of the hosts’ physical locations. It is one of the oldest Application layer protocols and was intitially ised on ARPANET to transfer files between mainframes. FTP is still widely used on the Internet to transfer files, and particularly for uploading web pages to remote servers. FTP transmits users’ passwords in clear text, so it is not a secure protocol.
    - In contrast to the single connections used by NNTP, HTTP and SMTP, two separate connections are established for an FTP session. One transmits commands and replies and the other transmits the actual data. By default, the command information is sent via TCP Port 21 and the data is sent via TCP Port 20 — watch out for hackers
    
    ## FTP in Action
    
    ![[Untitled 38.png|Untitled 38.png]]
    
    ## RIP
    
    - Routing Information Protocol (RIP) is used to exchange routing information among IP routers. RIP is a basic routing protocol designed for small to medium sized networks. It does not scale well to large IP-based networks. (including the internet)
    
    ## SNMP
    
    - Simple Network Management Protocol (SNMP) is used for communication between a network management console and network devices such as bridges, routers and hubs. This protocol facilitates the sharing of network control information with the management console.
    - SNMP uses a management system/agent framework to share relevant network management information. This information is stored in a Management Information Base (MIB) and contains a set of objects, each of which represents a particular type of network information such as an event, error, or an active session. SNMP uses datagrams to send messages between the management console and the agents
    - The application layer is complex, largely because applications and services can be developed that rely upon the services of the lower layers. This modular approach makes development less time consuming and more consistent across vendors, networks and systems, so new Application later protocols are constantly being developed.
    
    ## The core of networking…
    
    - The core of any network infrastructure is the directory-based system that supports the addressing and resource management of that networked system.
    
    ## Keeping track of stuff
    
    - Keeping track of everything on your network can be time consuming & difficult task
    
    ## So we need…
    
    - A comprehensive directory of objects
    - Bit like a phone book but far more flexible
    - To store information about organizations, sites, systems, users, shares and just about any other network object you can imagine.
    
    ## Issue
    
    - In AU there are probably around 17,000 users
    - 300 of them need to access a particular object
    - Do we really want to trawl through every single record and assign access to those who need it
    
    ## Groups
    
    - Simple solution… GROUPS
    - Set up a group which has access to the object in question
    - Then assign everyone who need access to that object to that group
    
    ## What is Active Directory
    
    ![[Untitled 1 18.png|Untitled 1 18.png]]
    
    ## What’s going on?
    
    - Active Directory is a specialist database designed to handle high-speed read and search operations matching users to the assets (hardware & software) on your network
    
    ## Active Directory
    
    - Hierarchical
    - Replicated
    - Extensible
    
    ## Hierarchical
    
    - Gives coherent structure and particularly facilitates the use of groups
    
    ![[Untitled 2 18.png|Untitled 2 18.png]]
    
    ## Replicated
    
    - So don’t store dynamic data there.
    - You can change what’s there and have it propagated
    
    ![[Untitled 3 16.png|Untitled 3 16.png]]
    
    ## Extensible
    
    - You can add your own classes and attributes.
    
    ## Structure
    
    There are 3 partitions (or ‘naming contexts’)
    
    ![[Untitled 4 15.png|Untitled 4 15.png]]
    
    ## They’re all objects
    
    - Everything tracked by Active Directory is an ‘object’ whatever it might be (user, system, resource or service)
    - Each object is described by attributes, but these differ depending on what the object is
    
    ## Attributes
    
    Example
    
    - User objects share attributes to store a username, full name and description
    - System objects have a separate set of attributes that include a host name, an IP address, and a location
    
    ![[Untitled 5 15.png|Untitled 5 15.png]]
    
    ![[Untitled 6 12.png|Untitled 6 12.png]]
    
    ## Schema
    
    - The set of attributes available for any given object type is called a schema.
    - The schema allows administrators to add attributes to object types (or classes) & have them propagate across the network without having to restart it.
    
    ![[Untitled 7 11.png|Untitled 7 11.png]]
    
    ![[Untitled 8 11.png|Untitled 8 11.png]]
    
    ![[Untitled 9 10.png|Untitled 9 10.png]]
    
    ## Domain Name Server (DNS)
    
    - Internet servers are addressed by a numerical IP address, not by the names we call our favourite sites.
    - DNS ‘name servers’ are computers which translate domain names into IP addresses.
    
    ## IP Addressing
    
    ![[Untitled 10 10.png|Untitled 10 10.png]]
    
    - A DNS name server responds to each query for a specific domain name from a web browser or e-mail program with the precise location on the exact web hosting server (using that server’s IP address) where that domain name — and thus web site or e-mail server — is located.
    - The DNS itself is a distributed database living on a hierarchy of special servers
    - A web browser makes a request for a website, this is passed up the hierarchy until the IP address for that site is found and passed back down to the web browser, which can then access it.
    - DNS is used to resolve a host name to an IP address in order to allow the delivery of network data packets… that can be anything, doesn’t have to be just a website.
    
    ## How was DNS developed
    
    - In the days before DNS, host name-to-IP resolution was accomplished via a text file called hosts. On ARPANET, this file was compiled and managed by the Network Information Center at the Stanford Research Institute
    - This plain text file contained the name and address of every single computer, but there was onlt a handful of computers on the network at the time. When a new computer was added, or a computer changed it’s IP address, the hosts file had to be edited manually and distributed to all the other computers. As the numbers of computers and networks increased and automated solution had to be devised and the specifications for a distributed naming system, called DNS, were developed
    
    ## Dynamic IP addressing
    
    - If you host a webserver in your home, you might not have a permanent IP address for it…
    - You see, your router — although it’s on the internet — gets assigned an IP address by your ISP, and that may change
    - So we need a special program that checks the IP address at intervals, then updates DNS as to where to find your webserver.
    
    ## TCP/IP addressing
    
    - IP addresses can be assigned automatically or statically. They can be assigned automatically using Dynamic Host Control Protocol (DHCP) or Automatic Private IP Addressing (APIPA) but in some cases it is better to configure then statically
    - Servers usually have a static IP address allocated to them as some of the components that you might want to install, for example an Active Directory (AD) or the Domain Name System (DNS), require the server to be configured with a static IP address.
    
    ## Running out of Addresses?
    
    - The concept of public and private addresses
    - Certain blocks of addresses are reserved for internal — or ‘private’ — use
    - Private IP addresses are assigned to a device by a router within the network, while an ISP assigns public IP addresses. In addition, public IP addresses can be any combination of numbers that do not fall within private IP address ranges
    
    ## Private IP Addresses:
    
    - 192.168.0.0 - 192.168.255.255 (65,536 IP addresses)
    - 172.16.0.0 - 172.31.255.255 (1,048.576 IP addresses)
    - 10.0.0.0 - 10.255.255.255 (16,777,216 IP addresses)
    
    ## How does it work?
    
    - Once your router makes its internet connection through your ISP, it sends internet activity to any computer connected to your router and is the basis of a networking innovation called a Network Address Translation (NAT)
    
    ## NAT
    
    - NAT is a process in which your router translates your private IP address into a public one so that it can send your traffic over the internet, keeping track of the changes in the process.
    - When the information comes back to your router, it reverses that change — from a public IP address into a private one — and forwards the traffic back to your computer.
    
    ## Finding me — Example
    
    - My public IP address is 50.63.209.48 — this is unique
    - And this computer’s IP address is 192.168.7.37 — this is not unique, there may be many computers with this IP on private networks!
    
    ## Threats to network security
    
    - External
    - Internal
    - Accidental
    
    ## Major computer threats
    
    - Email containing virus
    - Hackers
    - SPAM (not that bad)
    - ADWARE / SPYWARE
    - Browser Bugs
    
    ## Firewalls
    
    ![[Untitled 11 8.png|Untitled 11 8.png]]
    
    ![[Untitled 12 8.png|Untitled 12 8.png]]
    
    ## Firewall in action
    
    ![[Untitled 13 7.png|Untitled 13 7.png]]
    
    ## Encryption
    
    ![[Untitled 14 7.png|Untitled 14 7.png]]
    
    ## What do we need?
    
    - Confidentiality: only sender, intended receiver should “understand” message contents
        - sender encrypts message
        - receiver decrypts message
    - Authentication: sender, receiver want to confirm identity of each other
    - Message integrity: sender, receiver want to ensure message not altered (in transit, or afterwards) without detection
    - Access and availability: services must be accessible and available to users
    
    ## Friends and Enemies
    
    - Bob & Alice want to communicate securely
    - Trudy (intruder) may intercept, delete, add messages
    
    ![[Untitled 15 5.png|Untitled 15 5.png]]
    
    ## Who might Bob & Alice be?
    
    - Real life people
    - Web browser/server for electronic transactions (e.g. online purchases)
    - Online banking
    - DNS servers
    - Routers exchanging routing table updates
    
    ## What can an attacker do?
    
    - Eavesdrop: intercept messages
    - Actively insert messages
    - Impersonation: can fake (spoof) source address in packet (or any field in packet)
    - Hijacking: “take-over” ongoing connection by removing sender or receiver, inserting himself in place
    - Denial of service: prevent service from being used by others (e.g. overloading resources)
    
    ## Cryptography as protection
    
    ![[Untitled 16 5.png|Untitled 16 5.png]]
    
    ## Symmetric key cryptography
    
    - Bob & Alice share same key: K
    - e.g. key is knowing substitution pattern in mono alphabetic substitution cipher
    - But how do Bob and Alice agree on key value?
    
    ![[Untitled 17 5.png|Untitled 17 5.png]]
    
    ## Simple encryption scheme
    
    - substitution cipher: substituting one thing for another e.g. monoalphabetic cipher: substitute one letter for another
    
    ![[Untitled 18 5.png|Untitled 18 5.png]]
    
    ## Breaking encryption
    
    - cipher-text only attack: Trudy has ciphertext she can analyse
    - two approaches :
        - brute force: search through all possible keys
        - statistical analysis
    - known-plaintext attack: Trudy has plaintext corresponding to ciphertext
    - e.g. In monoalphabetic cipher, Trudy determines pairings for: {a, l, i, c, e, b, o}
    - chosen-plaintext attack: Trudy can get ciphertext for chosen plaintext
    
    ## Public and Private Keys
    
    ![[Untitled 19 5.png|Untitled 19 5.png]]
    
    ## Public key cryptography
    
    ![[Untitled 20 5.png|Untitled 20 5.png]]
    
    - Even if you have the public key, it should be impossible to compute the private key
    - RSA: Rivest, Shamir, Adelson algorithm
    
    ## Proving who you are…
    
    - Digital Signatures cryptographic technique analogous to hand-written signatures
    - sender (Bob) digitally signs documents establishing he is document owner/creator
    - verifiable, nonforgeable: recipient (Alice) can prove to someone that Bob, and no one else (including Alice), must have signed the document
    
    ## Digital signatures
    
    - Bob ‘signs’ his message with his private keys
    - Anyone can use Bob’s public key to read it & knows where it came from
    
    ![[Untitled 21 4.png|Untitled 21 4.png]]
    ![[Untitled 22 4.png|Untitled 22 4.png]]
    
    ## Public key certification
    
    - Certification authority (CA): binds public key to particular entity, E (person, router) registers its public key with CA
        - E provides “proof of identity” to CA
        - CA creates certificate binding E to its public key
        - Certificate containing E’s public key digitally signed by CA who says “this is E’s public key”
    
    ![[Untitled 23 4.png|Untitled 23 4.png]]
    
    ## Network Layer Confidentiality
    
    Between two network entities:
    
    - sending entities encrypts datagram payload, payload could be:
        - TCP or UDP segment, ICMP message, OSPF
    - all data sent from one entity to other would be hidden:
        - web pages, e-mail, P2P file transfers, TCP SYN packets
        - “blanket coverage”
    
    ## IPsec
    
    - Internet Protocol Security (IPsec) is a protocol suite for securing Internet Protocol (IP) communications by authenticating and encrypting each IP packet of a communication session.
    - IPsec is an end-to-end security scheme operating in the Internet Layer
    
    ## VPNs
    
    - Institution’s inter-office traffic is sent over public internet
        - encrypted before entering public Internet
        - logically separate from other traffic
    
    ![[Untitled 24 4.png|Untitled 24 4.png]]
    
    ## VPNs in action
    
    ![[Untitled 25 4.png|Untitled 25 4.png]]
    
    ## Access Rights Management
    
    ![[Untitled 26 4.png|Untitled 26 4.png]]
    
    ## Acceptable User Policies
    
    - Tell people what they may and may not do on an organisation’s system.
- YouTube
    
    # Network Devices
    
    ## Hosts
    
    Hosts are any device which can send or receive traffic.
    
    - Computer
    - Laptop
    - Phone
    - Printer
    - Server
    - Cloud Server
    - Any Internet of **Things** device
    
    All of these hosts must follow the same rules when sending a receiving data over the internet.
    
    There are two distinct types of host, **clients** and **servers**
    
    - Clients initiate requests, servers respond
    - This is relative and a server could become a client if it requests data from another server.
    
    A server is nothing more than a computer with software installed that knows how to respond to specific requests, like a web server.
    
    A web server is just a computer with software installed that tells it how to serve a web page.
    
    ## IP Addresses
    
    An IP address is the identity of the host
    
    Every host needs an IP to send or receive packets on a network, like how we all have an address or phone number.
    
    The IP is stamped on almost everything sent across a network, when a computer makes a request to a web server, it will send a packet, including what webpage it is asking for and included will be the source and destination IP’s, the source IP address is going to be the client IP address and the destination will be the server IP address, when the server sends a packet back it will stamp it but the server will be the source address and the client the destination, it’s a lot like mail
    
    IP addresses are 32 bits, we split this up into 4 bytes, and convert each byte into a decimal number, leaving us with:
    
    10001000000101100001000101100010 = 136.22.17.98
    
    These IP addresses are assigned hierarchically, it goes from the first number down to get move specific, this is related to subnetting.
    
    ## Network
    
    A network is what actually transports the traffic between hosts, In the most simplest forms, whenever you connect two hosts in any way, you have a network.
    
    A network is just a logical grouping of host devices that require similar connectivity.
    
    Networks can contains other networks, sometimes referred to as sub-networks
    
    Networks can connect to other networks, such as working from home or accessing school resources, to get these all connected without having to do so physically these networks are connected to a central network, the Internet, literally INTERconnected NETworks. These connections are usually handled by Internet Service Providers, hence the name hehe.
    
    ## Repeater
    
    Information being sent across a wire decays the longer the wire is, if the two computers are in the same room, this is not an issue, however say we are connecting host on the opposite side of a large building, we have a problem.
    
    If the signal fully decays before reaching the other side, then these two hosts cannot share data.
    
    In this case we need a repeater, a repeaters sole purpose is to take a signal in and repeat it stronger, this allows the connection of devices that span greater distances.
    
    ## Ease of expansion
    
    So far we have discussed networking with the view of connecting one host to another host, and then if we get a new one we must connect it to all pre-existing hosts, this can get very messy.
    
    Instead we create a device at the center on the network that all the other hosts can connect to, this can then receive information and funnel it out to the relevant destinations
    
    ## Hub
    
    A hub is nothing more than a multi-port repeater, if one computer wants to send a packet to another, it will send to the hub and the hub will just repeat it across all the other nodes
    
    This fixes the scale problem as this allows communication between hosts
    
    Everyone receives everyone else’s data, this is not very secure or efficient
    
    ## Bridge
    
    A bridge sits between hub-connected hosts, bridges only have 2 ports, one facing one set of hub-connected devices, and once facing the other.
    
    Bridges learn which hosts are on which side of the bridge, meaning information is only sent to the side that is necessary.
    
    So say 2 computers want to communicate on the same side of the bridge, the first computer will send out the packet, the hub will repeat it to all the computers on that side and the bridge, the bridge will get this packet but will not repeat it, as it knows it doesn’t need to cross the bridge.
    
    The main point is bridges can learn which hosts are connected on either side of it’s two ports.
    
    ## Switches
    
    A switch is like a combination of Hubs and Bridges, they are like hubs as it can have multiple ports, and they are like bridges as they can learn which host is connected to which port.
    
    The main difference is that they do this on a per-port basis and will keep any transfers contained to only the relevant ports.
    
    A switch controls communication within a network, networks all share the same IP address space.
    
    ![[Untitled 27 3.png|Untitled 27 3.png]]
    
    This set of devices could easily represent all the different hosts on your home network or a classroom.
    
    ## Routers
    
    Seeing as a switch can only facilitate communication within a network, we need another type of device to facilitate communication across networks, that device would be a router
    
    A router facilitates communication between networks, and is required to connect to the internet.
    
    Routers provide a traffic control point between networks (security, filtering, redirecting)
    
    They are a logical location to apply security policies as they sit on the boundaries between networks, traditionally switches could not perform such filtering (they can now)
    
    Routers learn the NETWORKS, that they are attached to, known as routes, stored in a routing table
    
    Routers have their own IP in each network they are attached to, like a host, this is called a gateway
    
    ## Gateway
    
    A hosts know way out of their own network, default gateway.
    
      
    
    Routers facilitate the communication between networks
    
    THE INTERNET IT JUST ROUTERS (kinda)
    
    # OSI Model
    
    ## OSI Model
    
    Purpose of networking: allow two host to share data with one another.
    
    Hosts much follow a set of rules to do so, such as how we follow rules for language to construct a proper sentence.
    
    The rules for networking are divided into 7 different layers, known as the OSI model.
    
    ![[Untitled 28 2.png|Untitled 28 2.png]]
    
    This is like all the systems of the human body, but for a network, if all these systems act as they should, then the goal of the network is achieved.
    
    ## 1: Physical - Transporting Bits
    
    - Computer data exists in the form of 1’s and 0’s
    - Something has to transport these bits between hosts
    - Level 1 Technologies: Cables, Wi-fi, Repeaters, Hubs
    - Note that the OSI model was invented before the creation of wifi and therefore wifi is classed as physical when the tangential property of it can be debated
    
    ![[Untitled 29 2.png|Untitled 29 2.png]]
    
    ## 2: Data Link - Hop to Hop
    
    - Interacts with the Wire (i.e. The Physical Layer)
        - NIC — Network Interface Cards / Wi-Fi Access Cards
    - Addressing Scheme — MAC addresses
        - 48 bits, 12 hex bytes
        - 94-65-9C-3B-8A-E5 (Windows
        - 94:65:9C:3B:8A:E5 (Unix)
        - Every NIC has a unique MAC address
    - Level 2 Tech: NICs, Switches
    - Often communication between hosts requires multiple hops, say from router to router, each of these routers has it’s own MAC address.
    
    ![[Untitled 30 2.png|Untitled 30 2.png]]
    
    ## 3: Network - End to End
    
    - Addressing Scheme — IP Addresses
        - 32 bits, represented as 4 octets, each 0-255
    - Level 3 Tech: Routers, Hosts (Anything with an IP)
    
    ## Why 2 Addresses?
    
    - They facilitate different purposes
    - They are linked by something called the Address Resolution Protocol which ties these two addresses together.
    
    ## 4: Transport - Service to Service
    
    - Distinguish data streams
    - Addressing Scheme — Ports
        - 0-65535 — TCP — favors reliability
        - 0-65535 — UDP — favors efficiency
    - Adds another header for this on the packet, similarly to the L2 & L3 headers
    
    ![[Untitled 31 2.png|Untitled 31 2.png]]
    
    - Servers listen to requests to pre-defined ports
    - Clients select random ports for each connection, this will be the return report.
    
    ![[Untitled 32 2.png|Untitled 32 2.png]]
    
    - This can be used to distinguish between multiple applications
    - One host can send multiple requests to the same server, like when you have multiple tabs of the same web page, they just use different random SRC ports to distinguish.
    - TCP 1.1.1.1:9999 ←→ 3.3.3.3:80
    
    ## 5, 6, 7: Session, Presentation, Application
    
    - Currently the distinction between these layers is quite vague and applications can implement their functions as they choose
    - Other networking models combine these into one layer.
    
    ![[Untitled 33 2.png|Untitled 33 2.png]]
    
    ## Sending Data - Encapsulation
    
    1. An application has created some form of information it wants to send across a network
    2. This data is first sent to L4, this will add a header to the data to facilitate the goal which is service2service, it will add if it is TDP or UDP and the relevant ports, the construct of a L4 Header + Data is called a SEGMENT
    3. This segment is then passed down the the next layer, L3, This layer will add another header to this data, this header will facilitate the goal of L3 which is end2end so this header will contain a source and destination IP address, the construct of a L3 Header + Data is a PACKET (notice that headers from previous layers aren’t seen by later layers and just appear as part of the data)
    4. This packet is then passed down to L2, which will add yet another header, this time facilitating hop2hop delivery, meaning it will contain the relevant MAC addresses, the construct of an L2 header + Data is a FRAME and that FRAME gets converted to binary and then put on the physical layer or “wire”
    
    ## Receiving Data - De-Encapsulation
    
    So this basically does that in reverse, it checks each header and then removes it as it makes it’s way up the stack, checking at each layer to see if it should have actually received this data or not.
    
    ## OSI Final Points
    
    - Network devices operate at specific levels and therefore only look at the information relevant to them
    - Different layers have different protocols
    - Exceptions to each of these — for example if you take a router which typically operates at layer 3 but configure it whatever, it can now look into L4
    - ARP also doesn’t fit into a specific model as it links L2 - L3
    - OSI is simply a model — not everything adheres to it
    
    ![[Untitled 34 2.png|Untitled 34 2.png]]
    
    # Host Communication
    
    ## Host’s on the same Network
    
    - Host’s aren’t very smart and have no idea what they are actually connected to, whether it be a switch or another computer
    - Lets say A and B are hosts and they are directly connected (they don’t know this)
        - Both hosts have a NIC and therefore a MAC address
        - Both hosts have IP addresses and Subnet Masks
            - The Subnet Mask tells you the size of the IP network
            - www.SubnetIPv4.com
    - Host A has some data to send to Host B
    - Host A knows the IP address of Host B
        - how?
    - Host A knows that Host B’s IP is on its own IP Network
    - Host A can create the L3 header to attach to the data it is trying to send
        - L3 - end2end (ip2ip)
    - A does not know B’s MAC address
        - A must use ARP (Address Resolution Protocol) this is the whole point of ARP it links IP and MAC
        - A sends out an ARP request for the MAC address for the associated IP address (this request will include A’s IP and MAC addresses)
        - e.g. (obvs not in english) “**If anyone on this network has the IP address 10.1.1.33, send me your MAC. my IP / MAC is 10.1.1.22 / a2a2**”
        - Since we don’t have B’s MAC address we send this ARP as a broadcast to everything on the Network (It has a special MAC address ff:ff:ff:ff:ff:ff which is the reserved MAC address to send a packet to everything on the network.
        - ARP Mappings are stored in an ARP Cache, at the moment A’s ARP cache says we are trying to resolve 10.1.1.33 to a MAC address
        - When B receives A’s ARP request it can populate its ARP cache with A’s information
        - B responds to the ARP request by sending an ARP response, because B has A’s IP and MAC it can send it directly
    - Now A knows B’s Mac address and can create an L2 header containing the MAC address of B
        - This accomplishes L2: hop2hop
    - **The data is finally sent to B**
        - Upon arrival the headers are discarded and the data is processes by whatever program needs it.
        - If B wants to respond it already has all of A’s information to do so
    
    ## Host’s on the Internet
    
    - A wants to send information to C
    - A, C and the Router have MAC and IP addresses
        - They all have a subnet mask of 255.255.255.0
    - A, C and the Router all have an ARP cache (we will focus on A’s)
    - A knows C’s IP address
    - A knows C is on a foreign network by comparing to it’s own IP
    - A can create a L3 header as it knows C’s IP
        - L3 - end2end
    - A needs to create a L2 header
        - L2 - hop2hop
        - The next hop is the router
        - We don’t know the routers MAC address so we use ARP
            - How does A know the routers IP address, because the router is configured as the default gateway out of the network
        - A broadcasts an ARP request asking for the default gateway’s MAC address, this request contains A’s IP and MAC address
        - The Router will issue a response directly to A with the IP and MAC address
    - A can now create the L2 header, now the data can be sent across the wire
    - The router will discard the L2 header upon receival, the router now takes over
        - A’s job is now done
        - A’s first step is always to determine if the target is local or foreign
            - foreign - ARP for default gateway
            - local - ARP for Target IP
    
    # Switch Communication
    
    - This describes the rules of switching.
    - Switches move data WITHIN networks, therefore any devices communicating through a switch belong to the same network
    - The switch is a L2 device and will therefore only look at the L2 header to make decisions, to the switch, everything after the L2 header is random data
    
    ## Communication Across a Switch
    
    _For this we will assume that Host A knows the MAC address of Host B_
    
    - Switches use and maintain a MAC address table, which is a mapping of the switch ports to MAC addresses
    - Switches perform 3 actions
        - Learn: Update MAC Address Table with mapping of Switch Port ←→ Source MAC
        - Flood: Duplicate and send frame to all switch ports (except src)
        - Forward: Use MAT to deliver frame to appropriate switch port.
    
      
    
    - A is going to send some data across a wire
    - This arrives to the switch in port 5, this allows the switch to perform it’s first action, which is to learn, it now knows that a1a1 is connected to Port 5.
    - Now it will look at the destination address of this frame (L2 + Data) and determine it must go to the device with the MAC address d4d4, the switch does not know which port this is connected to, this is when the switch duplicates the frame and sends it to all ports; flooding (doesn’t forward back to the original one obviously)
    - All the hosts that do not need this frame will simply discard (they aren’t the DST MAC address)
    - D will realise that it is the intended recipient of the frame
    - D will more than likely have some form of response for A which will contain the SRC: d4d4 and the DST: a1a1
    - D will send this across the wire to the switch, the switch will then learn about D, it know knows the mapped port for D
    - Because now it knows how to deliver a frame to a1a1 because it is on the MAC address table, it will forward the frame to A only.
    
    _Process would be identical if D was a default gateway._