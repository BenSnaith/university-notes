### Unit Objectives

- To distinguish logical vs physical design, and system vs detailed design.
- To recognise some characteristics of trustworthy software.
- To appreciate trade-offs in design.
- What is meant by architecture in information systems development.
- Some approaches to subsystems, including layers, partitions and MVC
- Some communication styles, e.g. peer-to-peer and client-server.

### How is design different from analysis?

- __Analysis__ identifies "what" the system must do.
- __Design__ specifies "how" it will do it.
- In __analysis__, the analyst seeks to __understand__ the organisation, its requirements, and its objectives.
- In __design__, the designer seeks to specify a system that will:
	- fit the organisation
	- meet its requirements adequately, and
	- assist it to meet its objectives.

### Logical and Physical Design

- __Logical Design__ is independent of the implementation language and platform.
	- _e.g., for a UI, types of fields, position in windows, etc._
- __Physical Design__ is constrained by the implementation platform and language.
	- _e.g., layout managers available, etc._
- Separating logical / physical design is useful if the software must be implemented on _different platforms_

### System Design and Detailed Design

- __System design__ deals with the high level `architecture` of the system:
	- e.g., structure of sub-systems, communication between then, and their distribution on processors.
	- We will consider some approaches to subsystems today.
- __Detailed Design__ deals with e.g. inputs, outputs, processes and file/database structures.
	- We will look at detailed design next unit.

### Some Qualities of Good Design

- __Functional:__ the system will perform its required functions.
- __Efficient:__ the system performs those functions efficiently in terms of _time_ and _resources_.
- __Reliable:__ not prone to hardware or software failure, will deliver the functionality when the users want it.
- __Secure:__ protected against errors, attacks and loss of valuable data.
- __Buildable:__ the design is not too complex for the developers to be able to implement it.
- __Maintainable:__ the design intention is clear to a maintenance programmer.
- __Usable:__ provides users with a satisfying experience.
- __Flexible:__ capable of being adapted to new uses, to run in different countries or to be moved to a different platform.

### Prioritising Design Trade-offs

- A designer is often faced with objectives that are mutually _incompatible_
- `Trade-offs` have to be applied to resolve these conflicts.
- _Functionality_, _reliability_ and _security_ are likely to conflict with _economy_.
	- e.g., the number of features in the end-product is constrained by the budget available for the development of the system.
- Priorities in design choice need to be clearly agreed with clients.

### Achieving Measurable Objectives in Design

- Design addresses the issue of _how_ to meet the requirements.
- `Non-functional requirements`, in particular, impact on the design.
- `Measurable objectives` should be formulated for these requirements so that they can be tested.

### Measurable and Verifiable Design Objectives

- In the context of software design, which of the following objectives are _measurable_ and/or _verifiable_
	1. To reduce the invoice errors by one-third within a year.
	2. To process 50% more orders at peak periods.
	3. To improve the quality of feedback to students.

### Trustworthy Software
###### Definition, and some real-world case studies

_Trustworthy-ness_ seeks to address the _quality_ and _robustness_ of software, ensuring that the software "performs as it should when it should and how it should."

### Trustworthy Software Standards
###### Trustworthy Software Foundation Guidance

- The Trustworthy Software Foundation (TSF) summarises five facets of trustworthiness:
	- __Safety:__ Software should operate without causing hard to anything or anyone.
	- __Reliability:__ Software should operate correctly.
	- __Availability:__ Software should operate when required.
	- __Resilience:__ Software should recover from errors quickly and completely.
	- __Security:__ Software should remain protected against the hazards posed by malware, hackers or accidental misuse.

### Architecture

- Defines structure and behaviour
	- What are the core components, and how do they interact with each other.
- Balances stakeholders' needs which may conflict.
- Has a particular scope:
	- _e.g., enterprise, system, software_
	- _more on this distinction next week_
	- _for today we will look ahead at subsystems_

### Subsystems

- A __Subsystem__ typically groups together system elements with some _common properties_
- _Advantages:_
	- it produces _smaller units_ of development in a system which may be complex.
	- It helps to _maximise reuse_, _maintainability and portability_ at the component level.

### Layering and Partitioning

- Two general approaches to divide a system into subsystems.
	- __Layering:__ different subsystems usually represent different _levels of abstraction_.
	- __Partitioning:__ usually means that each subsystem focuses on a different aspect of functionality.
- The approaches are often used together on one system.

### Layering and Partitioning

![[Pasted image 20241212144246.png]]

### Tiered Architecture
###### Layered Architectures vs. Tiered Architectures.

- A __layered architecture__ - _logical_ structuring:
	- groups functionality / code based on its level of abstraction.
	- All layers may reside on the _same_ computer.
- A __tiered architecture__ - _physical_ structuring:
	- concerns the logical grouping of functionality / code, BUT
	- Tiers reside on, and are executed by, _different computers._

###### Three-tier Architecture

![[Pasted image 20241212144613.png]]

### Partitioning
###### Partitioned Subsystems

![[Pasted image 20241212144653.png]]

### But...
###### An issue with some architectures

![[Pasted image 20241212144741.png]]

### Model-View-Controller (MVC)

![[Pasted image 20241212144831.png]]

- __Model:__ The model represents _data_ and the rules that govern access to and updates of this data.
- __View:__ The view _renders_ the contents of a model and must update its presentation as needed. The view may _register_ itself with the model for change notifications, or may _call_ the model to retrieve the most current data.
- __Controller:__ The controller _translates_ the user's interactions with the view into actions that the model will perform. In a stand-alone GUI client, user interactions could be button clicks or menu selections, whereas in an enterprise web application, they appear as `GET` and `POST` HTTP requests.

![[Pasted image 20241212145211.png]]

- __CalcMVC:__
	- is the _top-level_ class.
	- responsible for _creating_ the `model`, `view` and `controller` objects.
- __CalcModel:__
	- does _not know_ about the `view` nor the `controller`.
	- _fires_ property change notifications to its subscribers, in this case, the `view`.
- __CalcView:__
	- _renders_ data from the `model` using a GUI
	- _subscribes_ to the property change notifications from the `model`.
	- _passes_ user input events to its subscribers.
- __CalcController__:
	- _subscribes_ to all user input events.
	- _defines_ the event handlers for GUI events.
	- _calls_ the `model` to change its state based on the user event.

### CalcMVC Example

```java
import javax.swing.*;

public class CalcMVC {
	//... Create Model, View, and Controller.
	public static void main(String[] args) {
		CalcModel model = new CalcModel();
		CalcView view = new CalcView(model);
		CalcController controller = new CalcController(model, view);

		view.setVisible(true);
	}
}
```

### Model-View-Controller (MVC)
###### Single Model, Multiple Views.

![[Pasted image 20241212150325.png]]

- The MVC Architecture is _flexible_.
- _Multiple_ views can be created in the MVC architecture.
- Changes made to the model within one view is _reflected immediately_ to all views which use the same model.

```java
import javax.swing.*;

public class CalcMVC {
	public static void main(String[] args) {
		CalcModel model = new CalcModel();
		CalcView view1 = new CalcView(model);
		CalcController controller1 = new CalcController(model, view1);
		CalcView view2 = new CalcView(model);
		CalcController controller2 = new CalcController(model, view2);
	
		view1.setVisible(true);
		view2.setVisible(true);
	}
}
```

### Architecture Continued

- Relationship between architecture and design.
- Enterprise, System and Software Architecture.
- Communication between subsystems
	- Examples: Peer-to-peer, Client-server
- Service-Oriented Architecture (SOA)

### Relationship between Architecture and Design

![[Pasted image 20241212151048.png]]

### Enterprise Architecture

- `Enterprise architecture` concerns:
	- Modelling the way the _enterprise_ conducts business.
	- Modelling _information systems_ to support those operations.
- _Typical Questions_:
	- How does the system overlap / interface with other systems in the organisations?
	- Will the system help the organisation to achieve its goals?
	- Is the cost of the system justified?

### System Architecture

- Describes the hardware and software elements and interactions between them.

`System Architects`:

- Address the _big picture_.
- Ensure that the required _qualities_ of the system are accounted for in the design.
- Ensure the required features are provided at the right cost.

### Software Architecture

- "A software architecture describes the overall components of an application and how they related to each other. Its design goals, include sufficiency, understandability, modularity, high cohesion, low coupling, robustness, flexibility, reusability, efficiency, and reliability" - Braude and Bernstein (2011)

###### Architecture != Framework

- The terms _architecture_ and _framework_ have sometimes been used interchangeably, but that is _inappropriate_.
- "A __framework__, or library, is a collection of software artifacts that can be used by different applications"
	- e.g., Laravel, Django, React, Ruby on Rails

### Subsystem Communication Styles

- Each `subsystem` provides services of other subsystems.
- We will look at two different styles of _communication_ that make this possible: _client-server_ and _peer-to-peer_ communication.

![[Pasted image 20241212153526.png]]

### Subsystem Communications

###### Client-Server

- _Client-server_ communication requires the `client` to know the interface of the `server` subsystem.
	- The communication is only in one direction.
- The `client` subsystem requests _services_ from the server subsystem and not vice versa.
	- The `client` plays the role of a consumer; while the `server` is considered to be the supplier
- Examples of client-server communication can be found in most _network-based applications._
	- e.g., email systems and most web applications.

###### Peer-to-peer

- _Peer-to-peer (P2P)_ communication requires each system to know the interface of the other, thus _coupling_ them more _tightly_.
- Each peer has to run exactly the _same program_ and hence all peers provide _identical services_.
- _Peer-to-peer_ communications is _two way_ since either peer subsystem may request services from the other.
- How to find the peer with the information you need?
	- _Centralised Model_ (used by Napster)
	- _Flooding_ (used by Gnutella)
	- _Distributed Hash Table_ (e.g. Kademlia, Chord)

### P2P: How to find which peer hold the required information?

__Using a centralised model...__ One point of failure.

![[Pasted image 20241212154459.png]]

__By means of flooding...__ Robust, but requires many numbers of messages  per lookup.

![[Pasted image 20241212154557.png]]

__Using Distributed Hash Table...__ The key-value index is itself distributed, meaning there is some redundancy and fault tolerance.

![[Pasted image 20241212154854.png]]

### Subsystem Communications

- Torrent file sharing systems use a _distributed hash table_ to facilitate storing and retrieval of large files.
- _... a key-value store distributed across a number of nodes in a network_
	- Each peer knows which portions of files it keeps and also where to look for other chunks for other keeps.
- (By contrast, in a blockchain, each node of the network usually stores the full ledger of transactions)

### Service Oriented Architecture (SOA)

- Large _distributed_ systems may adopt __Service Oriented Architecture (SOA)__ in their design.
- The basic unit of communication in SOA is the invocation of _remove services_.
- A __service__ typically refers to a __Web service__, which:
	- communicates via Internet Protocols (e.g., __HTTP__) and
	- sends and receives structured data, e.g., in __XML__ or __JSON__ format.
- In a SOA, _services_ interact via a common communications protocol.
	- The resulting system components are _loosely coupled_ with each other.

###### A Holiday Booking Scenario

- An example of a SOA system is a network of __Web Services__ comprising and supporting _travel agents_.
- This system is composed of _services_ for booking flights, hotels and car hire.
- Agent applications use these _services_ to assemble more sophisticated holiday-package services for their clients.

![[Pasted image 20241212161541.png]]

- Each bubble is a _service_ provided by potentially a _different_ vendor.
- A _service_ tends to use another service in order to complete its task.
- It should be easy to switch between the services of the same kind provided by a different vendor.

![[Pasted image 20241212161704.png]]

- Reusable logic is divided into services.
- Services share a formal contract.
	- _mainly regarding information exchange_.
- Services are _loosely coupled_.
- Services _abstract_ underlying logic.
	- _The only part of a service that is visible to the outside world is what is exposed via the service's description._
- Services are _composable_.
	- _i.e., a service can be made up of other services._

### Why SOA

Business use of SOA is justified by a promise of:
- __Easier reuse__ of services for multiple purposes
- __Better adaptability__ to changing business environment and available technologies
- Ability to integrate new and _legacy systems_.
- Ability to _cheaply_ setup e-business links across the world.