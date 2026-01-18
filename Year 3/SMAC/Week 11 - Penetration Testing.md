### Introduction

 - Definition of Penetration Testing.
 - Who needs Penetration Testing.
 - Penetrating Testing Viewpoints.
 - Phases of Penetration Testing:
	 - Reconnaissance.
	 - Scanning.
	 - Vulnerability Testing and Exploitation.

### Penetration Testing

Definition of Penetration Testing

 - A penetration test or pentest is a test evaluating the strength of all security controls on the computer system. Penetration tests evaluate procedural and operational controls as well as technological controls.

### Who needs Penetration Testing

 - Banks/Financial Institutions, Government Organisations, Online Vendors, or any organisation processing and sorting private information.
 - Most certifications require or recommend the penetration tests be performed on a regular basis to ensure the security of the system.
 - PCI Data Security Standard's requires organisations to perform applications and penetrations tests at least once a year.

### Penetration Testing Viewpoints

 - External vs. Internal
	 - Penetration testing can be performed from the viewpoint of an external attacker or a malicious employee.
 - Overt vs. Covert
	 - Penetration testing can be performed with or without the knowledge of the IT department of the company being tested.

### Phases of Penetration Testing

- Reconnaissance.
- Scanning.
- Vulnerability Testing and Exploitation.
- Reporting.

### Types of Reconnaissance

Purpose: To discover as much information about a targer (individual or organisation) as much as possible.

There are two methods used to obtain data:

 - **Passive Reconnaissance**:
	 - Gather information without engaging any action with the target network.
	 - Uses public information / public intelligence.
	 - May use technical and non-technical tools / techniques.
- **Active Reconnaissance:
	- Engage with the target network to gather information.
	- Typically uses technical tools.

### Passive Reconnaissance

Gathering freely available public data from:

 - Cached web pages.
 - Job postings.
 - Professional profiles.
 - Troubleshooting mailing lists.
 - News archives.
 - Social media.
 - User groups.
 - Job sites.

Tools:

 - WHOis
 - Web retrieval
 - Sniffers
 - Google
 - shodanhq.com
 - Passive fingerprinting
 - Host
 - Facebook graph search

Adv / Dis

 - Adv:
	 - Doesn't raise suspicious.
	 - Increases the chances of a successful attack.
 - Dis:
	 - It is time consuming.
	 - May not produce 100% accurate / valid results.
	 - The amount of information gathered may be overwhelming.

### Active Reconnaissance

 - Active reconnaissance techniques / tools allow gathering preliminary information about the network.
	 - DNS lookup (e.g., `nslookup`)
	 - DNS zone transfer -> legitimate synchronisation between DNS servers.
	 - DIG lookup -> allows attempting a DNS zone transfer.
 - Active reconnaissance is easy to detect, therefore, put the attackers at risk but...
	 - It may be very rewarding for the success of the next stages, for example, by recovering a list of valid IP addresses used by an organisation.

### What is scanning a target

 - Scanning is about actively probing a system to find what is attackable -> i.e., find entry points to a network / specific target.
	 - In some aspects there is a fuzzy line between active reconnaissance & scanning.
 - Goal: Obtain a network map and find vulnerabilities.

### What can be obtained via scanning

 - Scanning can provide information such as determining:
	 - If a system is alive
	 - Open TCP/UDP ports
	 - Protocols used
	 - Services running
	 - Operating systems / versions installed
	 - Deployed defences
	 - Resources or shares on the network
	 - Usernames or groups assigned on the network
	 - Last tine user logged on
	 - Known vulnerabilities

### Example of scanning techniques

 - Ping / Ping sweep
 - Banner Grabbing
 - Web-based directory enumeration
 - Firewall enumeration & fingerprint
 - DNS enumeration
 - Others

### Vulnerability Testing and Exploitation

Purpose: To check hosts for known vulnerabilities and to see if they are exploitable, as well as to assess the potential severity of said vulnerabilities.

 - Methods:
	 - Remote vulnerability scanning (Nessus, OpenVAS)
	 - Active exploiting testing:
		 - Login checking and brute forcing.
		 - Vulnerability exploitation (Metasploit, Core Impact)
		 - 0 day and exploit discovery (Fuzzing, program analysis)
		 - Post exploitation techniques or assess severity. (Permission levels, backdoors, rootkits, etc.)

### Reporting

Purpose: To organise and document information found during the reconnaissance, network scanning, and vulnerability testing phases of a pentest.

  - Methods:
	  - Documentation tools (Dradis)
		  - Organises information by hosts, services, identified hazards and risks, recommendations to fix problems.

### How to become a Penetration Tester

 - Stay up to date on recent developments in computer security, reading newsletters and security reports are a good way to do this.
 - Becoming proficient with C/C++ and a scripting language such as PEARL.
 - Microsoft, Cisco, and Novell certifications.
 - Penetration Testing Certifications.
	 - Certified Ethical Hacker (CEH).
	 - GIAC Certified Penetration Tester (GPEN).

### Vulnerability scanning vs. Penetration testing

 -  A penetration test is a test evaluating the strengths of all security controls on the computer system.
 - A vulnerability scan is an automated process that focuses on finding known vulnerabilities without exploiting them.
 - A penetration test uses the same methods an attacker might use to exploit systems. Whereas a vulnerability scan can be automated, a penetration test requires a certain level of expertise and human interaction. Penetration testing can be performed across the whole organisation looking at the risk form a human element to your applications and infrastructure depending on where personal data is held or accessed.
 - Because vulnerability scans can only identify known vulnerabilities, they cannot find zero-day exploits.
 - A good penetration tester can link multiple vulnerabilities to be able to compromise the system, analyse the vulnerability scans to exploit weakness and create and use specialist tools during testing.
 - Vulnerability scan is predictable in terns of when it is taking place is known to the employee. Penetration testing may or may not be predictable.




