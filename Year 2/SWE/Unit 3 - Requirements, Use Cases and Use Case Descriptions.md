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

- The <<include>> relationship:
    
    R1.1: The content management system that shall allows an administration to create a new blog account, provided the personal details of the applying author are verified using the Author Credentials Database.
    

[](https://www.notion.soundefined)

- <<Extend>> in this context means optionally including, i.e. A may or may not include B.

[](https://www.notion.soundefined)

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

![[image 5 4.png|image 5 4.png]]

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
    - Explain rationale.