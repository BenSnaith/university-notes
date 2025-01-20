### Outline

- Systems Analysis.
- UML Sequence and Communication Diagrams.
- Practical work based on case study.

### What is Systems Analysis?

- **Systems Analysis** is being conducted when we draft technical solutions to out requirements
- The deliverable is not yet implementable, but very close to be.
- Overlaps with Domain Analysis, but is more technical and definitely a synthesis activity.

### The Big Picture

- Domain Analysis feeds Systems Analysis with information.
- Systems Analysis delivers a more technical solution to meet the requirements.
- i.e. detailed models of the system, modelling of internal mechanisms, etc.

![[Pasted image 20241128200508.png]]

### The role of the Systems Analyst

- The object-oriented **Systems Analyst** (SA) role is to:
	- Research problems and determine requirements.
	- Plan technical solutions for an enhanced or new system.
		- **Derive an outline object design from the requirements**
		- **The design realises all use cases via actor-object and object-object collaboration**
		- **Objects of the design have a specific responsibility that can be implemented**
- The business process and their use cases to a comprehensive model of the system's objects, behaviours and interfaces.

### Object-oriented Systems Analysis

- Software-based object-oriented modelling was first introduces to simulate real-world entities
- **Real-world entities:** software objects representing the entities (e.g. employees, students, orders, goods).
- **Attributes of entities:** object fields (e.g. employee names).
- **Behaviours:**
	- **Autonomous behaviours:** object's own thread executes object's private methods
	- **Object interactions:** signals sent between objects.
- The essence of OO models: **objects** interact by passing **messages** to each other.

### UML Sequence Diagrams

- **UML Sequence Diagrams** provides the necessary notation to draw objects and sequences of interactions between them.
- It is a two-dimensional diagram: objects are arranged along the top of the diagram, and the interactions are listed underneath in time order going down the page.
- Using analysis, they help us tie together the sequences in use case descriptions
- Notation for three types of objects available.

![[Pasted image 20241202183850.png]]

### Objects in Sequence Diagrams

- Boundary Objects
	- Facilitate interactions with the outside world (usually a UI, and API of some sort).
	- Manage the dialogue between an actor and the system.
	- Do not store any data, but may wrap it appropriately.
	- At least one is always present in a sequence diagram.
- Entity Objects
	- Model a store or persistence mechanism that captures information (data) in the system.
- Control Object
	- Realise use cases and organise complex behaviours
	- Interact with boundary objects to send/receive input/output and interact with actors.

### Notation of Objects in Sequence Diagrams

![[Pasted image 20241202184705.png]]

### UML Sequence Diagram: Activation Bar

![[Pasted image 20241202185014.png]]

- **Activation bars** include that the object is active (i.e. is doing something).
- Can be omitted as they can clutter up the diagram.

### UML Sequence Diagram: Messages

![[Pasted image 20241202185312.png]]

- **Nested messages** are allowed.
- Difference types of messages can be shown.
- **Synchronous messages**: caller waits until the receiver finishes and returns.
- **Asynchronous messages**: "fire and forget"

![[Pasted image 20241202185438.png]]

### The humanoid scenario

![[Pasted image 20241202185605.png]]

- Reaching & grasping capabilities already developed.
- The reaching space is limited (no torso contribution).
- *icub*: the main robot's controller's object
- _leftHand/rightHand_: arm controllers that reach and grasp

### UML Sequence Diagrams: Alternatives

- **Alternative fragments** show a choice of behaviour in a workflow. A guard is used to evaluate a choice. Only one of the options is executed.

![[Pasted image 20241202185914.png]]

### UML Sequence Diagram: Optionals

- **Optional fragments** are only executed when their condition is true.

![[Pasted image 20241202190031.png]]

### UML Sequence Diagram: Loops

- **Loop fragments** illustrate repetitive sequences.

![[Pasted image 20241202190120.png]]

- Fragments can be combined to communicate the appropriate models.

### UML Sequence Diagram: Reflexive Messages

- **Reflexive** calls allow an object to send messages to itself.

![[Pasted image 20241202190254.png]]

### Deriving Objects from User Cases

Process:
- For each use case:
	1. Pick a few representative scenarios, i.e. primary, alternative and exception paths.
	2. Express each scenario/path as a sequence diagram, identifying participating objects and their interactions.
	3. Rework the sequence diagrams as communication diagrams
	4. Combine all communication diagrams to derive a outline/overview class diagram.

### Starting from the Use Case Description

- Consider the following use case's primary path:
	1. The sales operative takes the customer number and enters it on the screen.
	2. The customer details are retrieved and displayed on the screen.
	3. The sales operative checks that the customer details march those given by the customer, and ticks a confirm box.
	4. The sales operative enters the order details.
	5. The sales operative enters the delivery details.
	6. The sales operative requests that the order is created.

### Determine Actors and Objects

**Actors**: SalesOperative
**Boundary Objects**: Screen (to display details)
**Entity Objects**: Customer, Order, Delivery
**Control Object**: OrderCreator

### Deriving a Sequence Diagram

Process:
- Draw a lifeline on the left of the initiating actor.
- Draw next to it lifeline(s) for the actor's boundary object(s).
- Draw (generously spaced) interactions between actors and the boundary object(s).
- For each boundary object interaction determine whether there is a need to involve another object.
	- If the interaction is about a single entity object, create it.
	- If the system needs to perform an action that involves more than one entity object, consider creating a control object to manage the action.

### Resulting Sequence Diagram

![[Pasted image 20241226135247.png]]

### Sequence Diagram to Communication Diagrams

- __UML Communication diagrams__ are another way of interrelating objects in sequence diagrams.
- Numbering interactions in sequence diagrams translates them easier to communication diagrams.
- Easier to derive class from communication diagrams.

![[Pasted image 20241226140413.png]]

### Communication Diagrams to Class Diagrams

- Knowing the objects, one can derive a UML class diagram and add further details such as attributes, associations and multiplicities.
- Note that some of these details may need clarification with the business analysts/stakeholders.

![[Pasted image 20241226140613.png]]

### Finishing by Aggregating all Models

- The process of taking your design from use case and use case descriptions, to sequence diagrams, to communication diagrams and ultimately to class diagrams is iterative.
- At the end, we try to aggregate all the generated models into one outline class models of the software system.
- Nothing stops you from using other UML diagrams to generate your models. e.g. State Machine Diagrams are often used in Systems Analysis to model __Actor__ -- GUI interaction.
