### Security Information and Event Management (SIEM) Systems

 - Combining security information management (SIM) and security event management (SEM), security information and event management (SIEM) offers real-time monitoring and analysis of events as well as tracking and logging of security data for compliance or auditing purposes.
 - Provide a centralised, uniform audit trail storage facility and a suite of audit data analysis programs.

### SIEM Configuration

There are two general configuration approaches:

 - Agentless.
	 - The SIEM server receives data from individual log generating hosts without needing to have any special software installed on those hosts.
 - Agent-based.
	 - An agent program is installed on the log generating host to perform event filtering and aggregation and log normalisation for a particular type of log, and then transmit the normalised log data to an SIEM server, usually on a real-time or near-real-time basis for analysis and storage.

### Benefits of SIEM

 - Advanced real-time threat recognition.
 - Regulatory compliance auditing.
 - AI-driven automation.
 - Improved organisational efficiency.
 - Detecting Advanced and Unknown Threats.

Using integrated threat intelligence feeds and AI technology, SIEM solutions can successfully mitigate against modern-day security breaches such as:

 - Insider threats.
 - Phishing attacks.
 - SQL injection.
 - DDoS attacks.
 - Conducting forensic investigations.
 - Assessing and Reporting on Compliance.
 - Monitoring Users and Applications.

### How does SIEM work?

At the most basic level, all SIEM solutions perform some level of data aggregation, consolidation and sorting functions in order to identify threats and adhere to data compliance requirements. While some solutions vary in capability, most offer the same core set of functionality:

 - **Log Management**: SIEM captures event data from a wide range of source across an organisation's entire network.
 - **Event Correlation and Analytics**

Event correlation is an essential part of any SIEM solution. Utilising advanced analytics to indentify and understand intricate data patterns, even correlation provides insight to quickly locate and mitigate potential threats to business security. SIEM solutions significantly improve mean time to detect (MTTD) and mean time to respond (MTTR) for IT security teams by offloading the manual workflows associated with the in-depth analysis of security events.

 - **Incident Monitoring and Security Alerts**

Because they enable centralised management of on-premise and cloud-based infrastructure, SIEM solutions are able to identify all entities of the IT environment.

 - **Compliance Management and Reporting**

Due to the automated data collection and analysis that it provides, SIEM is a valuable tool for gathering and verifying compliance data across the entire business infrastructure.

### SIEM Features

SIEM products usually include several features to help users, such as the following:

 - **Graphical User Interfaces (GUIs)** that are specifically designed to assist analysts in identifying potential problems and reviewing all available data related to each problem.
 - **A security knowledge base** with information on known vulnerabilities, the likely meaning of certain log messages, and other technical data; log analysts can often customise the knowledge base as needed.
 - **Incident tracking and reporting capabilities** sometimes with robust workflow features.
 - **Asset information storage and correlation**, e.g., giving higher priority to an attack that targets a vulnerable OS or a more important host.

### SIEM Software

![[Pasted image 20251230110155.png]]

### SIEM Challenges

 - **Cost**: A commercial SIEM solution for a large company can cost millions of dollars, but some open-source SIEMs are free. An organisation's size, system complexity, functional and performance requirements, and appetite for custom development should all help inform its choice for SIEM. While millions of dollars for an off-the-shelf software product may seem exorbitant at first blush, its purchase will depend on the needs of the organisation. If a company needs to create custom features and pay for expert support, maintenance, and training, a free open-source solution may end up costing more than the supported commercial support.
 
 - **Data Portability**: Requirements evolve, and the SIEM that meets today's needs will someday need replacing. Before choosing a SIEM, ensure that you will have a way to export your saved data in a standard format that most other SIEMs can read. Knowledge that you store in the SIEM, such as saved searched or data visualisations, tend to be SIEM specific and you will likely need to rebuild such knowledge bases when you switch products.

 - **Log-Source Compatibility**: SIEMs are continually becoming more flexible in terms of the types of data they can import and the ease with which they let users define new data types, but some SIEMs are better than others in this regard. Depending on the data type and the system that  is generating a given set of logs, SIEMs may require you to install agents or intermediary severs to collect logs. Once you know the logs that are important to you, you can identify which SIEMs already read those data logs, which could read those logs with a bit of configuration, and which would require agents.

 - **Deployment Complexity**: Because SIEMs can touch thousands of systems in an enterprise, deploying them is generally a complex undertaking. Deployment will likely require a variety of configuration changes  (for example, updating system audit policies, and configuring devices to send logs to a new IP), some of which will be unpredictable side effects of the intricacies of your environment. For an enterprise with over 1,000 systems, a full deployment is likely to take months and require coordination across a variety of teams.

 - **Customisation**: SIEM vendors compete on the basis of depth of built-in functionality and ease of customisation. Some SIEMs come with extensive user interfaces and a number of major data sources working right out of the box; others offer only basic functions, but are easy to customise with scripts. Whichever type of SIEM you choose, be sure to understand how much of the functionality you need is either built-in or easy to acquire, and how much you'll have to develop yourself.

 - **Data Storage**: SIEMs generally require vast quantities of storage, but the exact amount varies greatly according to system architecture and activity to be monitored. Log files listing IDS alerts are relatively sparse, while full packet capture can result in gigabytes of new data per second. SIEMs often manage 100 TB of data or more.

 - **Full-time Maintenance**: Because they interact with so many different systems, SIEMs are inherently complex, so deploying, maintaining, and customising them are expert skills in themselves. If you run a large organisation, be prepared to devote at least one full-time staff member exclusively to such tasks.

 - **User Training**: SOC analysts are generally trained in incident detection, investigation, and response, but they may know how to use the particular tools deployed in your organisation. Be prepared to have each user spend about a week training to learn to use the SIEM, and expect a temporary decrease in productivity while learning to migrate old habits and workflows to the new system.

### Security Operations Centre (SOC)

 - Why have a Security Operations Centre?
 - Security Operations Centres (SOCs) can vary widely in scope, but most are responsible for **detecting** and **responding** to cyber attacks.
 - Whilst the primary goals of cyber security is to prevent attacks, this is not always possible. The role of a SOC is to limit the damage to an organisation by detecting and responding to cyber attacks that successfully bypass your preventative security controls.
 - Equally, a SOC can include a multitude of security activities, such as vulnerability assessment, compliance activities and system configuration.

### SOC Operating Model

 - Designing an operating model will help you enumerate and understand the components required when building a SOC. It acts as the foundation for the various aspects of your design. By considering the threat you are faced with, and the assets you are monitoring, you will be in a position to design a target operating model (TOM) that is proportional to your requirements.

**Things to consider**

 - It is important that the operating model you develop is proportionate to the threats you face and what you are trying to protect.

### SOC: Threat Profile

 - The capabilities of your SOC should be proportionate to the threat faced by your organisation.
 - This means that the first task should be to define that threat profile.
 - Your threat profile will influence your approach to detecting attacks, and have implications for other SOC functions, such as the skills required by your SOC analysts.

### SOC: Assets

 - It can be very difficult for a SOC to provide the same level of monitoring for an entire IT estate. For this reason, a SOC must understand what the organisation's most critical assets are, and the business context in which they operate:
	 - Understand the system and context.
	 - Threat modelling.
	 - Impact assessment.

### Typical capabilities of a SOC in the context of sophistication and volume of attacks

![[Pasted image 20251230113143.png]]

### SOC Pillars

![[Pasted image 20251230113202.png]]

### SOC Functions

 - **Threat Intelligence (TI)**: This is the function that should provide the SOC with information about current cyber threats to the organisation and IT estate. This typically indicators of compromise (IOCs) and qualitative information about threat actors.
 - **Threat Handling**: This is the function that aims to perform proactive, iterative and human-centric identification of cyber threats that have evaded existing security controls.
 - **Content Development or Analytics**: This is the team that turns actionable threats intelligence into programmatic detection rules within the SOC tools. Which in turn are then used to identify suspicious behaviour from within your systems and services.
 - **Engineering**: This team is typically responsible for the maintenance of the SOC tooling, the technical onboarding of logs (sometimes referred to as plumbing) and ensuring all the systems are running.
 - **Incident Response or Handling**: THis is the team that responds to the security events by investigating the root cause of an event. Their main objective is to determine whether an event should be escalated into a security incident.
 - **Incident Management (IM)**: When an event is confirmed as a security incident the SOC will pass the event to its IM teams (which may be a static team or a dynamic teams that is stood up in response). This team will have a multitude of responsibilities, from communications to technical reactions, all with the goal of reducing the impact and controlling the damage caused by the security incident.

**In addition to these core functions, some organisations may add other functions to the SOC:**

 - **Vulnerability Management**: A SOC that is required to identify and manage vulnerabilities with the estate will require significantly different resources (for example, the expertise and tools to test, patch and evaluate system builds). It will require the SOC to be far more interactive with systems and this comes with greater responsibility. It is important that the additional resources required for this function are captured within the design.
 - **Insider Threat**: A SOC that is required to detect and respond to insider threats will also have a different setup, compared to a SOC geared only towards external threats. They aren't mutually exclusive, but as monitoring employees is a sensitive subject, any capability (specifically toolsets) that performs such a tasks should be segregated. This is because the SOC and its staff, along with other business systems and staff might be subject to security monitoring and investigations in response to security incidents.

### Governance

 - Thought should be given to where the SOC best fits under the organisational structure. Its important to ensure that reporting lines and oversight are appropriate for the work being performed. As part of this the SOC will need to determine which metrics are being reported. Metrics can evolve over time in order to meet the evolving needs of the organisation.
 - Managing the operation of a SOC requires robust governance in order to make sure the SOC is operating legally, complying with regulation, organisational policies and ensuring that the SOC powers are not misused or abused.

### Continual Improvement

Continual improvement is critical to the success of a SOC, because the environment they operate in and the adversaries which they face, are constantly evolving.

These challenges fall into three broad categories:

 - **An ever changing environment** - Your organisation will most likely be constantly evolving, your business might change making you more attractive to attackers. The assets you are trying to protect might change leading to gaps in your monitoring capability. If you incorporate review cycles into your SOC processes, you should be able to stay on top of this.
 - **Changing threat landscape** - Attackers continually update their methods and motivations may change. This is where **Threat Intelligence** comes into play.
 - **Maintaining detection effectiveness** - All detection approaches require a SOC to build and maintain it's detection methods in order to remain effective. This includes building new security logic and investing in the continues development of your analysts.

### SOC Security

