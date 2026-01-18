NISTIR 7298 defines access control as:

*"The process of granting or denying specific requests to: (1) obtain and use information and related information processing services; and (2) enter specific physical facilities"*

RFC 4949 defines access control as:

*"A process by which use of system resources is regulated according to a security policy and is permitted only by authorised entities (users, programs, processes, or other systems) according to that policy"*

## Access Control Principles

 - In a broad sense, all of computer security is concerned with access control.
 - RFC 4949 defines computer security as:

*"Measures that implement and assure security services in a computer system, particularly those that assure access control service"*

![[Pasted image 20251025152847.png]]

## Access Control Policies

 - Discretionary Access Control (DAC)
	 - Controls access based on the identity of the requestor and access rules (authorisations) stating what requestors are (or are not) allowed to do.
 - Role-based Access Control (RBAC)
	 - Controls access based on the roles that users have within the system and on rules stating what accesses are allowed to users in given roles.
 - Mandatory Access Control (MAC)
	 - Controls access based on comparing security labels with security clearances.
 - Attribute-based Access Control (ABAC)
	 - Controls access based on attributes of the user, the resource to be accessed, and current environmental conditions.

## Subjects, Objects, and Access Rights

 - **Subject**: An entity capable of accessing objects.
	 - Three classes:
		 - Owner
		 - Group
		 - World
 - **Object**: A resource to which access is controlled
	 - Entity used to contain and/or receive information
 - **Access Right**
	 - Describes the way in which a subject may access an object
		 - Could include:
			 - Read
			 - Write
			 - Execute
			 - Delete
			 - Create
			 - Search

## Discretionary Access Control (DAC)

- Scheme in which an entity may be granted access rights that permit the entity, by its own violation, to enable another entity to access some resource.
- Often provided using an access matrix.
	- One dimension consists of identified subjects that may attempt data access to the resources.
	- The other dimensions lists the objects that may be accessed.
- Each entry in the matrix indicates the access rights of a particular subject for a particular object

![[Pasted image 20251025153641.png]]

![[Pasted image 20251025153704.png]]

![[Pasted image 20251025153739.png]]

![[Pasted image 20251025153758.png]]

![[Pasted image 20251025153816.png]]

## Protection Domains

 - Set of objects together with access rights to those objects.
 - More flexibility when associating capabilities with protection domains.
 - In terms of the access matrix, a row defines a protection domain.
 - Users can spawn processes with a subset of the access rights of the user.
 - Association between a process and a domain can be static or dynamic.
 - In user mode certain areas of memory are protected from use and certain instructions may not be executed.
 - In kernel privileged instructions may be executed and protected areas of memory may be accessed.

## UNIX File Access Control

 - **UNIX files are administered using inodes (index nodes)**
	 - Control structures with key informaiton needed for particular file.
	 - Several file names may be associated with a single inode.
	 - An active inode is associated with exactly one file.
	 - File attributes, permissions and control information are sorted in the inode.
	 - On the disk there is an inode table, or inode list, that contains the inodes of all the files in the file system.
	 - When a file is opened its inode is brought into main memory and stored in a memory resident inode table.
 - **Directories are structured in a hierarchical tree**
	 - May contain files and/or other directories.
	 - Contains file names plus pointers to associated inodes.

## Features of UNIX File Access Control

 - Unique user identification number (user ID).
 - Member of primary group identified by a group ID.
 - Belongs to a specific group.
 - 12 protection bits.
	 - Specify read, write, and execute permission for the owner of the file, members of the groups and all other users.
 - The owner ID, group ID, and protection bits are part of the file's inode

## Traditional UNIX File Access Control

 - System temporarily uses rights of the file owner/group in addition to the real user's rights when making access control decisions.
 - Enables privileged programs to access files/resources not generally accessible.
 - **Sticky Bit**
	 - When applied to a directory it specifies that only the owner of any file in the directory can rename, move, or delete that file.
 - **Superuser**
	 - Is exempt from usual access control restrictions.
	 - Has system-wide access.

## Access Control Lists (ACLs) in UNIX

 - **Modern UNIX systems support ACLs**
	 - FreeBSD, OpenBSD, Linux, Solaris.
 - **FreeBSD**
	 - `setfacl` command assigns a  list of UNIX user IDs and groups.
	 - Any number of users and groups can be associated with a file.
	 - Read, write, execute protection bits.
	 - A file does not need to have an ACL.
	 - Includes an additional protection bit that indicates whether the file as an extended ACL.
 - **When a process requests access to a file system object two steps are performed**
	 - Step 1 selects the most appropriate ACL.
	 - Step 2 checks if the matching entry contains sufficient permissions.

![[Pasted image 20251028094401.png]]

![[Pasted image 20251028094423.png]]

![[Pasted image 20251028094439.png]]

![[Pasted image 20251028094455.png]]

## Scope RBAC Models

![[Pasted image 20251028094524.png]]

![[Pasted image 20251028094540.png]]

## Constraints - RBAC

- Provide a means of adapting RBAC to the specifics of administrative and security policies of an organisation.
- A defined relationships among roles or a condition related to roles
- Types:

![[Pasted image 20251028094701.png]]

## Attribute-Based Access Control (ABAC)

![[Pasted image 20251028094736.png]]

## ABAC Model: Attributes

![[Pasted image 20251028094801.png]]

## ABAC

 - Distinguishable because it controls access to objects by evaluating rules against the attributes of entities, operations, and the environment relevant to a request.
 - Relies upon the evaluation of attributes of the subject attributes of the object, and a formal relationship of access control rule defining the allowable operations for subject-object attribute combinations in a given environment.
 - Systems are capable of enforcing DAC, RBAC, and MAC concepts.
 - Allows an unlimited number of attributes to be combined to satisfy any access control rule.

![[Pasted image 20251028095206.png]]

![[Pasted image 20251028095226.png]]

## ABAC Policies

A policy is a set of rules and relationships that govern allowable behaviour within an organisation, based on the privileges of subjects and how resources or objects are to be protected under which environment conditions.

Typically written from the perspective of the object that needs protecting and the privileges available to subjects.

Privileges represent the authorised behaviour of a subject and are defined by an authority and embodied in a policy.

Other terms commonly used instead of privileges are: rights, authorisations, and entitlements.

## Identity, Credential, and Access Management (ICAM)

 - A comprehensive approach to managing and implementing digital identities, credentials, and access control.
 - Developed by the U.S. government.
 - Designed to:
	 - Create trusted digital identity representations of individual and nonperson entities (NPEs)
	 - Bind those identities to credentials that may serve as a proxy for the individual of NPE in access transactions
		 - A credential is an object or data structure that authoritatively binds an identity to token possessed and controlled by a subscriber.
	 - Use the credentials to provide authorised access to an agency's resources.

![[Pasted image 20251028100039.png]]

## Identity Management

Concerned with assigning attributes to a digital identity and connecting that digital identity to an individual or NPE.

Goal is to establish a trustworthy digital identity that is independent of a specific application or context.

Most common approach to access control for applications and program sis to create a digital representation of an identity for the specific use of the application or program.

Maintenance and protection of the identity itself treated as secondary to the mission associated with the application.

## Credential Management

 - The management of the life cycle of the credential:
	 - Examples of credentials are smart cards, private/public cryptographic keys, and digital certificates
 - Encompasses five logical components:
	 - An authorised individual sponsors an individual or entity for a credential to establish the need for the credential.
	 - The sponsored individual enrolls for the credential
		 - Process typically consists of identity proofing and the capture of biographic and biometric data.
		 - This step may also involve incorporating authoritative attribute data, maintained by the identity management component.
	 - A credential is produces
		 - Depending on the credential type, production may involve encryption, the use of a digital signature, the production of a smart card or other functions.
	 - The credential is issued to the indivudual or NPE.
	 - A credential must be maintained over its life cycle
		 - Might include revocation, reissurance/replacement, renrollment, expiration, personal idetification number reset, suspension, or reinstatement

## Access Management

 - Deals with the management and control of the ways entities are granted access to resources.
 - Covers both logical and physical access.
 - May be internal to a system or an external element.
 - Purpose is to ensure that the proper identity verification is made when an individual attempts to access a security sensitive building, computer systems, or data.
 - Three support elements are needs for an enterprise-wide access control facility.
	 - Resource management.
	 - Privilege management.
	 - Policy management.

## Three support elements are needed for an enterprise-wide access control facility

 - **Resource management**
	 - Concerned with defining rules for a resource that requires access control.
	 - Rules would include credential requirements and what user attributes, resource attributes, and environment conditions are required for access of a given resource for a given function.
 - **Privilege management**
	 - Concerned with establishing and maintaining the entitlement or privilege attributes that comprise an individual's access profile.
	 - These attributes represent features of an individual that can be used as the basis for determining access decisions to both physical and logical resources.
	 - Privileges are considered attributes that can be linked to a digital identity.
 - **Policy management**
	 - Governs what is allowable and unallowable in an access transaction.

## Identity Federation

 - Term used to describe the technology, standards, policies, and processes that allow an organisation to trust digital identities, identity attributes, and credentials created and issued by another organisation.
 - Addresses two questions:
	 - How do you trust identities of individuals from external organisations who need access to your systems.
	 - How do you vouch for identities of individuals in your organisation when they need to collaborate with external organisations.

![[Pasted image 20251029102935.png]]

## Open Identity Trust Framework

 - **OpenID**
	 - An open standard that allows sers to be authenticated by certain cooperating sites using a third party service.
 - **OIDF**
	 - OpenID Foundation is an international non-profit orgainsation of indivduals and companies committed to enabling, promoting, and protecting OpenID technologies.
 - **ICF**
	 - Information Card Foundation is a non-profity comminity of companies and indivuduals together to evolve the information card ecosystem.
 - **OITF**
	 - Open Identity Trust Framework is a standardised, open specification of a trust framework for identity and attribute exchange, developed jointly by OIDF and ICF.
 - **OIX**
	 - Open Identity Exchange Corporation is an independent, neutral, international provider of certification trust frameworks conforming to the OITF model.
 - **AXN**
	 - Attribute Exchange Network is an online Internet scale gateway for identity service providers and relying parties to efficiently access user asserted, permissioned, and verified online identity attributes in high volumes at affordable costs.

![[Pasted image 20251029104205.png]]

![[Pasted image 20251029104224.png]]

![[Pasted image 20251029104240.png]]

![[Pasted image 20251029104331.png]]