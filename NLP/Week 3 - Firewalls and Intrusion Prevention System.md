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