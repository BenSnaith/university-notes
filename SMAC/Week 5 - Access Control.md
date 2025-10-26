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