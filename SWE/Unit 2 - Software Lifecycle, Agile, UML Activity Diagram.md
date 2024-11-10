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

![[image 14 2.png|image 14 2.png]]