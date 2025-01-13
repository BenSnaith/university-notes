# Unit 1 - Systems
## Unit Overview

- Why Software Engineering
- Systems and Modelling
- UML Component Diagram.

## Units

1. Modelling and Systems
2. Development Process
3. Requirement Engineering
4. Business Analysis
5. OO Systems Analysis
6. Testing
7. Software Design
8. Architecture
9. OO Detailed Design
10. Design Patterns.
11. Implementation.
12. Refactoring.

## Motivation: Why Software Engineering?

- Software Engineering (SE) refers to the systematic procedures used for the analysis, design, implementation and maintenance of software.
- The term became commonly known in 1968 as the tile for NATO’s conference to discuss software issues, guidelines, best practices, etc.
- Coined by NASA’s scientist Margaret Hamilton earlier in the 60’s.
- SE’s aim is to solve the Software Crisis.
    - Failures due to increasing demands and low expectations.

## Importance of Software Engineering

Software and engineering sets apart a hobbyist programmer from a professional software developer.

- It is the standardised, structured and thorough approach to writing code.
- Treats the while development process from start to finish in a formalised manner.
- It allows us to deliver programs that meet a certain level of rigour (i.e. it is correct, efficient and secure).

## Systems Thinking

Systems thinking is the holistic approach to solving problems that focuses on how a system’s components interrelate and change over time, within the context of the overall missions that the system is designed to accomplish.

## System Characteristics

Systems have the following characteristics:

- Central Objective
    
    All components work together to achieve a common goal.
    
- Integration
    
    Components are put together to complete a system.
    
- Interaction
    
    The system works as a result of components interacting with each other.
    
- Interdependence
    
    A change to one component will affect other components.
    
- Organisation (hierarchical)
    
    The right components in the right place, in the right time.
    

## Expected Components in a System.

Systems have the following types of components:

- Input, processes and output.
- Environment: Internal and External.
- Boundary
- Interface
- Feedback and Control

## Hierarchy in Systems

- Complex systems are comprised of various subsystems
- Subsystems are arranged in hierarchies and are integrated to achieve the common goal.
- Subsystems have their own boundaries, thus interfaces and environment.

## Systems and External Environments

- Users and/or other systems interact with a system via interface components.
- The external (operational) environment affects the functioning of a system.
- A system’s function may be to change its environment.
- External environment can be both physical and organisational.

## Emergent Properties (or Behaviours)

The complex relationships between the components in a system mean that a system is more than simply the sum of its parts.

  

Properties emerge once the system components are integrated.

- Functional emerge when all the parts of a system work together to achieve some objective.
- Non-functional relate to the behaviour of the system in its operation environment.

## System Modelling

The world is full of systems and sets, with the majority of people seeing only the latter.

  

What is required to propose or improve an existing system?

- Use out “component-based vision” to create a system’s model out of a system.
- Model it, no matter how crude the overall insight of it might be.

A system’s model must have the right level of detail define:

- The components that constitute the system.
- The types of relations between those components.
- How the components interrelate into the whole system to perform some function.
- How the whole system interacts with its environment.

## Why are models useful?

Models are useful for:

- Abstraction
    
    Allows the modeller to focus on the most important features of a real-world situation.
    
- Representation
    
    Makes one’s ideas into a more concrete artefact.
    
- Communication
    
    Help sharing ideas and thoughts that are difficult to put into words.
    
- Easy Evaluation
    
    No runtime failures, check if requirements are met.
    

## Examples of Models

![[Untitled 15.png|Untitled 15.png]]

## Models over Modelled Systems

Advantages of a model over the modelled system:

- A model is quicker and cheaper to build.
- One can choose which details to include or omit in a model — easier to analyse.
- Some models can be used in simulated environments — cheaper and safer options.
- Models evolve (no need to be perfect) and in some cases they do no even need to make sense.

## Models in Software Engineering

- Software is an abstract entity — its models will be abstract too!
- Program code = detailed model?
- Models of software focus on certain aspects:
    - Code organisation.
    - Runtime entities and their responsibilities.
    - Overall data flow.
    - Messages among entities.
- Unified Modelling Languages (UML) provides all the tools necessary to produce models.

## UML Component Diagrams - Notation \#1

Component diagrams help us plan out the high-level pieces of a system to establish the architecture and manage complexity and dependencies amongst components.

![[Untitled 1 5.png|Untitled 1 5.png]]

## UML Component Diagram - Notation \#2

Two common ways to depict how components work together.

![[Untitled 2 5.png|Untitled 2 5.png]]

## UML Component Diagrams - Notation \#3

Ports are used to depict points of interaction between a component and the outside world.

![[Untitled 3 4.png|Untitled 3 4.png]]

## UML Component Diagrams - Notation \#4

One can depict the internal structure of a component and use delegation connectors to show the direction of traffic:

![[Untitled 4 4.png|Untitled 4 4.png]]

## Useful Notation for Component Diagrams: The Circuit Example

# Unit 2 - Software Lifetimes

## Unit Overview

- Software Development Lifecycle Processes.
- UML Activity Diagrams

## Software Development Lifecycle

- Software Development Lifecycle (SDLC) or software development process / methodology is a sequence of project phases we can follow in order to create a software application.
- Several models and frameworks from the early 60’s until the ones that we still use today.
- SDLC = Activities required to develop software AND an approach to linking them together in a work flow.

## Motivation — Progression of Activities

- There is a need for a logical progression of activities when developing software (not necessarily a time progression).

![[image 14.png|image 14.png]]

## Details of Lifecycles Phases

- **Domain Analysis**: study what is already there, literature review, conversations with experts, etc.
- **Specification (Requirements Engineering)**: feasibility study, user requirements, elicitation and analysis (input from stakeholders), systems analysis, etc.
- **Design**: model software structures, software prototypes, interface specifications, competent models, etc.
- **Implementation**: source code, database, interfaces, data models, deployment plan, etc.
- **Validation**: component testing (unit testing, module testing), integration testing (sub-systems and system testing), user testing (acceptance testing), etc.
- **Deployment**: deployed system, user manuals, training, documentation, training staff, fault report, etc.

## The Waterfall Process

- The simplest way of organising the development — very rarely used these days.
- Large documents and collections of models created at most stages.
- In the classical model there is no turning back (some modern variants allow backtracking)

![[image 1 3.png|image 1 3.png]]

## Cyclic: Iterative / Incremental

- Cyclically repeating (a subset of) waterfall activities
- A cycle adds a feature or makes improvements.
- Typically cycles are 1-4 weeks short.
- You can, if needed, deploy stakeholders ideas.

![[image 2 3.png|image 2 3.png]]

## Incremental vs Iterative

- **Incremental**: adding new features in each version
- **Iterative**: making improvements with each cycle.

![[image 3 3.png|image 3 3.png]]

## Unified Process

- The Unified Process is iterative:
    - Inception Phase
        
        project scope, communication with stakeholders, goals, planning, costs → vision document, use case models, etc.
        
    - Elaboration Phase
        
        analysing problem domain, eliminating all major risks, refining plan → actors identified, clarifying requirements, etc.
        
    - Construction Phase
        
        delivering the “beta” version, meeting all stakeholders’ needs, testing → a working product ready to be deployed, test results, documentation, etc.
        
    - Transition Phase
        
        deployment and maintenance of the system, bug reports, training users → project completed and in use, debriefing.
        

## Unified Process Lifecycle Illustrated

- Performing SDLC activities to different extent:

![[image 4 3.png|image 4 3.png]]

## Agile

- Agile is an approach to software development
- Also, a movement, a mindset.

“We do not act rightly because we have virtue or excellence, but rather we have those because we have acted rightly. We are what we repeatedly do. Excellence, then, is not an act but a habit.

— Aristotle, Nicomachean Ethics

- Agile was another answer to software crisis in the ‘70s

## The Agile Manifesto

“We are uncovering better ways of developing software by doing it and helping others do it.

Through this work we have come to value:

  

Individuals and interactions over processes and tools

Working with software over comprehensive documentation

Customer collaboration over contract negotiation

Responding to change over following a plan

  

This is, while there is value in terms on the right, we value the items on the left more.”

## Agile Processes and Principles

- Face-to-face communication among team and customers.
- Customer representative always available.
- Software developed in quick iterations and tested continuously.
- Good quality, well documented code.
- No long-term planning, but setting long-term goals and visions.
- Simple design to meet personal needs, refactor due to changes.

Scrum adds:

- Communication via several types of regular meetings.
- Stakeholders have to trust developers.
- Prioritisation of features via backlogs (i.e. todo lists).

eXtreme Programming adds:

- Pair programming.
- Sustainable pace, no overtime.
- Shared systems metaphor.
- Shared code ownership - anyone can edit.

## The Scrum

- Roots in a 1986 paper by Takeuchi and Nonaka, “The new new product development game”.
- Developed in 1990, formalised by Sutherland and Schwaber in 1995.
- def Scrum(n): A framework within which people can address complex adaptive problems, while productivity and creatively delivering products of the highest possible value.

## Scrum Pillars and Values

**Pillars**

- **Transparency**: everybody involved in delivering the project should understand what is expected and how the process works.
- **Inspection**: review the progress at regular intervals.
- **Adaptation**: change a process if it is not working, or is not delivering a sensible result.

**Values**

- Pillars come to life and build trust for everyone only when commitment, courage, focus openness and respect are embodied and lived by the team.

## Scrum Roles and Events

Roles

- The **Product Owner** is responsible for maximising the value of the product and work of the Development Team.
- The **Development Team** is equipped with all necessary skills to successfully deliver the product.
- The **Scrum Master** supports for the Product Owner, the Development Team.

Events

- **Sprint**: time-box to produce a “done” product increment.
- **Spring Planning, Daily Scrum, Spring Review, Spring Retrospective.**

![[image 5 3.png|image 5 3.png]]

## UML Activity Diagrams

Activity Diagrams show high-level actions chained together to represent a business process occurring in our system.

![[image 6 2.png|image 6 2.png]]

An action starts when it receives a control token.

Diamonds are used to depict decision or merge nodes.

![[image 7 2.png|image 7 2.png]]

Multiple actions that run in parallel are depicted using forks and joins.

A flow is broken up into two or more simultaneous flows. All incoming actions must finish before the flow must proceed past the join.

![[image 8 2.png|image 8 2.png]]

When time is a factor in an activity, time events are used to model a waiting period.

![[image 9 2.png|image 9 2.png]]

When an activity interacts with an external actor or process, messages are send and received. These are called signals.

A receive signal wake up for action, whereas a send signal is a message to the external participant.

![[image 10 2.png|image 10 2.png]]

More on signals:

- When send an receive signals are combined, a synchronous flow is depicted.
- If only a send signal is depicted, the flow is asynchronous (does not wait for a response to proceed).
- A receive signal can replace a starting node.

![[image 11 2.png|image 11 2.png]]

Interruptions are receive signals that cause activities to stop following their “expected” flows. A lightning bolt symbol is used to depict an interruption.

Interruptible regions show the area in which an interruption is expected to occur.

![[image 12 2.png|image 12 2.png]]

Objects can be depicted either by using object nodes or pins.

Input pins represent input objects, i.e. an action cannot run without an object parameter. Output pins specify that an object is output from an action.

![[image 13 2.png|image 13 2.png]]

Swim lanes or partitions are used to depict which component or participant is responsible for which actions.

# Unit 3
## Unit Objective

- Requirements Engineering.
    - Feasibility study, Elicitation and Analysis of Requirements, Requirements Specification, etc.
- Use Case Descriptions and UML Use Case diagrams.

## Requirements Engineering

- The requirements for a system are the descriptions of what the system should do, the services that it provides and the constraints on its operation.
- The process of finding out, analysing, documenting and checking these services and constraints is called requirements engineering (RE)
- The term requirement is used inconsistently in the literature.
    - User requirements: statements plus diagrams of system services and any associated constraints.
    - System requirement: detailed descriptions of system’s functions, services and operational constrains.
    - Domain and software requirements (will be soon discussed).

## Examples of User and System Requirements

- User Requirement Definition:
    1. The LocalCare system shall generate monthly management reports showing the cost of drugs prescribed by each clinic during that month
- System Requirement Specification:
    1. On the last working day of each month, a summary of the drugs prescribed their cost, and the prescribing clinics shall be generated.
    2. The system shall automatically generate the report for printing after 17.30 on the last working day of the month.
    3. A report shall be created for each clinic and shall list the individual drug names, the total number of prescriptions, the number of doses prescribed, the the total cost of the prescribed drugs.
    4. If drugs are available in different dose units separate reports shall be created for each dose unit.
    5. Access to all cost reports shall be restricted to authorized users listed on a managements access control list.

## Types of Requirements

- Functional Requirements (FR):
    - Statements of services a system should provide.
    - How the system should react to particular input.
    - How the system should behave in particular situations.
    - In some cases, a functional requirement may explicitly state what the system should NOT do.
- Non-Functional Requirements (NFR):
    - Constraints on services or functions offered by the system.
    - Timing constraints, development-related, imposed by standards, etc.

## Functional Requirements

- Describe what the system should do.
- Depend on the type of software and expected users.
- User requirements are described in an abstract way to be understood by system users.
- System requirements are more detailed (input/output, exceptions, etc).
- FRs are written in a functional requirements specification document, which needs to be both complete and consistent.

## Non-Functional Requirements

- Often more critical than functional requirements.
- Types of non-functional requirements:

![[image 15.png|image 15.png]]

## Measuring Non-Functional Requirements

- Non-functional requirements must be testable, written quantitatively so that they can be objectively tested.
- Rewriting NFR:
    
    ![[image 1 4.png|image 1 4.png]]
    
- Metrics for specifying NFR:

![[image 2 4.png|image 2 4.png]]

## The Software Requirements Document

- Official statement of what software developers should implement.
- Covers both user and system requirements. FR and NFR.
- A thick document that has a diverse set of readers.

## How to conduct Requirements Engineering

- A spiral view of the requirement engineering iterative:

![[image 3 4.png|image 3 4.png]]

## Feasibility Study

- Feasibility Study is a short, focused study that assesses if the system is useful to the business.
- Should answer the following questions:
    - Does the system contribute to the overall objectives of the organisation?
    - Can the system be implemented within schedule and budget using current technology?
    - Can the system be integrated with other systems that are used?

## Requirements Elicitation and Analysis

- Software engineers work closely with stakeholders to elicit and analyse requirements
- **Discovery**: applying several techniques to interact with stakeholders and find out about domain, user and system requirements
- **Classification and Organisation**: grouping related requirements, making coherent clusters and associate them with sub-systems of the architecture.
- **Prioritisation and Negotiation**: ordering requirements and resolving conflicts.
- **Specification**: validating and formally documenting requirements.

## Elicitation Challenges

- Stakeholder often do not know what they want/need.
- Requirements are often expressed in the stakeholders own terms, and with implicit knowledge of their work.
- Different stakeholders have different requirements → conflicts.
- Political factors may influence the requirements of the system (e.g. managers may demand specific requirements to increase their own influence in the organisation)
- The importance of each requirement may change with the economic and business environment
- New stakeholders will come with a new set of requirements.

## Requirements Discovery

Several techniques, depending on the stakeholders:

- **Brainstorming**: creating new ideas - requires voting methods.
- **Interviews**: closed or open, formal and informal.
- **Questionnaires**: running short, targeted surveys.
- **Examination of documents / artefacts**: reading current policies and procedures.
- **Scenarios**: running example interaction sessions.
- **Use Cases**: textual or graphical using UML
- **Prototyping**: best in receiving feedback, can be paper, PowerPoint or functional.
- **Ethnography**: watching daily activities and identifying problems that arise.

## An example scenario

- An example scenario — template may vary.

![[image 4 4.png|image 4 4.png]]

## Scenarios with multiple workflows

- A scenario is a sequence of events and/or actions that are initiated by an actor.
- Starts with assumptions (pre-conditions), and finished with a description of the system’s state (post-conditions)
- It has workflows, i.e. paths within the scenario with a common goal usually structured as follows:
    - Primary path: most common.
    - Alternative path(s): less common way to the goal.
    - Exception path(s): aiming for the goal but miss it.
- 80/20 rule applies: you’ll spend 80% of your time dealing with what will happen 20% of the time (alternative paths).

The tea making process: teapot vs. cup.

Primary path:

1. Fill kettle
2. Switch kettle on
3. Put tea in teapot
4. Pour boiling water
5. Wait for two minutes
6. Pour team into cup
7. Add milk and sugar

Alternative path:

1. Fill kettle
2. Switch kettle on
3. Put teabag in cup
4. Pour boiling water
5. Wait for two minutes
6. Add milk and sugar

Exception path:

1. Fill kettle
2. Switch kettle on
3. Kettle explodes
4. Stop the fire

## Use Cases and Use Case Descriptions

- A use case is a piece of functionality, presented within a scenario and performed by the system that can be described by a short name.
- Each use case is associated with its initiator(s) and a use case description.
- Its name should describe the functionality from the initiator’s point of view.
- We use UML Use Case diagrams to depict use cases.

## UML Use Case Diagrams

- Actors are drawn as stick men (human actors) or stereotyped boxes (external systems).

[](https://www.notion.soundefined)

## Relationships in UML Use Case Diagrams

- The `<<include>>` relationship:
    
    R1.1: The content management system that shall allows an administration to create a new blog account, provided the personal details of the applying author are verified using the Author Credentials Database.

- `<<Extend>>` in this context means optionally including, i.e. A may or may not include B.

## Requirements Classification & Organisation

- Group related requirements
- Give them numbers so they are traceable, e.g. FR1, FR2, NFR1, etc.
- Decompose the system into sub-systems and components of related requirements.
- Defined relationships between these components.
- Identify which design patterns to employ.

## Requirements Prioritisation

- **MoSCoW**: Must, Should, Could and Would (or Won’t, Wish to) have.
- If any of the must requirements is not included, the delivery is considered a failure.
- Should requirements are important but now as time-critical as the must ones.
- Requirements related to improving user experience are often classified as could.
- Won’t requirements are least-critical and can be delivered in the next release

  

- Rank requirements on an ordinal scale, using different numerical values based on importance.
- Ranking can be used with **MoSCoW** or any other similar method/variant.
- e.g. There are multiple must requirements, which one to implement first?

## Requirements Prioritisation with Agile

- XP’s user stories can be used instead of use cases (especially at early stages).
- Cards usually contains a checklist of tests to validate the requirement later.
- Good user stories are INVEST:
    - Independent: can be understood without having to read some other user story.
    - Negotiable: invitation to discuss, not a contract.
    - Valuable: giving useful outcomes to the stakeholders.
    - Estimatable: so we know they are small.
    - Small: fits in one cycle of development.
    - Testable: so it can be declared as “completed”.
- Prioritising user stories using user stories maps.

## Requirements Validation

- Requirements Validation is the process of checking that requirements actually define the system that the customer really wants.
- Types of checks:
    - Validity check: does the system provide the functions which best support the needs of the stakeholders?
    - Consistency check: are there any conflicts to resolve?
    - Completeness: are all functions required by the customers included?
    - Realism: can the requirements be implemented given time and budget?
    - Verifiability check: can the requirements be tested?

## Requirements Validation Techniques

- Ways to conduct requirements validation:
    - Requirements reviews: the requirements are analysed systematically by a team of reviewers who check for errors and inconsistencies.
    - Prototyping: an executable model of the system in question is demonstrated to end-users and customers.
    - Test-case generation: if a test is difficult or impossible to design, the requirements will be difficult to implement.

### Requirements Specification

- Requirements specification is the process of writing down the requirements in the requirements document.
- Almost always written in natural language supplemented by diagrams and tables.
- Useful guidelines:
    - Invent a standard format.
    - Use language consistently to distinguish between mandatory and desirable requirements (e.g. “must/shall”, “should”, etc).
    - Use text highlights (e.g. bold, italic, colour).
    - Avoid jargon, abbreviations and acronyms.

# Unit 4 - Business Analysis
### Outline

- Business / Domain / Context Analysis
- UML Object, Class and State Machine Diagrams

### The Big Picture

- Unit 1: Systems Thinking (systems, components and properties/behaviours), component diagrams
- Unit 2: SDLC (Waterfall, UP, Agile), activity diagrams
- Unit 3: Requirements Engineering, use case diagrams and descriptions
- **Unit 4: Business Analysis, object/class/state machine diagrams.**
- Unit 5: Systems Analysis, sequence/communication diagrams.
- Unit 6: Software Testing

### Analysis vs Synthesis

Analysis:
- An investigation of the components parts of a whole.
- Involves some kind of abstraction, i.e. creating a component model.
Synthesis:
- Creating something real out of abstract models.

### Analysis and Software Engineering

**In Business / Context / Domain Analysis:**
- Analyse existing structures and their processes.

**In Requirements Analysis:**
- Discover and define desirable external behaviour of a new or modified system.

**In Systems Analysis:**
- Elaborate requirements into a more formal specification external behaviour (including user's perception of the internal behaviours).
- In reality, here we do more syntheses than analysis.

### Analysis or Synthesis?

Think about creating an activity diagram during a system's design. Would you call it an analysis or synthesis activity?

- Synthesis

**The activity diagram describes a process that (hopefully!) fulfils a desired requirement. When we draw activity diagrams during system design, we do not model an exist process of the organisation.

### What is Business Analysis?

- **Business Analysis** is the set of tasks and techniques we use when working with stakeholders to understand the structure, policies and operations of an organisation.
- A **Business Analyst (BA)**:
	- Identifies the business problems and opportunities.
	- Elicits the needs and constraints from stakeholders.
	- Analyses the needs and defines requirements.
	- Assesses and validates the potential and actual solution.
- Main focus on business goals and not technology designs.
- BAs to Developers ratio 1/6, but now changing 

### Business Analysis towards requirements

- When describing a business, there are four basic requirements components
	1. Information is data.
	2. Manual or automated activities and procedures the business performs.
	3. People (or systems, or departments) inside and outside the organisation.
	4. Guidelines, constrains and policies under which the organisation operates.
- The Business Analyst breaks requirements down and identifies where the improvements need to be made.

### Conducting Business Analysis

- We have learned about business **scenarios**.
- We have seen **workflows** (primary/alternative paths) in use case descriptions.
- We are familiar with **process models** (activity diagrams).
- We will look at:
	- **Business Process Maps**
	- **Object Models** (class & object diagrams and state machines).

### Business Process Maps

![[Pasted image 20241128181313.png]]

- **A business process** is a logical grouping of events that can be agreed as a fundamental element of the business.
- **A business process map** is a collection of named processes grouped hierarchically on no more than 3 levels.
- A few rules of thumb:
	- The root is the most abstract process.
	- Level 1 should not have more than 10 high-level processes.

![[Pasted image 20241128181432.png]]
- A lower-level process is a specialisation of its parent.

![[Pasted image 20241128181525.png]]
- Braking down to more than 3 levels will render the business process map useless (it has to remain abstract)

### What to avoid in Business Process Maps

- Business Process Maps help us focus on main functionality
	- Provide a top-level view and give scope, clarify terminology, easy to understand for everyone.
- No need to present a perfect breakdown.
- A business process map does not show:
	- The structure of the organisation.
	- Information flow.
	- Time considerations.
	- Interactions among processes.

### Method to produce a Business Process Map

- Usually a half-a-day workshop attended by business managers and experts.
	- All contribute to knowledge, but need to reach an agreement.
- Need for a **facilitator**:
	- Oversees the discussions and forces rules.
	- Aiming for a high-level view and a good but not perfect map (not always achievable)
	- Ensures timing (time-boxed event).

### Identifying Domain Objects

- **Noun-verb analysis**: the first step to **class decomposition**.
	- To break a large problem down into a class structure
- Nouns may represent:
	- Classes.
	- Specialisations (classes that extend Abstract classes).
	- Attributes (i.e. a Student has a name).
	- Data (values to attribute variables/containers/etc).
- Verbs may represent:
	- Services (i.e. methods) provided by a Class.
	- Services used by Classes.

### UML Object and Class Diagrams

- UML Object Diagrams are used to communicate object information (relationships and static view).
- They represent instances of classes and derive from **UML Class Diagrams**
- Object diagrams may or may not contains object attribute values.
- Class diagrams are usually more detailed, include attribute and method information.
- Notation: `myCup : Cup` `myCup` is an instance of `Cup`.

### UML Object Diagrams

![[Pasted image 20241128182849.png]]
- Anonymous object may exist, can you think why?

### Object to Object Relationships

![[Pasted image 20241128183017.png]]

### Relationship Over Classes

![[Pasted image 20241128183051.png]]

### A Detailed Class Diagram

- Class Diagrams can be very detailed
- - (private), + (public), # (protected), / (derived)
- Parameters and return types
- Interface and Abstract classes (realisation and specialisation arrows).

![[Pasted image 20241128192025.png]]

### Object and Class Diagrams - What to remember

Use a UML Object Diagram to:
- Show a static view of an interaction
- Describe object relationships of a system
Use a UML Class Diagram to:
- Better understand the general overview of the schematics of an application.
- Provide an implementation-independent description of types used in a system.

### Object States and State Machine Diagrams

- **State machine diagrams** are used to show how an object's state changes during its lifetime.
- Object State = attribute values.
- Drawing a state machine requires increase of abstraction.

![[Pasted image 20241128193013.png]]

### State Machine Diagrams Notation

- Object states can be a passive quality (on or off) or an active quality, i.e. the object is doing something.

![[Pasted image 20241128193153.png]]

- Objects transition from source states to target states

![[Pasted image 20241128193229.png]]

- A transition syntax: `trigger [guard] / behaviour`

![[Pasted image 20241128193319.png]]

- More than one reasons for a transition.

### Composite States

- UML allows concurrent states to be shown using the composite states notation.
- A non-player game character is in the "Neutral" state, which consists of two substates "searching" and "pacing".

![[Pasted image 20241128193605.png]]

- Even if a substate runs to completion, the composite state is complete when every substate diagram is complete.

### History States

- **History states** are used to remember the state before an interruption happened

![[Pasted image 20241128195450.png]]

### Advanced Pseudostates

- UML notations allow choices, forks and joins to be possible

![[Pasted image 20241128195550.png]]

### State Machine - What to remember

Use a UML state machine to:
- Show event-driven objects in a reactive system.
- Describe how an object moves through various states within its lifetime.

### Summary

Today's learning outcomes:
- We discussed Business Analysis.
	- Discovery, Classification and Organisation, Prioritisation, Specification.

# Unit 5 - Systems Analysis
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

# Unit 6 - Software Testing
### Unit Objectives

- Importance.
- Black-box vs White-box testing.
- Testing Techniques.
- Levels of Testing.
- Testing documentation and planning.
- JUnit examples.
- Test-Driven Development.

### What is Software Testing

- A process to validate a software application.
- Observing, recording and comparing the behaviour (output) of the software with the intended behaviour and output.
- Main purpose of testing is to try __find errors__.
	- Is it always done?

### When to do testing?

- Testing should be done __early__ and __often__.
- No need to wait until all operations of a software component are fully implemented.
- Even a smallest change on a piece of code may __invalidate__ the entire system!
	- Testing should be done __whenever changes have been made__

### Test Data

- __Test data__ should test the software at its limits and test business rules.
- Test data should include:
	- Extreme Values:
			(e.g., Out-of-Bounds)
	- Borderline Values:
			(e.g., -1, 0.9999)
	- Invalid Combinations of Values:
			(e.g., age=3, marital_status=true)
	- Nonsensical Values:
			(e.g., negative order line quantities)
	- Heavy Loads
			(e.g., are performance requirements met?)

### Who should perform testing?

- Ideally, test scripts should be built and executed by __specialist test teams__ who have access to software.
- Testing should also be done by business and systems analysts.
- In eXtreme Programming (XP), programmers are expected to write __test harnesses:__ a software framework that imitates missing infrastructure allowing automated testing.
- Intended users of the system should test against requirements, aka __user acceptance testing__.

### What kind of testing?

- __Black Box Testing__ seeks to establish whether the end-product does what it's meant to.
   
Checking FR, and is usually done by Systems Analysts.

- __White Box Testing__ seeks to establish whether the end-product delivers a good solution, not just a solution to the problem.
  
Checking RF/NFR, and is usually done by the developers.

### Various types of Testing

- __Unit Testing:__ ensures that individual classes work correctly.
- __Interface Testing:__ validates the function exposed by components.
- __Integration Testing:__ establishes whether all components in the system work correctly together.
- __Subsystem Testing:__ checks if each subsystem works correctly and delivers the required functionality.
- __System Testing:__ check if the WHOLE system works seamlessly.
- __Robustness Testing:__ establish the ability of the software application in handling anomalies (being __trustworthy__).
- __Mutation Testing:__ introduce statement/value/decision "mutations" on purpose, to see how the system reacts.
- __Performance Testing:__ check if the system is fast enough and it uses an acceptance amount of memory (like a stress test).

### Different Levels of Testing

- __Level 1:__ Testing components (i.e. classes), then program (i.e. use cases), then suites (i.e. application).
- __Level 2 (Alpha Testing or Verification):__ Execute programs in a simulated environment and test inputs and outputs.
- __Level 3 (Beta Testing or Validation):__ test in a live use environment and test for response times, performance under load and recovery from failure, etc.

### Summary of Testing Activities

![[Pasted image 20241211163923.png]]

### Regression Testing

- __Regressing Testing__ is a process in which the software is __retested__ so as to ensure that its behaviour has not been compromised by the addition of new, or change to existing code.
- It facilitates faster development:
	- It reduces risk of changes
	- Unexpected effect can be found quickly.
	- Ability to run thousands of tests in one click.

### When is Regression Testing needed?

- __Regression Testing__ is important but van be very time and cost consuming.
	- Requires capturing of data, analysis, reporting, etc.
- Consider the following scenario.

__Question:__
![[Pasted image 20241211164229.png]]

__Answer:__
![[Pasted image 20241211164323.png]]

### Test Documents (Plans/Cases/Results)

- __Test Plans__
	- Written before the tests are carried out!
	- Written, in fact, before the code is written.
	- Contains test cases.
- __Test Cases__ are specified with the following formation:
	1. Test data.
	2. Expected Outcomes.
	3. Description of the Test.
	4. Test Environment and Configuration.
- __Test Results__
	- Used for analysis, recorded in a spreadsheet, database or a specialist package (e.g. Jira).
	- Record when tests are failed or passed.
	- Include statistics, e.g. percentage of passed/failed.
	- Ideally should be linked to requirements (traceability!).
	- Error results should be recorded in a fault reporting package, with enough details for development to __reproduce__ them with a view to fixing the bugs.

### Test Planning - Steps

1. Define what is meant by a `Testing Unit`.
2. Determine the types of testing to be performed.
3. Determine the extent of testing (i.e. prioritise the tests).
4. Determine how to document the testing procedure.
5. Determine __input sources__.
6. Decide who will performed which tests.
7. Estimate __resources__.
8. Identify __metrics__ to be collected.

### Determine the Extent of Testing

- Software should be thoroughly tested before __release__, but when should testing stop?
- There is no "one size fits all" scheme, in software testing.
- The testing team should establish a set of stopping criteria:
	- A tested is unable to find another defect in __n__ minutes of testing (where __n__ may be any +ve integer, e.g. 5, 10, 30, 100).
	- When all __nominal__, __boundary__ and __out-of-bounds__ test data show no defect.
	- When a given __checklist__ of test types has been completed.
	- When testing runs out of its scheduled times (DANGEROUS).

### Unit Testing

- __Unit Testing__ is performed to test parts (classes and their methods) of an application __in isolation__.
- Black Box Unit Testing:
	- __Equivalence Partitioning:__ divide inputs values into equivalent groups.
	- __Boundary Values Analysis:__ test as boundary conditions.
- White Box Unit Testing:
	- __Code Coverage:__ test cases cause every line of code (__statement__), all conditions (__branch__) and all possible flows (__path__), from entry to exit, to be executed.

### Unit Testing - Path Coverage Example

- Performing __path coverage__ on the following methods:

```cpp
class Example
{
private:
	static void showResult(int guessed, int toGuess)
	{
		if(guessed == toGuess)
		{
			std::cout << "Well Done! You've Guessed It!" << std::endl;
		}
		if(guessed > toGuess)
		{
			std::cout << "Sorry! Your Guess Is Too High!" << std::endl;
		}
		else
		{
			std::cout << "Sorry! Your Guess Is Too Low!" << std::endl;
		}

		std::endl << "The Number I Have In Mind Is: %d\n", toGuess);
	}
}
```

- A test case for each __distinct path__ path:
	- `showResult(8, 8) : 2 -> 3 -> 11`
	- `showResult(9, 8) : 2 -> 5 -> 6 -> 11`
	- `showResult(7, 8) : 2 -> 5 -> 8 -> 9 -> 11`

### Using Assertions

- __Assertions__ are statements in Java which ensure the correctness of assumptions.
- Allow us to enforce business rules and catch any mistakes.
- Allow us to check for parameter and return values.

```cpp
public:
	void checkCanDrive(int age)
	{
		assert age >= 17 : "Cannot Drive";
		std::cout << "Can Drive At: %d\n", age);
	}
```

### Unit Testing with JUnit

- __JUnit__ is a framework for unit testing which facilitates the writing of repeatable tests.
- To use JUnit 5, typically one imports:
	- `org.junit.jupiter.api.Assertions`
	- `org.junit.jupiter.api.Test`
- Annotates a test method with a @Test
- Uses assert methods, i.e. `assertFalse`, `assertTrue`, `assertEquals`, `assertThrows`, `etc`.

```java
// Switch to Java for this
@Test
public void testAddingStaff() {
	StaffManager sm = new StaffManager();
	sm.addStaff("Lucy", "Bastin");
	Assertions.assertFalse(sm.getAllStaff().isEmpty());
	Assertions.assertEquals(1, sm.getAllStaff().size());
}
```

### JUnit Test Life Cycle - Fixtures

- __Fixtures__ allow you to set up a testing environment: prepare the baseline of your tests.
- Usually fixtures have the following life cycle

```java
@BeforeAll
@BeforeEach
@Test
@AfterEach
@AfterAll
```

- You may want to use the "Before" annotations for the preparation of test data, and the "After" annotations for housekeeping

### Test-Driven Development

- A different approach to writing software.
- The development of the application is thus driven by the test cases solely.
- Writing test cases __before__ writing any source code.
- Code that does not address the issues in the test cases will not be written.
- A testing framework such as JUnit can be used to facilitate TDD.

### Test-Driven Development Process

![[Pasted image 20241211171930.png]]

### Advantages of TDD

- Test cases __ensure a good statement coverage__.
- Only code required to address the requirements is written; __no redundancy__.
- __Rapid feedback__ on the written code.
- Test suite availability for further testing purposes, e.g., __regression testing__

# Unit 7 & 8 - Software 
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

# Unit 9 - Object Oriented
### Unit Outcomes

- How to represent __classes__ and their relationships in UML class diagrams.
- How to design __associations__
- How to evaluate a detailed design in terms of __cohesion__ and __coupling__ 
- What is meant by the __Liskov Substitution Principle (LSP)__ and how it helps to ensure a good design.

### Detailed Design: Classes

- Classes defined in system analysis capture key business concepts and operations, but only present a _partial_ view of the required class model.
- In detailed design, more detail is added, including:
	- __Data Type__ of each _attribute_
	- Adding primary _operations_
	- Defining the _signatures_ and _parameter types_ of operations.
	- Deciding the _visibility_ of attributed and operations.

### Style Guidelines for UML Class Diagrams

- _Class_ name should be _centred_ and presented in __bold__
- The first letter of class names should be _capitalised_ (if the character set supports uppercase).
- _Attributes_ and _operations_ names should begin with a _lowercase_ letter.
- The name of each __abstract class__ should appear in _italics_.
- _Full_ attributes and operations should be shown _only_ when needed. They should be _suppressed_ in other contexts or when merely referring to a class.

![[Pasted image 20241212165004.png]]

### Specifying Attributes: Examples

- The attribute `balance` in class `BankAccount` might be declared with an _initial value_ of zero using the syntax:

```java
balance: Money = 0.00
```

- Attributes that may not be `null` are specified using a _property string_

```java
accountName: String {!null}
```

- Arrays are specified using _multiplicity_

```java
qualifications: String[0...10]
```

- The _derived value_ `availableBalance` whose value is calculated from `balance` + `overdraftLimit` is marked by `/`:

```java
/availableBalance: Money
```

### Operation Signatures

- An operation's _signature_ is determined by the operation's _name_, the _number_ and the _type of its parameters_ and the _return type_, if any.
- _Visibility_ is the visibility of the operation.
	- i.e., `+ (public)`, `- (private)`, `# (protected)`, `~ (package)`
- `BankAccount` __credit()__ operation shown in the diagram as:

```java
credit(amount: Money) : Boolean
```

- More Examples:
	- `- hide()`
	- `+ insertionSort<T -> Comparable>(data: T[1..*])`

![[Pasted image 20241212170143.png]]

### Which Operations to Include?

Here are some guidelines for determining which operations to be shown in a class diagram:
- Show _primary operations_ (i.e. __constructors__, __destructors__, __getters__, and __setters__) where it is necessary.
- Only shown constructors where they have special significance.
- _Varying levels of details_ at different stages in the development cycle.

### Templates

Templates are model Elements that are parameterised by other model Elements.

__Templates__ typically appear within the context of specifying a generic type.

![[Pasted image 20241212170553.png]]

### Class Relations - Notations

![[Pasted image 20241212171236.png]]

### Designing Associations
###### One-Way One-to-One Association

- Class __Owner__ can send `messages` to class __Car__, but not vice versa.
- Each __Owner__ object keeps a `reference` to the owning __Car__ object.

![[Pasted image 20241212171414.png]]

###### Collection Classes

- _Collection_ classes are used to hold the object identifiers (i.e. object references) when message passing is required _from one to many_ along an association.
- OO Languages typically provide support for working with _collection_ classes.

e.g., In the Agate case study, an advertising campaign may include > 1 advertisement. Class `Campaign` may include a field such as:

```java
private List<Advert> adverts;
```

### One-to-many associations using a collection class

![[Pasted image 20241215145346.png]]

### Integrity Constraints

- _Referential Integrity_: an `object identifier` (object reference) should refer to an object that _exists_, otherwise, it should refer to the `null` value.

e.g., The `Campaign` object reference(s) which a `CreativeStaff` object keeps must be either `null` (i.e., the staff is not working on any campaign) or must reference existing `Campaign` object(s).

- _Dependency Constraints_ ensure consistency in case where one attribute may be calculated from other attributes.

An attribute whose value is calculated from other attributes is known as a derived attribute and is marked by / in UML.

- _Domain Integrity_ attributes only hold _permissible_ values.

e.g., Attributes from the `Cost` domain must be non-negative recorded in `2` decimal places.

![[Pasted image 20241215190949.png]]

### Interfaces
###### Interface Specification: UML Notations

- UML supports two notations to show _interfaces_:
	- The _small circle_ icon showing no detail.
	- A _stereotyped class_ icon with a list of the operations supported.
		- _Normally one one of these is used on a diagram._
- The _realisation_ relationship, represented by the dashed line with a (non-filled) triangular arrowhead, indicates that the _client_ class support at least the operations listed in the interface.

![[Pasted image 20241215193008.png]]

### Cohesion and Coupling
###### What are they?

- Bennett, McRobb and Farmer (2010):
	- _Cohesion_ is a measure of the degree to which an element contributes to a single purpose.
	- _Coupling_ describes the degree of interconnectedness between design components. It is reflected by the number of links an object has and by the degree of interaction the object has with other objects.
- Braude and Bernstein (2011):
	- _Cohesion_ within a module is the degree to which the module's elements _belong together..._ it is a measure of how focused a module is.
- The concepts of coupling and cohesion are not mutually exclusive - the _interact_
- _Maximising cohesion_ of modules of code so all contribute to the achievement of a single function.
- _Minimising coupling_ - unnecessary linkages between module that make them difficult to maintain or use in isolation.

- Several kinds of coupling and cohesion that are relevant within an _object-oriented approach:_
	- Interaction coupling
	- Inheritance coupling
	- Operation cohesion
	- Class cohesion
	- Specialisation cohesion
	- Temporal cohesion

###### Interaction Coupling

- _Interaction Coupling_ is a measure of the number of message types an object sends to other objects and the number of parameters passed with these message types.
- As a rule of thumb: message connections involving > 3 parameters should be reconsidered to see if they could be simplified.
- Interaction Coupling in a detailed design should be kept to a _minimum_ to reduce the possibility of changed rippling through the system to make reuse easier.

###### Inheritance Coupling

- _Inheritance Coupling_ describes the degree to which `subclass` actually needs the features it inherits from its `base class`.
- As a rule of thumb, class inheritance should not be used in abundance or carelessly as it may weaken the degree of _information hiding_ in the classes concerned.

![[Pasted image 20241220192419.png]]

- Classes __Vector__ and __Stack__ in package `java.util` is an example of _poor_ inheritance coupling because __Stack__ inherits a range of unsuitable methods from __Vector__.
- __Stack__ is a _Last-In-First-Out (LIFO)_ collection with access to its elements at the __top__ of the stack only.
- __Stack__ inherits inappropriate methods such as `insertElementAt`, `firstElement`, `setElementAt`, `removeElementAt`, and `sort` from __Vector__.

###### Operation Cohesion

- _Operation cohesion_ measured the degree to which an __operation__ focuses on a _single_ __functional requirement__.
- Example of _good_ operation cohesion:

![[Pasted image 20241220192920.png]]

`calculateRoomSpace()` performs an atomic task: _computer total area of the room._

###### Class Cohesion

- _Class Cohesion_ measures the number of things a __class__ represents.
	- _Each class should represent only a single entity, e.g. Lecturer, Student, Programme, Module, etc._
- _Class Cohesion_ measures the degree to which a __class__ is focused on a _single_ __requirement__, e.g. maintaining a particular typical type of record.
- Example of _good_ class cohesion:

![[Pasted image 20241220193242.png]]

- _Lecturer includes attributes and operations which address the same requirement: maintain lecturer record._

###### Specialisation Cohesion

- _Specialisation Cohesion_ addresses the semantic cohesion of inheritance hierarchies.
- It measures the _semantic-relatedness_ between the inherited attributes and operations to the class itself.
	- _i.e. are the classes related to each other through a __is a__ or __is a kind of__ relation? Or is the generalisation/specialisation relation defined out of convenience?
- Class A should __extend__, and hence __inherit__ attributes and operations from, class B _only_ when A is a _specialised_ version of B, not simply because it needs to use the attributes and operations in B.

![[Pasted image 20241220233014.png]]

###### Temporal Cohesion

- Module elements linked only by the time at which they need to be done.
- e.g. an __initialisation__ module

"Temporal cohesion is present when a subprogram performs a set of functions that are related in time, such as 'initialisation', 'house-keeping', 'wrap-up' ... The only connection between these operations is that they are performed within the same limited time-span"

###### Points to note

- _"Low cohesion classes often represent a very 'large grain' of abstraction or have taken on responsibilities that should have been delegated to other objects ... as a rule of thumb, a class with high cohesion has a relatively small number of methods, with highly related functionality, and does not do too much work. It collaborates with other objects to share the effort if the task is large"_
- _"...no coupling between classes ... offends against a central metaphor of object technology ... low coupling taken to excess yields to poor design ... it is not high coupling per se that is the problem; it is high coupling to elements that are unstable in some dimension, such as their interface, implementation, or mere presence."_

### Liskov Substitution Principle
###### What is it?

_"What is wanted here is something like the following substitution property; if for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behaviour of P is unchanged when o1 is substituted for o2 then S is a sub-type of T."_

```java
public void setDriver(Member carUser) {
	if(carUser.hasDrivingLicence()) {
		driver = carUser;
	}
}
```

```java
public void setDriver(Staff carUser) {
	if(carUser.hasDrivingLicence()) {
		driver = carUser;
	}
}
```

_Here Staff is an extension of Member_

- _"Functions that use pointers or references to base classes must be able to use objects derived classes without knowing it."_
- Essentially the principle states that, in object interactions, it should be possible to treat a __derived object__ (an instance of a __subclass__) as if it were a __base object__ (an instance of a __superclass__) without integrity problems.

###### A Liskov-compliant Class Hierarchy

![[Pasted image 20241220235017.png]]

###### Why LSP?

- LSP helpts to ensure that an OO class design is _maintainable_ and _reusable_
	- Subclasses typically inherit attributes and operations from their superclass.
	- If an attribute or operation is unsuitable (not applicable) for the semantic of a subclass, it is possible for the subclass to _"disinherit"_ it by declaring it __private__.
		- _However, this will violate the Liskov Substitution Principle._

###### Applying Liskov Substitution Principle

![[Pasted image 20241220235330.png]]

# Unit 10 - Design Patterns
### Unit Objectives

- Cover well-known design patterns:
	- Singleton
	- Adapter
	- State
	- Strategy
	- Observer
	- Composite

### What is a Design Pattern?

- A design pattern is a "_description of communicating objects and classes that are customised to solve a general design problem in a particular context."
- Patterns are _problem-centred_, not _solution-centred_.
- Patterns capture and communicate "_best-practice_" and expertise.

### Patterns and Non-functional Requirements

- Patterns are typically applied to address __non-functional requirements,__ which include:
	- Changeability
	- Interoperability
	- Efficiency
	- Reliability
	- Testability
	- Reusability

### Pattern Template

- _Meaningful_ __name__ reflecting the knowledge embodied by the pattern.
- A description of the __Problem__ that the pattern addresses.
- __Context__ the circumstances in which the pattern can be applied.

- __Forces__
	- The constraints addressed by the solution.
	- Any trade-offs or language specific issues.
- __Solution__
	- The components involved in the pattern and their relationships.
		- _May be depicted as a __UML class diagram__ or __object diagram___

### GoF Design Patterns

- Gamma et al. (1995) documented a catalogue of 23 design patterns.
	- __GoF (Gang of Four)__ refers to the authors of the book.
- __GoF Patterns__ are classified by two criteria:
	- __purpose__: _creational_, _structural_ & _behavioural_
	- __score__: _class_ & _object_

###### Creational Patterns

- Concerned with the construction of object instances.
- Separate the operation of an application from how its object are created.
- Examples:
	- Class: __Factory__
	- Object: __Abstract Factory__, __Builder__, __Prototype__, __Singleton__

###### Structural Patterns

- Concerned with the way in which classes and objects are organised.
- Offer effective ways of using object-oriented constructs such as _inheritance_, _aggregation_, and _composition_ to satisfy particular requirements.
- Examples:
	- Class: __Adapter__
	- Object: __Adapter__, __Bridge__, __Composite__, __Decorator__, __Facade__, __Flyweight__,__Proxy__.

###### Behavioural Patterns

- Address the problems that arise when assigning responsibilities to classes and when designing algorithms.
- Suggest particular static relationships between objects and classes and also describe how the objects communication.
- Examples:
	- Class: __Interpreter__, __Template Method__
	- Object: __Chain of Responsibility__, __Command__, __Iterator__, __Mediator__, __Memento__, __Observer__, __State__, __Strategy__, __Visitor__

### Behavioural Pattern: Observer
###### Context/Issue

- An investment company helps clients find profitable stocks in the market for investment.
	- The company keeps an account for _each_ client.
	- A client may be investing in _multiple_ stocks.
	- The same stock is typically being purchased by _multiple_ clients.
- The price of a stock changes _continually_.
- The investment company needs to maintain _up-to-date_ stock values for all clients.
- _How to ensure that when stock value changes, the clients' accounts are updated immediately?_

###### Potential Solutions 

1. Equip class __Stock__ with an _update_ method which, when invoked, updates the respective value in all __Account__ objects which are referenced by it.

```java
public class Stock {
	private double value;
	private Set<Account> owners;
	// other fields, constructors and methods omitted

	private void updateOwners() {
		for(Account owner : owners) {
			owners.changeStockValue(this.value);
		}
	}
}
```

2. "_Define a one-to-many dependency between objects so that when one object changes state, all of its dependants are notified and updated automatically._"

###### Solution: Description

- Enable the object acting as the _data source_ to communicate with _all_ objects which use the data (i.e. The __Observer__ objects).
- Notify the __Observer__ objects of any change in the data source.
- Upon receiving a change notification, each __Observer__ object updates its __State__.
	- The __observer__ pattern promotes good object-oriented design because it enables the observers to keep their own data up-to-date.

###### Solution: Class Design

![[Pasted image 20241218151635.png]]

###### General Form

![[Pasted image 20241218151658.png]]

###### An Implementation (deprecated!) in Java

![[Pasted image 20241218151818.png]]

###### Discussion

- The _observer_ pattern is used in the __Model-View-Controller__ (MVC) architecture in which the __views__ play the role of the _observer_ and the __model__ is the _observable_, with the __controller__ acting as _clients_, i.e. updating the observable.

![[Pasted image 20241218152413.png]]

###### Example: Car Rental Company

- A car rental company groups similar cars in __car classes__ based on the characteristics of the cars.
- Sample car classes are: __Mini__, __Economy__, __Intermediate__, __Standard__, __Mini MPV__, __Mini Bus__, etc.

![[Pasted image 20241218152726.png]]

- A client _specifies the car class_ which he/she wishes to rent, the car rental company simply _picks one available car from the __fleet___ in the required car class for dispatching to the client.
- To facilitate look-up of available cars in the required __car class__, a _map_ (e.g. __HashMap__) is used to _associate_ each fleet of cards with their respective car class.

```java
private HashMap<CarClass, HashSet<Car>> carList;
```

- To reflect changes in the car market, the company may _create a new __car class___ or _remove an obsolete __car class___ from the system.
- When a new `CarClass` object is added to the `ArrayList` object. `carClasses`, both __Fleets__ and __HireList__ objects will need to add a new key-value pair to their __HashMap__.

![[Pasted image 20241218163702.png]]

- To keep `carList` and `hireList` up to date, Car classes is an _observable,_ and __Fleets__ and __HireList__ are _observers_.

![[Pasted image 20241218165219.png]]

### Structural Pattern: Composite
###### Context/Issue

- Consider the __Agate__ case study: we need to store information about _media clips_ for each _advertisement_...
- Each advertisement may be made up of a _single_ or a _composite sequence_ of media clip(s).
- Each media clip in turn may take up the form of a video clip or a sound clip, or a combination of several media clips.
- How to present the _same interface_ for a media clip whether it is composite or not?
- How can we incorporate _composite structures?_.
- How to present the _same interface_ for a media clip whether it is composite or not?

![[Pasted image 20241218170059.png]]

- How can we incorporate _composite structures?_

![[Pasted image 20241218170142.png]]

###### Solution

- Combine interface and aggregation hierarchies:

![[Pasted image 20241218170254.png]]

###### Basic Structure

![[Pasted image 20241218170321.png]]

###### General Form

![[Pasted image 20241218170349.png]]

###### Discussion

Consider the _general form_ of the __Composite__ pattern:

- The __Composite__ pattern is designed to model _recursive tree structures_ to capture a complex _part-whole relation_ in a class design.
- The __Component__ may be defined as an __interface__ an __abstract class__ or a __concrete class__, depending whether its attributes and operations need to be inherited.
- When applying the __Composite__ pattern to Java software development, the __Composite__ pattern poses an issue: _Methods `addComponent`, `removeComponent` and `getChild` are relevant to the Composite, but irrelevant to the Left classes. Hence, it displays a poor level of __inheritance coupling__ and it also violates the __Liskov Substitution Principle___
- A working solution would be to define the attributes and operations that are _common_ to all the class hierarchy in the __Component__ class and define `addComponent`, `removeComponent` and `getChild`, which are relevant to the __Composite__ only, in the __Composite__ class.

###### Corrected General Form

![[Pasted image 20241219121930.png]]

###### Composite Pattern vs. Composite Structure

The part-whole relationship could alternatively be modelled by a simple _composition_ relationship:

![[Pasted image 20241219122122.png]]

_What are the advantages of using the __Composite__ pattern instead of straight-forward composition_

###### Advantages of using composite pattern

- _Providing more flexibility_:
	- A client class can collaborate with a part (e.g. _Component_) or a whole (e.g. _Composite_) _in the same way_ because they have the same interface.
- _Enabling reuse, reducing code duplication_:
	- Common properties can be defined in the super-class and inherited by both Leaf and Composite subclasses.
	- e.g.: In a graphics application, each graphic component/composite may keep an attribute `isVisible` to indicate if it should be hidden from the view or not.
- _Simplify the implementation by avoiding the need of type casting_:
	- In the composite _structure_ shown earlier, the Composite class keeps a reference to all of its components, in a Collection.
	- However, such a collection object will need to be defined of a general type, e.g. __Object__ in Java, so as to accommodate various types of component objects.
	- _Type Casting_ will therefore be unavoidable when operations specific to each type of component need to be carried out.

###### Example from Java API

- The _composite_ design pattern is used in modelling the part-whole relationship between GUI components.

![[Pasted image 20241219122719.png]]

```java
public static void setFont4All(Component component, Font font) {
	component.setFont(font);

	if(component instanceof Container) {
		Container parent = (Container) component;

		for(Component child : parent.getComponents()) {
			setFont4All(child, font); // recursive
		}
	}
}
```

###### Context/Issue

- Consider the __Agate__ case study: we need to store information about Agate Company to be accessed by different system objects.
- How to ensure that _only one_ instance of the __Company__ class is created?

![[Pasted image 20241219123012.png]]

### Creational Pattern: Singleton

Restrict access to the __constructor__.

- Use class-scope attribute (i.e. __class__/__static__ variable) to ensure a single instance.
- Use class-scope operations (i.e. __class__/__static__ methods) to allow global access.

![[Pasted image 20241219123211.png]]

###### Restricted Access to Constructor

```java
public class Company {
	private static Company companyInstance;

	private Company() {
		// Initialise any instance variables
	}

	public static Company getCompanyInstance() {
		if(companyInstance == null) {
			companyInstance = new Company();
		}
		return companyInstance;
	}
}
```

###### General Form

![[Pasted image 20241219123413.png]]

###### Examples from Java API

- The __singleton__ design pattern is fairly commonly used, examples of such from the Java API include:
	- `java.awt.Desktop.getDesktop`
	- `java.lang.Runtime.getRuntime`

###### Context/Issue

- Consider the class __Campaign__.
- It has four states:
	- `Comissioned`
	- `Active`
	- `Completed`
	- `Paid`
- A __Campaign__ object has different behaviours, depending on the _state_ it is at.
- For example, regardless of the state of a __Campaign__ object (i.e. `Comissioned`, `Active`, etc), there is the need to calculate the costs incurred by this campaign so far. Each state, however, entails a different costing model.
- _How can an object's behaviour change at run-time, based on the state is it as?_

###### Potential Solutions: using nested if statements

_How can an object's behaviour change at run-time according to the __state__ is it at?_

- The state-dependent operations may be implemented using __case__ statement or nested __if__ statements to specify _alternative behaviour_.
	- _What is the issue with this approach?_
- The resulting nested __if__ statement may become very complex...
	- _Especially when on object has many different states._
- Any addition and/or removal of state(s) will require changes made in the nested __if__ statement.

###### Potential Solutions: using separate components

_How can an object's behaviour change at run-time according to the __state__ it is at_

- The class may be factored into _separate components_: one for modelling the required behaviours in each of its states.

![[Pasted image 20241219125744.png]]

###### Solution

- An object whose behaviour changes depending on the state that it is in delegates its _state-dependent operations_ to other objects which are designed to model state-dependent behaviour.
- Each state that the object can be in is modelled by a __concrete class.__ These classes implement the same __interface__ which specifies state-dependent operations.
- The object keeps a reference to the current state object, which provides __polymorphic behaviour__.

###### General Form

![[Pasted image 20241219130108.png]]

###### Application

![[Pasted image 20241219130129.png]]

- Interface __Marital Status__:

```java
public interface MaritalStatus {
	// Calculate and returns the amount of income tax to be charged.
	public abstract float calcIncomeTax(float income);
	// Calculate and returns the amount of child benefit entitiled.
	public abstract float calcChildBenefit(Person[] children);
}
```

- Class __Single__:

```java
public class Single implements MaritalStatus {
	public float calcIncomeTax(float income) {
		
	}

	public float calcChildBenefit(Person[] children) {
	
	}
}
```

- Class __Person__:

```java
public class Person {
	private static final int MAX_CHILDREN = 10;

	private MaritalStatus maritalStatus;
	private Person[] children;
	private Person spouse;
	private float income;

	public Person() {
		maritalStatus = new Single();
		children = new Person[MAX_CHILDREN];
		spouse = null;
		income = 0.0f;
	}

	public MaritalStatus getMartialStatus() {
		return maritalStatus;
	}
}
```

- To provide state-specific behaviour, the actual calculation of income tax and child benefit entitlement are done by the __state__ object:

```java
public class Person {
	private MartialStatus maritalStatus;

	// Other details omitted

	public float calcIncomeTax(float income) {
		return martialStatus.calcIncomeTax(income);
	}

	public float calcChildBenefit(Person[] children) {
		return maritalStatus.calcChildBenefit(children);
	}
}
```

- Over their life, a person's marital status in a software system may need to be changed. Method `registerSpouse(Person)` invokes method `changeState(MaritalStatus)`.

```java
public void registerSpouse(Person spouse) {
	this.spouse = spouse;
	changeState(new Married());
}

public void changeState(MartialStatus newState) {
	maritalStatus = newState;
}
```

From then on, calculation of income tax and child benefit entitlement will be done using operations defined in class __Married__.

###### Discussion

- The __state__ pattern enables an object to exhibit different behaviour at _run-time_ in a flexible manner.
- __State objects__ which provide different behaviours for the same operation may be created at run-time and attached to the __context object__ whenever the circumstance of the modelling entity changes.

###### Context/Issue

- Consider a word processing application which supports different ways to align the text in each paragraph.
- Depending on the type of document, a different alignment strategy would apply.
- _How to avoid hard-coding all the available alignment strategies in the Composition class which is responsible for laying out the text in a document?_
- _How to ensure that introducing new alignment strategies in future will require minimal changes to existing classes_

###### Potential Solutions

- Hard-code all alignment strategies in the __format__ method using a set of __if-then-else__ statements:

```java
public void format() {
	if(isExamPaper(text)) {
	
	}
	else if(isBook(text)) {
	
	}
	else  {
	
	}
}
```

- Define _each_ alignment strategy in a _separate class_ and make all of them __implement__ the same __interface__.
- Class __Composition__ will interact with a suitable alignment strategy through the interface.

![[Pasted image 20241219132034.png]]

###### Solution

- Define a family of algorithms using an __interface__ and a set of __concrete classes__.
- The __client class__ may use any _one_ of the algorithms.
- Existing algorithms may change _without_ having an impact on the __client__ class.

###### General Form

![[Pasted image 20241219132158.png]]

###### Discussion

- The _strategy_ pattern enables a class to delegate its task to more specialised objects. The __context__ class will not need to keep data required by the family of algorithms. The resulting __context__ class will be less bloated.
- In order to perform the required operation, each __concrete strategy__ class needs access to the data in the __context__ class. One way to achieve this is by passing the reference of the __context__ to the collaborating __concrete strategy__ object.

- Class __IntroductoryOffer__:

```java
public class IntroductoryOffer {
	public double applyPricingScheme(Campaign c) {
		
	}
}
```

- Class __Standard__:

```java
public class Standard {
	public double applyPricingScheme(Campaign c) {
	
	}
}
```

- Class __Campaign__:

```java
public class Campaign {
	private Pricing strategy;

	public Campaign(Pricing strategy, ...) {
		this.strategy = strategy;
		...
	}

	public double calculateCost() {
		double charge = strategy.applyPricingScheme(this);
	}
}
```

_Which pricing strategy to use it determined before the campaign comes into existence. Class __Campaign__ does not need to know all pricing strategies available.

- Class __SalesSubsystem__:

```java
public class SalesSubsystem {
	public void addCampaign(...) {
		Campaign c = new Campaign(new Standard());
	}
}
```

_Each pricing strategy can be modelled using the __singleton__ pattern_

### Difference between State and Strategy?

- Both use polymorphic classes.
- Both have a context (e.g. editing or browsing)
- Both actually apply different strategies (e.g. use different versions of an algorithm).
- Both are trying to avoid inflexible nested case or if statements.
- Both are actually about doing work in alternative ways, and a __ConcreteState__ actually encapsulated its own group of strategies for executing function.
- The __StatePattern__ is a way to vary an object's behaviour dynamically, whereas the __StrategyPattern__ is a way to vary the implementation.

###### Context/Issue

- Consider a software application (e.g. `MyDraw`) for users to draw and arrange __graphical elements__ (e.g. lines, polygons, text, ...) into a diagram.
- We define an __abstract class__ (e.g. __Shape__) for modelling a generic _graphical element_. Subclasses of __Shape__ would model __Line__, __Polygon__, __Circle__, etc.
- We also need a __Text__ subclass for displaying and editing text.
- There is a __TextEditor__ _framework_ class which addresses the requirements of our intended __Text__ class.
- However, __TextEditor__ does not have the same interface as the _abstract class_ __Shape__ which `MyDraw` expects to work with.

![[Pasted image 20241220191159.png]]

_How to enable an existing class to work with classes with a different and incompatible interface?_

###### Solution

_Gamma et al. (1995)_

- Using an __Adapter__ class, convert the interface of a class into another interface which clients expect.
- Clients call operations on an Adapter instance.
- The _Adapter_ then invokes the respective __Adaptee__ operations to complete the task.
- The __Adapter__ class will also include concrete implementation of other methods which are defined by the implementing __interface__ but not supported by the __Adaptee__ class.

![[Pasted image 20241220191508.png]]

###### General Form

![[Pasted image 20241220191535.png]]

###### Examples from Java API

- Examples of the __Adapter__ design pattern in the Java API include:
	- `java.util.Arrays.asList`
		- _Method `asList` adapts an array to the collection type list._
- An __Adapter__ is particularly useful when you want to use an existing class, but its interface does not match the one required by your application.

### Applying Pattern
###### Before

- Is there a _simpler_ solution
	- _Patterns should not be used for the sake of it._
- Is the context of the pattern consistent with that of the problem?
- Are the consequences of using the pattern acceptable?
- Are constrains imposed by the software environment that would conflict with the use of the pattern?

###### After selecting a suitable pattern

Steps to follow in applying the selected pattern:

1. Read the pattern to get a complete overview.
2. Study the __Structure__. __Participants__ and __Collaborations__ of the pattern in detail.
3. Examine __Sample Code__ to see an example of the pattern in use.
4. Choose names fo the pattern's participants (i.e. classes) that are meaningful for your application.
5. Define the classes.
6. Choose application specific names for the operations.

# Unit 11 - Implement
### Unit Objectives

- Learn about the tasks involved in implementation.
- Techniques involved in writing maintainable code.
- What is meant by _defensive programming_ and for to enforce intention.
- What tools are used in software implementation.

### Implementation - What does it involve

Two different views:

- Bennett et al. (2010) wrote:

"Implementation is concerned with the _process_ of building the new system. This involves _writing program code_. developing _database_ tables, _testing_ the new system, setting it up with _data_, possibly transferred from an old system. _training-users_ and eventually _switching over to the new system_."

- Braude & Bernstein (2011) however stated:

"The implementation phase consists of _programming_ which is the translation of the software design developed in the design phase to a programming language. It also involves _integration_, the assembly of the software parts."

- One thing in common is that `implementation` involves constructing a software system based on a design: this involves _writing program code._
- To facilitate the coding process, one needs to consider:
	- Which programming _languages_ to use for developing the required software.
	- Which _software tools_ will be used to support the software development process.
	- How to ensure that the code, though written by different programmers, will be _easy to read, understand, and maintain_.
	- How to effectively _manage changes to programs_ throughout the development process.

### Language Choice

The choice of the programming language depends on the nature of the required software system.

- e.g., JavaScript, CSS, and HTML for _client-side_ web application
- For server side scripting we could use; _PHP, Java SpringBoot, Ruby, Python_.
- Lots of simultaneous, lightweight communications? Maybe _Node.js with websockets_.
- Where a client prefers to use Microsoft products only, the implementation is likely to be _C#_.
- If the tasks require a substantial amount of processing on _tree_ data structures, a _functional programming language_ such as _Lisp, Haskell_ or possibly _Julia_ is likely to be a good choice.
- If a system is expected to perform a lot of efficient _low-level system operations_ and _efficiency_ is paramount, _C_ may be a preferred language choice.
- If the required software system is expected to run on _different platforms_ a language like _Java_ or _Scala_ would be appropriate.

### Writing Classes

- _Class_ names should be _meaningful_, e.g., in the `Agate` example, `CampaignStaff` would be a better class name than `Staff`.
- Avoid using _ambiguous_ or _cryptic_ names such as `Record` or `C1`
- The purpose of each class should be _clearly_ and _concisely_ stated in the documentation comment.
	- _This view is not universally agreed. Some software developers adopt the "comment-free" practice, and opt to achieve clarity by structuring the source code and naming identifiers, variables, etc. in a way that makes the code feel self-explanatory._

### Documenting Methods

- The _purpose_ of each method should be clearly stated in code comments, e.g.:

```java
// Tests whether this date is after the specified date.
public boolean after(Date when)
```

- To facilitate _maintenance_ and _reuse_, it is helpful to specify the following information for methods, especially for the _non-trivial_ ones:

	- Intent
	- Return
	- Exceptions
	- Known Issues
	- Preconditions
	- Post-conditions
	- Invariant

- __Intent__:
	- An _informal_ statement of what the method is intending to do.
- __Return__:
	- The value which the method returns.
- __Known Issues__:
	- Honest statement of what has to be done, defects that have been repaired, etc.
- __Exceptions__:
	- Capture the situations when an _abnormality_ occurred during the _execution_ of the method.
	- Such situations may occur due to __preconditions__ not being met.
- __Preconditions__:
	- What must be true _when_ a method is invoked
	- Conditions on non-local variables, including the parameters, that the method assumes, e.g.:

```java
	private int price;
	// Precondition: reduction > 0
	public void reducePrice(int reduction) {
		price -= reduction;
	}
```

- Verification of these conditions is not guaranteed by the method as it is assumed to be done by the caller.

- __Post-conditions__:
	- What must be true _after_ a method completes successfully.
	- Specify the _effect_ of the method.
	- Specify the value of non-local variables after execution.
	- Notation: `x'` denotes the value of variable x after execution, e.g.:

```java
	private int price;

	// Post-conditions: price' = price - reduction
	public void reducePrice(int reduction) {
		price -= reduction; // = price'
	}
```

### Class In-variants

- _Class in-variants_ specify constraints on __Attributes__ and their relationships. object, e.g.:

```java
public class Time {
	private int hour;    // hour >= 0 && hour < 24
	private int minute;  // minute >= 0 && minute < 60
	private int second;  // second >= 0 && second < 60
}
```

- Even though the value of each attribute in an object might change at runtime, its values must conform to the _class invariants_.

### Java Assertions

- __Preconditions__, __Post-conditions__ and __In-variants__ can be specified in a Java program as __Assertions__.
- _Assertion_ in Java provides a convenient tool for run-time checking.
	- As well as a means for documentations.
- An `Assert` statement typically:
	- Performs a _check_, and
	- Displays a message when the check _fails_.
- An `Assert` statement may also:
	- Throw an exception, and
	- Include file and line info.
- By default, assertions are _ignored_ by the JVM and they are used mainly for _debugging_.
- To _switch on_ assertion checks, a Java program needs to run with the option `-ea` (i.e. enable assertions), e.g.:

```java
	java -ea ArrayRemove
```

- Where `ArrayRemove` is a compilation unit which includes a _main_ method.

_N.B. Do not confuse assert methods in JUnit with `assert` statements in Java. They serve different purposes._

### Object-Oriented Standard

- Naming standards should be agreed early in the project.
- A typical _object-oriented standard:_
	- Classes with capital letters: __Campaign__
	- Attributes and operations with initial lower case letters: `userID`

### Hungarian Notation

- The __Hungarian Notation__ is typically used in __C__ or __C++__.
- Identifiers are prefixed by an abbreviation to show the type of the `variable`
	- `b` for boolean: `bOrderClosed`
	- `i` for integer: `iOrderLineNumber`
	- `btn` for button: `btnCloseOrder`

### Underscore Convention

- Another convention commonly used for _column names_ in databases uses _underscores_ to separate parts of a name instead of capital letters, e.g.:

```SQL
Order_Closed
```

or in Postgres...

```
order_closed
```

This convention makes it easier to replace the underscores with spaces to produce meaningful column headings in reports.

### Documentation Standard

- The one who wrote a piece of code is unlikely to be the one having to maintain it in future. Hence, it is important that code is _readable_ to facilitate maintenance.
- _Good documentation is important_ to facilitate maintainability and re-usability of any written code.
- Java has well-defined _documentation standards_ which should be adhered to if coding in __Java__ (Javadoc).
- Use _XML_ tags if coding in __C#__.
- Many _IDEs_ include features for generating __Javadoc__ from comment automatically.

### Naming Conventions For...

- __Packages__: all lower case.
	- _internal use_: prefix with name of product, e.g.: `cwkl.shapes`
	- _for distribution_: prefix with domain name, e.g.: `uk.ax.aston.cs`

_The word in between each full stop corresponds to the name of a __folder__ in a file system._

- __Reference Types__ (i.e. classes/interface names): start with capital, then mixed case
	- _classes_: use a noun describing an instance, e.g.: `MyShape`.
	- _interfaces_: either a noun, e.g. `Observer`, or an adjective, e.g. `Cloneable`.
- __Methods__:
	- Active methods (i.e. __Mutator Methods__) usually start with verb, e.g. `changeSize()`
	- Getter methods (i.e. __Accessor Methods__) named by return value, e.g. `length()`, or with a '_get_', e.g. `getLength()`.
- __Fields and Constants__:
	- __Static Final__ fields (i.e. __Named Constants__): all capitals, e.g. `EQUALS_TOLERANCE`, `INITIAL_VALUE`.
- __Parameters__: some capitalisation as method names,
	- e.g. `newSize`
	- Choose fitting, yet succinct names, for parameters.
	- Keep them consistent if they have the same meaning.
- __Local Variables__: same capitalisation as method names, e.g.: `count`
	- Always use _meaningful_ names good for achieving readability.
	- Except for routine cases, e.g. `for(int i = 0; ...; i++)`

### Documentation Comments

- May contain a number of special __tags__, e.g.:
	- `@author`
	- `@version`
	- `@see` hyperlink to documentation of another member, class
	- `@param` every method parameter should have one
	- `@return` describes the return value of a method.
	- `@throws` describes potential exception propagation.

- Start with `/**` and end with `*/`

### Defensive Programming

- _Defensive Programming_ is a programming technique which seeks to minimise program errors by _anticipating_ potential errors and _implementing_ code to handle them.
- Techniques of defensive programming include:
	- Various error handling techniques.
	- Buffer overflow prevention.
	- Enforce intentions.

###### Error Handling Techniques

- _Wait for a legal data value_: typically used when getting data from an external source, e.g. user interface.
- _Set a default value_: typically used to ensure the continuity in execution of a (critical) process.
- _Use the previous result_: typically used when a constant stream of input is expected as a regular interval.
- _Log error_: Store error info for later use or analysis.
- _Throw an exception_.
- _Abort_: typically used in operations where illegal data may lead to a fatal consequence, hence the system must be aborted and reset.

###### Buffer Overflow Prevention

- Some languages (e.g. __C__ and __C++__) permit data to be written to memory and even the data require more space than what was declared in the code, _so long as_ the required space does not exceed the space allocated to the program (e.g. through the `malloc` function).
- This may lead to _overwriting_ existing data kept in the memory.
- Such overwriting, when exploited, may lead to a _security breach_.
- _Buffer overflow prevention_ attempts to prevent buffer overflow by checking the size of variables.

###### Enforce Intention

- Use suitable programming constructs to enforce the intended design or use a piece of code.
- Use keywords such as `final` and `abstract` to enforce coding intentions, e.g.:

```java
public final class String {...}
public abstract class AbstractList {...}
```

- Make constants, variables and classes as _local_ as possible e.g.:

```java
for(int i = pos; i < array.length - 1; i++) {...}
```

- Use the __Singleton__ design pattern if only one instance is expected from a class.
- Define attributes and operations as `private` if they are not intended to be accessible by other classes.
- If a class is expected to be _extended_ by other classes, make attributes `protected` and define _accessor methods_ for accessing their values.
- If a method is not expected to be used by classes in another package, do not use the `public` keyword to specify its _visibility_.
- Use _enumerate types_ to enable a variable to be assigned with a predefined set of constants, e.g.:

Rather than:

```java
int tShirtSize = 1
```

We define an _enum_ type in Java to model permissible sizes for a T-shirt:

```java
public enum Size {
	XS, S, M, L, XL, XXL
}

Size tShirtSize = XS;
```

- Consider introducing new classes to encapsulate legal parameter values so as to prevent bad data, e.g.: 

Instead of:

```java
determineRoadTax(String vehicle)
```

We use:

```java
determineRoadTax(Vehicle vehicle)
```

Where class `Vehicle` has various _factory methods_ to create the permissible types of vehicles, e.g.:

```java
Vehicle createCar() {...}
Vehicle createLorry() {...}
Vehicle createMotorbike() {...}
```

### Software Implementation Tools
###### Modelling Tools

- Many interactive development environment (IDEs) _support UML_.
	- However, the notations used might not always strictly follow the current standard.
- Some modelling tools support _automatic generation_ of program code (in __Java__, __C++__, and __VB__) from the models e.g. __Visual Paradigm__.
- Some also support _reverse engineering_ of code (i.e. generating a design model from existing code).
- Some of them map classes to a _relational database_.

###### IDEs (Integrated Development Environments)

- Manage files in a project and the dependencies among them.
- Link to __configuration management tools__.
- Use compilers to build the project, _only_ recompiling what has changed.
- Provide various facilities such as _debugging_, _refactoring_, _auto-layout_, _documentation generation_, etc.
- May include a _visual editor_ for GUI building.
- Con be configured to link to third party tools.

###### Configuration Management Tools

- Include elements of __version control__ - to _compare_ source code so as to assist in resolving potential __conflicts__.
	- Though configuration management is more than just version control.
- Maintain a record of _file versions_ and the _changes_ from one version to the next.
- Record all the versions of software and tools that are required to produce a repeatable software __build__.
- __Dockerfiles__ are a (fairly rudimentary) form of configuration management.

###### DBMS (Database Management Systems)

A DBMS typically comprises:
- Server System.
- Client Software (administration interfaces, ODBC and JDBC drivers)
- Tools to manage the database and carry out performance tuning.
- Tools to make compiled classes persistent so they can be used with object DBMS.
- Large DBMS, such as __Oracle__, come with many tools, even their own application server.

###### Application Containers

- Web Containers, e.g. __Tomcat__ (__Java__), __Flask__ (__Python__).
	- Runs servlets and small-scale applications
- Applications Servers, e.g. __Glassfish__, __WebSphere__, __nginx__, __Apache Web Server__.
	- Provide a framework in which to run large-scale, enterprise applications.

###### Installation / Deployment Tools

- e.g. __GitLab CI/CD__, __AWS CodeDeploy__, __Jenkins__.
- Automate extraction of files from an archive and setting up of configuration files and registry entries.
- Some maintain information about dependencies on other pieces of software and will install all necessary packages.
- Uninstall software, removing files, directories and registry entires.

# Unit 12 - Refactoring
### Unit Objectives

- What is meant by refactoring
- Various kinds of refactorings
- How to use __Eclipse__ to perform some refactorings.

### Some Tips on Software Development

- _"Any fool can write code that a computer can understand. Good programmers write code that humans can understand."_
- _"When you find you have to add a feature to a program, and the program's code is not structures in a convenient way to add the feature, first refactor the program to make it easy to add the feature, then add the feature."_
- _"Refactoring changes the programs in small steps. If you make a mistake, it is easy to find the bug."_
- _"Before you start refactoring, check that you have a solid suite of tests. These tests must be self-checking."_

### What is Refactoring?

- _"Refactoring is a process of altering source code so as to lave its existing functionality unchanged."_
- __Refactoring__ refers to the process of restructuring source code in order to improve its __readability__, __maintainability__ and __extend-ability__ without altering and _observable_ behaviour of the software system.
- Though a key reason for refactoring may be to improve the source code's ability to cope with new requirements, i.e. in preparation for _system extension_, refactoring itself does _not_ and should not, lead to any change in the _functional requirements_ which the source code is to address.
	- __This allows the same suite of automated tests to be used.__

###### Examples: Renaming

__Renaming__

- Renames an element and (if enabled) corrects all references to the elements (also in other files).
- An element may be a:
	- __method__
	- __method parameter__
	- __field__
	- __local variable__
	- __type__
	- __type parameter__
	- __enum constant__
	- __compilation unit__
	- __package__

###### Examples: Promoting an attribute to a class

__Promoting attribute to class__

- Create a new lass for modelling an attribute.
- Typically, the promoted attribute was defined as a __primitive__ or __String__ type previously
- The new class enables further information to be modelled.

_before:_

```java
public class Customer {
	private String firstName;
	private String surname;
	private String address;

	// other fields and details omitted.
}
```

_after:_

```java
public class Customer {
	private String firstName;
	private String surname;
	private String address;

	// other fields and details omitted.
}
```

### Why is there a need for refactoring?

- Refactoring is _particularly relevant_ in __Agile Development__.
- In __Agile__ project life cycle, the typical phases in a __waterfall__ model are performed _repeatedly_ in cycles, i.e. requirements capture, design, implementation, testing, requirements capture, design implementation, testing, etc.
- In _each_ cycle, new code is written and _added_ to the existing __code base__.
- At each cycle, the focus is to develop code that _addresses the current requirements_.
- At the end of each cycle, the __code base__ needs to be _"cleaned up"_ in order to prevent it from becoming too messing and difficult to maintain.

![[Pasted image 20241226123144.png]]

- Refactoring facilitates __maintenance__ and __extension__ of the code base.

### Big Refactorings

- This kind of refactoring changes the _overall system design_ in terms of the number of classes invoked.
- We will consider four kinds of _big refactoring:_
	- Extract hierarchy.
	- Tease apart inheritance.
	- Covert procedural design to objects.
	- Separate domain from presentation.

###### 1. Extract Hierarchy

- Refine the current class design by introducing a _new class hierarchy_ or extending an existing class hierarchy.

![[Pasted image 20241226125409.png]]

###### 2. Tease Apart Inheritance

- To alleviate the potential for _class explosion_, identify _common properties_ and model them as _separate_ class hierarchies.

![[Pasted image 20241226130702.png]]

###### 3. Convert procedural design to objects

- Improve the design by removing _procedural_ components into classes.

![[Pasted image 20241226133238.png]]

###### 4. Separate Domain from Presentation

- Make the _responsibility_ of each class more _focused_ by separating the presentation operations from the domain classes.

![[Pasted image 20241226133448.png]]

### Other Types of Refactoring
###### Composing Methods

_These refactoring apply at the __method level__ only_.

- __Extract Method__
	- Identify a block of code and _create a new method_ to contain it.
	- Why?
		- Code becomes more readable, especially if the new method had a meaningful name.
		- Code becomes more modular and re-usable if that block of code is generically useful.
- __Inline Methods__
	- _replace_ a class to a method by the statements of the method
	- Why?
		- e.g. Where a method body has become condensed down to just one line.
		- Inverse of __Extract Method__!
- __Inline Temp__
	- _remove_ a __local temporary__ variable and replace it by the associating expression.

```java
boolean hasDiscount(Order order) {
	double basePrice = order.basePrice();
	return basePrice > 1000;
}
```

- __Introduce Explaining Variable__
	- use a _local variable_ to replace a portion of a complex expression.

###### Moving Features between Objects

- __Move Method__
	- Move a method from one class to another.
- __Move Field__
	- When a new class is introduced, existing fields may need to be moved to the new class.
- __Extract Class__
	- Make a new class from a subset of existing fields and methods.

###### Dealing with Generalisation

- __Pull Up Field__
	- When >= 2 subclasses in the same class hierarchy have the same field(s), move the common field(s) from the subclasses to the superclass.
- __Pull Up Method__
	- When two methods in different subclasses within the same class hierarchy have essentially the same behaviours, move the method to the superclass.
- __Push Down Field__
	- When a field is used by some subclasses only, but not all subclasses, move the field to those subclasses which use that field.
- __Push Down Method__
	- When there is a method in a superclass that is relevant to only some of its subclasses, move that method to those subclasses.
- __Extract Subclass__
	- When there is a feature in a class that is applicable to some instances only, create a subclass for that class and move the feature to it.
- __Extract Superclass__
	- Make a new class from the common field(s) and method(s) in a set of existing classes, with the extracting classes becoming the direct subclasses of the new class.
- __Extract Interface__
	- Make a new interface from an existing class, with the class becoming one which implements the new interface.
-