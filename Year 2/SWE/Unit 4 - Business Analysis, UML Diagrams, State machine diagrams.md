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
- UML Object, Class ans State Machine Diagrams