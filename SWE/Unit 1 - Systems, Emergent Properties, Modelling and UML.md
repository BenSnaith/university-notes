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

![[Untitled 5 4.png|Untitled 5 4.png]]