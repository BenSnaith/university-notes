## What is a firewall

*An integrated collection of security measures that are designed to prevent unauthorised access to a networked computer system* - White G. (2003)

## The Needs for Firewalls

 - Internet connectivity is essential, however it creates a threat.
 - Effective means of protecting LANs.
 - Inserted between the premises network and the Internet to establish a controlled link, can be a single computer system or a set of two or more system working together.
 - Used as a perimeter defence, single choke point to impose security and auditing insulates the internal systems from external networks

## Firewall Characteristics

##### Design Goals

All traffic from inside to outside, and vice versa, must pass through the firewall.
Only authorised traffic as defined by the local security policy will be allowed to pass.
The firewall itself is immune to penetration.

## Firewall Access Policy

 - A critical component in the planning and implementation of a firewall is specifying a suitable access policy
	 - This list the types of traffic authorised to pass through the firewall
	 - Includes address ranges, protocols, applications and context types.
 - This policy should be developed from the organisation's information security risk assessment and policy.
 - Should be developed from a broad specification of which traffic types the organisation needs to support
	 - Then refied to detail the filter elements which can then be implemented within an appropriate firewall topology.

## Firewall Filter Characteristics

 - **IP Address and Protocol Values
	 - This type of filtering is use by packet filter and state-ful inspection firewalls
	 - Typically used to limit access to specific services
 - **Application protocol**
	 - This type of filtering is used by an application-level gateway that relays and monitors the exchange of information for specific application protocols.
 - **User Identity**
	 - Typically for inside users who identify some form of secure authentication technology.
 - **Network Activity**
	 - Controls access based on considerations such as the time or request, rate of requests, or other activity patterns.

## What a firewall can and cannot do?

 - **Can do**
	 - Security gateway
	 - Traffic control device
	 - Packet filtering device
	 - Routing
	 - Enforce a security policy
	 - Logging
	 - Secure the network from external attacks
 - **Cannot Do**
	 - Firewall is only one piece of the large complex puzzle of network security
	 - Not an authentication server
	 - Not a remote access server
	 - Cannot see the content of encrypted packets
	 - Cannot see all the traffic if not positioned properly
	 - Not a malicious code scanner
	 - Not an IDS

## Terminology

 - **Stateless Firewall**: The firewall makes a decision on a packet by packet basis.
 - **Stateful Firewall**: The firewall keeps state information about transactions (connections).
 - **NAT - Network Address Translation**: Translates public IP address(es) to private IP address(es) on a private LAN.

## Firewall Categories

 - **Firewall Methods**:
	 - Packet filters
	 - Stateful Packet Inspection (SPI)
	 - Proxy Firewalls
	 - Stateful Multilayer Packet Inspection
 - **Firewall Types**:
	 - Hardware
	 - Software

## Firewall Methods: Packet Filters

![[Pasted image 20251007124941.png]]

![[Pasted image 20251007125004.png]]

## Firewall Methods: Stateful

![[Pasted image 20251007125147.png]]

## Firewall Methods: Proxy

 - Uses protocol information or application information
 - Each service needs a proxy e.g. Web proxy
 - Filter on specific commands e.g. `http:post` or `http:get`

![[Pasted image 20251007125248.png]]

## Firewall Methods: Stateful Multilayer Packet Inspection

 - Combined other 3 types (except no proxys).
 - Algorithms used to recognise application layer data.
 - Examines entire packet. Headers and data. Blurring the line between firewall and IDS.

![[Pasted image 20251007125411.png]]

## Firewall Categories

 - **Hardware**:
	 - Stand-alone product - *Needs to be compatible*
	 - Can be effective with little or no configuration - *Can't protect from some threats*
	 - Uses packet filtering to examine the header - *Connection speed effects*
	 - Easier to maintain and administer - *Manipulation is easy*

## Firewall Risks and Disadvantages

![[Pasted image 20251007125640.png]]

## Placement of the Firewall

1. The structure of your network (sections, subnets, DMZ)
2. The traffic patterns
3. Protect all internet access points and gateways
4. Remote access
5. Special needs of your infrastructure

![[Pasted image 20251007125742.png]]

## Firewall rules management

*Deny by default, allow by exception*

 - Rules = filters
 - Pre-configured firewalls are not good practice, you should:
	 - Do an inventory of essential **business applications & communications**
	 - Determine protocols/ports/IP @ of **valid traffic**
	 - Write the rules and test them in a lab environment
	 - Obtain approval for the rule sets
	 - Document the rules into a security policy

## Firewall enhancements

First, get a reliable filtering device, then you could add a few add-ons such as:
 - IDS/IPS
 - Malware scanning
 - VPN end-points
 - Unified Threat Management (UTM)

But don't forget to check:
 - Updates of the add-on
 - Network performance

## Firewall management and security

 - **Best practices for firewall management**
 - Design a complete security solution around the firewalls
 - **Mitigating** firewall threats and exploits and **testing** the firewal security.
 - Managing and monitoring the **Firewall**
	 - **Snort**: can detect firewall breaches.
	 - **Backtrack, netcat**: hack your own firewall
	 - **Syslog**: properly managing logs
	 - **Wireshark**

## DMZ Design: De-militarised Zone

![[Pasted image 20251007130428.png]]

## Goals of a DMZ

 - The core goal of DMZ is to segregate devices, systems, sevices and applications based on risk.
 - DMZ exists to mitigate risk by isolating certain services and function in a separate segment of the network.
 - DMZ is used to add an additional layer of security in a layered security model.

## DMZ Architecture

 - DMZ use a firewall to restrict access from internet to private LAN to protect against compromises.
 - Example:
	 - Allow connections from Internet to mail server on port 25 (SMTP)
	 - Allow connections from intranet to mail server over port 993 (secure IMAP)
 - Two of the most basic DMZ design architecture are:
	 - A single firewall.
	 - Dual firewalls.

## DMZ design with a single firewall

 - A single firewall with at least 3 network interfaces:
	 - 1st firewall interface: The external network (Internet)
	 - 2nd firewall interface: The internal network
	 - 3rd firewall interface: DMZ
 - The firewall will handle all of the traffic going to ht eDMZ as well as the internal network.

## DMZ design with Dual firewall

 - More secure approach is to use two firewalls to create a DMZ
	 - The first firewall (also called the "front-end") configured to allow traffic destined to the DMZ only.
	 - The second firewall (also called the "back-end") allows only traffic from the DMZ to the internal network.

## DMZ Summary

 - DMZ always you to completely segment your network in terms of trust. You can initiate connections to DMZ and Internet, but neither of those two networks can initiate connections to you.
 - It is generally inappropriate to locate a Critical servers (e.g Radius) in a DMZ segment.
 - DMZ designers should be aware of protocol vulnerabilities.
 - Firewall or router should be configured to initiate a log message or rule alert to notify administrator.
