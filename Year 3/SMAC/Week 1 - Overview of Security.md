## Definition

The NIST Internal/Inter-agency Report defined the term computer security as follows:

*Measures and controls that ensure **confidentiality**, **integrity**, and **availability** of information systems assets including hardware, software, firmware, and information being processed, stored and communicated*

## Security Objectives

- **Confidentiality**:
	- Also known as data confidentiality.
	- The property that information is not made available or disclosed to authorised, individuals, entities, or processes.
	- A loss of confidentiality is the unauthorised disclosure of information.
- **Integrity**:
	- Data integrity
		- Ensures that data and program are charged only in a specific and authorised manner
		- A loss of data integrity is the unauthorised modification or destruction of information
	- System Integrity
		- Ensures that a system performs its intended function is an unimpaired manner, free from deliberate or inadvertent unauthorised manipulation of the system.
- **Availability**:
	- Ensures that systems work promptly and that service is not derived to authorised users
	- A loss of availability is the disruption of access to or use of information an information system

![[Pasted image 20250929140032.png]]

## Authenticity and Accountability

- **Authenticity**:
	- The property of being geniuine and being able to be varified and trusted, confidence in the validity of a transmission, a message, or a message originator.
	- This means verifying that users are who they say they are and that each input arriving at the system came from a trusted source.
- **Accountability**:
	- The security goal that generates the requirement for actions of an entity to be traced uniquely to the entity.
	- This supports non-rupidation, deterrence, fault isolation, intrusion detection and prevention, and after-action recovery and legal action.
	- It must be possible to trace a security breach to a responsible party.
	- Systems must keep records of their activities to permit later forensic analysis to trace security breaches or to aid in transaction disputes.

## Levels of impact

- **Low**:
	- The loss could be expected to have a limited adverse effect on organisational operations, organisational assets, or individuals.
- **Moderate**:
	- The loss could be expected to have a serious adverse effect on organisation operations, organisational assets, or individuals
- **High**:
	- The loss could be expected to have a severe or catastrophic adverse effect on organisational operations, organisational assets, or individuals.

![[Pasted image 20250929141309.png]]

## Key Terms

**Adversary (threat agent)**: Individual group, organisation, or government that conducts or has the intent to conduct detrimental activities.
**Attack**: Any kind of malicious activity that attempt to collect, disrupt, deny, degrade, or destroy information system resources or the information system resources or the information itself.
**Countermeasure**: A device or techniques that has an objective that impairment of the operational effectiveness of undesirable or adversarial activity, or the prevention of espionage theft, or unauthorised access to or the use of sensitive information or information systems.
**Risk**: A measure of the extent to which an entity is threatened by a potential circumstance or event, and typically a function of 1) the adverse impacts that would arise if the circumstance or event occurs; and 2) the likelihood of an occurrence.
**Security Policy**: A set of criteria for the provision of security services. It defined and constrains the activities of a data processing facility in order to maintain a condition of security for systems and data.
**System Resource (Asset)**: A major application, general support system, high impact program, physical plant, mission critical system, personnel, equipment, or a logically related group of systems.
**Threat**: Any circumstance or event with the potential to adversely impact organisation operations (including missions, functions, image, or reputation), organisational assets, individuals, other organisations, or the Nation through an information system via unauthorised access, destruction, disclosure, modification of information, and/or denial of service.
**Vulnerability**: Weakness in an information system, system secutiry procedures, internal controls, or implementation tha tcould be exploited triggered by a threat source.

## Vulnerabilities, Threats and Attacks

- Categories of vulnerabilities
	- Corrupted (loss of integrity)
	- Leaky (loss of confidentiality)
	- Unavailable or very slow (loss of availability)
- Threats
	- Threat is a potential cause of hard
	- Capable of exploiting vulnerabilities
	- Represent potential secutiry harm to an asset
- Passive - Attempt to learn or make use of information from the system that does not affect system resources.
- Active - Attempt to alter system resources or affect their operation
- Insider - Initiaited by an entity inside the secutiry parameter
- Outsider - Initiated from outside the perimeter

## Countermeasures

![[Pasted image 20250929144233.png]]

## Formula

The formula is as follows 

```
ALE = SLE x ARO
```

Where:

 - SLE (Single Loss Expectancy) is the expected cost of a single occurrence of a particular risk, including direct and indirect costs such as repair, replacement, and downtime.
 - ARO (Annual Rate of Occurrence) is the number of times a particular risk is expected to occur in a given year.

So, the calculation determines the expected financial loss per year due to that risk.

Suppose an organisation is considering the risk of a data breach. The following information is available:

1. Single Loss Expectancy (SLE) = $100,000

This represents the expected cost of a single data breach occurrence, including direct and indirect cost such as lost business, reputation damage, and legal fees.

2. Annual Rate of Occurrence (ARO) = 2

This represents the number of times the organisation expects a data breach to occur in a given year based on industry statistics or experience.

Using the formula

$100,000 * 2 = $200,000

So the annualised loss expectancy data is $200,000, meaning they expect to lose $200,000 per year due to data breaches.

![[Pasted image 20250929150351.png]]

## Scope of Computer Security

![[Pasted image 20250929150423.png]]

## Cyber-security Threats Overview

| Threat              | Description                                    | Potential Consequences                          | Real-World Example                                    |
| ------------------- | ---------------------------------------------- | ----------------------------------------------- | ----------------------------------------------------- |
| Phishing            | Deceptive emails or messages to trick users    | Data theft, Financial loss, Identity compromise | Google and Facebook lost $100M to phishing            |
| Malware             | Malicious software like viruses, worms, trojan | System damage, Unauthorised access, Data loss   | ILOVEYOU virus (2000) affected millions               |
| Ransomware          | Encrypts data and demands payment              | Data loss, Downtime, Financial Loss             | Colonial Pipeline attack (2021) disrupted fuel supply |
| DDoS                | Overwhelms system to deny service              | Downtime, Revenue loss, Brand damage            | Dyn DNS attack (2016) took down major sites           |
| MitM                | Intercepts communication between parties       | Data Interception, Session hijacking            | Enquifax breach (2017) involved unencrypted           |
| SQL Injection       | Malicious SQL to manipulate databases          | Data Breach, Unauthorised access                | Heartland Breach (2008) compromised 100M records      |
| Zero-Day            | Exploits unknown vulnerabities                 | System compromised, No patch available          | Stuxnet worm (2010) exploited 4 zero-day flaws        |
| Insider Threat      | Risks from within an organisation.             | Sabotage, Data leaks                            | Edward Snowden leaked NSA                             |
| Credential Stuffing | Uses stolen credentials for access.            | Account Hihacking, Fraud                        | Zoom accounts compromised in 2020                     |
| Social Engineering  | Manipulate people to breach security           | Data access, Identity theft                     | Twitter Hack (2020) via employee manipulation         |
| Unpatched Software  | Known flaws left unpatched                     | Increased risk, Compliance issues               | Equifax Breach (2017) from unpatched Apache           |
| IoT Vulnrabilities  | Insecure internet-connected devices.           | Privacy Risks, Botnets                          | Mirai Botnet (2016) used IoT devices for DDoS         |
## Computer and Network Assets, With Examples of Threats

![[Pasted image 20250929152625.png]]

## Passive and Active Attacks

 - **Passive Attack**:
	 - Attempts to learn to make use of information from the system but does not affect system resources.
	 - Eavesdropping on, or monitoring of, transmissions.
	 - Goal of attacker is to obtain information that is being transmitted.
	 - Two types:
		 - Release of message contents
		 - Traffic analysis

 - **Active Attack**:
	 - Attempts to alter system resources or affect their operation
	 - Involve some modification of the data stream or the creation of a false stream
	 - Four categories:
		 - Replay
		 - Masquerade
		 - Modification of messages
		 - Denial of service

## Fundamental Security Design Principles

![[Pasted image 20250929153147.png]]

## Attack Surfaces

Consist of the reachable and exploitable vulnerabilities in a system

Examples:

![[Pasted image 20250929153313.png]]

## Attack Surface Categories

![[Pasted image 20250929153538.png]]

![[Pasted image 20250929153621.png]]

## Computer Security Strategy

- Security Policy
	- Formal statement of rules and practices that specify or regular how a system or organisation provides security services to protect sesitive and critical system resources
- Security Implementation
	- Invokes four complementary courses of action:
		- Prevention
		- Detection
		- Response
		- Recovery
- Assurance
	- Encompasing both system design and design system implementation, assurance s an attribute of an infomation system that provides grounds for having cofidence that the system operates such that the system's security policy is enforced.
- Evaluation
	- Process of examining a computer product or system with respect to certain criteria.
	- Involves testing and may also involve formal analytic or mathematical techniques.

## Standards 

Standards have developed to cover management practices and the overall architecture security mechanisms and services.

The most important of these organisation are:

 - **National Insititute of Standard Technology (NIST)**:
	 - NIST is a U.S. federal agency that deals with measurement science, standard technology related to U.S. government use and to the promotion of U.S. private sector innovation.
 - **Internet Society (ISOC)**:
	 - ISOC is a professional membership society that provides leadership in addressing issues that confront the future of the internet, and is the organisation home for the groups respoinsible for Internet infrastructure standards.
 - **International Telecommunication Union (ITU-T)**:
	 - ITU is United Nations agency in which governments and the private sector coordinate global telecom networkds and services.
 - **International Organisation for Standardisation (ISO)**:
	 - ISO is a non-governmental organisation whose work results in international agreements that are published as International Standards.

