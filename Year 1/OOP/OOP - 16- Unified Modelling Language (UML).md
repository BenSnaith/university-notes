## What is UML?

Origins

- We need to analyse and design first before implementing big systems: we need notations
- The rise of OO analysis and design produced many notations
- Three of the leading experts (Booch, Rumbaugh and Jacobson) proposed in ‘97 the Unified Modelling Language
- UML now driven by Object Management Group consortium
- It is language dependent: differs from Java in places

## What is UML for?

Uses

1. Visualise a system as is or as desired
2. Specify structure and behaviour
3. Giving a template for construction: generation of code from UML diagrams
4. Document decisions taken

## Some types of UML diagrams

|   |   |
|---|---|
|Class|Describes the various concepts in the domain (analysis) or the Java classes/interfaces in your system (design). Good for the static view|
|Use case|Presents the ways in which your system can be used, and the different people and entities that relate to your system (stakeholders)|
|Sequence|Shows how objects talk to each other (dynamic view) to achieve a goal. Focuses on the time ordering if the messages|
|Collaboration|Similar to sequence diagrams, but focuses on the way the communicating objects are organised|

From this module, you should be able to read/write class diagrams and read sequence diagrams. Rest will be discussed next year.

## Classes

- Box with 1-3 compartments for the name, fields and methods (methods)
- Detail level can vary:
    - If the details are in another diagram, just the name is fine
    - At the analysis stage, you do not really need types
    - At the design stage, you want visibility and types
- Abstract classes use italics for their names (wavy underlines if doing diagram by hand)

## Specifying Fields

Notation (static fields are underlined)

- (vis) name (’:’ type) (’(’ mult ‘)’) (’=’ default)

Optional parts (in brackets)

- Visibility: - (private), + (public), # (protected), ~ (package)
- Type: goes at the end
- Multiplicity: “1” for exactly 1 value, “*” for 0+ values, “1..*” for 1+…
- Default: Default value for the field

Examples

- verysimple
- height: Float = 42.0
- # employees: Employee (*)
- - DEFAULT_CAPACITY: int = 50

## Specifying Methods

Notation (static: underlined, abstract: italics/wavy ul)

- (vis) name ‘(’( param (’:’ type) (’,’ param (’:’ type))* ‘)’ (’:’ return)

Optional parts (in brackets)

- Visibility: same as for fields
- Parameters: At least the name, and maybe the type
- Return type: Just the name of the type, also goes at the end

Examples

- tick()
- - bark()
- # print(message)
- + addTwoNumbers(x: int, y: int): int

## Example

![[Untitled 51.png|Untitled 51.png]]

```Java
public abstract class Frame {
	private FrameHeader nheader;
	private static long uniqueID;
	
	public Status addMessage(Message m) {
		// method def here
	}
	
	protected void setCheckSum() {
		// method def here
	}
	
	private void encrypt() {
		// method def here
	}
}
```

## Example: Reverse

```Java
public class Student1 {
	private static int lastHUN = 0;
	private int HUN;
	private int year;
	private String name;
	
	public Student1(String name, int year);
	public Student1(String name);
	public String getName();
	public int getHUN();
	public boolean equals(Object o);
	public String toString();
	
	private static int nextHUN();
}
```

![[Untitled 1 29.png|Untitled 1 29.png]]

## Interfaces

- Interfaces are drawn either as a circle (simple form) or as a stereotyped class (expanded form)
- An interface does not normally included and fields

![[Untitled 2 27.png|Untitled 2 27.png]]

## Relationships

Classes do not exist in isolation: they are related to each other, or they are useless

|   |   |
|---|---|
|Generalisation|A class/interfaces extends to another class|
|Realisation|A class implements an interface|
|Association|A class stores a reference to objects of another class. Two special cases|
|Composition|Exclusive whole/part relationship|
|Aggregation|Non-exclusive whole/part relationship|
|Dependency|A class uses another class|

## Generalisation: Java “extends”

![[Untitled 3 25.png|Untitled 3 25.png]]

Notation

- Arrow with a white head, using a solid line.
- Goes from subtype to supertype (just like “extends”)

Meaning

- Every Dog is an Animal: all the Animal methods are available from Dog objects
- This means that wherever our program expects an Animal, we can pass a Dog and it will work fine
- You can use generalisation between interfaces (as in Java)

## Realisation: Java “implements”

![[Untitled 4 22.png|Untitled 4 22.png]]

Notation

- Arrow with a white head, using a dashed line
- Goes from impl. to interface (just like “implements”)

Meaning

- Hunter is an implementation of Actor
- Wherever we need an Actor, we can pass in a Hunter

## Association, Composition, Aggregation

![[Untitled 5 22.png|Untitled 5 22.png]]

Notation

- A plain association is just a straight solid line
- Composition uses a black diamond on the “whole” side.
- Aggregation uses a white diamond on the “whole” side.
- Multiplicities are optional on either side, and must be read starting from the other side

![[Untitled 6 18.png|Untitled 6 18.png]]

![[Untitled 7 17.png|Untitled 7 17.png]]

Recursive association

- An association can be from a class to itself
- Useful for hierarchical structures (e.g. a family tree)
- Here, a person can be the parent of 0+ children, and a Person is the child of 2 parents
- In addition to an association name, now we have roles at each end: this helps us give meaning to the multiplicities

## Dependency

![[Untitled 8 16.png|Untitled 8 16.png]]

- Dashed line, optionally with <<stereotype>>
- Means a class uses another class, without storing a reference
- Typically comes from argument/return types

## Draw JCF class diagram

Class hierarchy

- Abstract class `AbstractCollection` is the base class for two further abstract classes: `AbstactList` and `AbstractSet`
- `AbstractSet` has two concrete (i.e. not abstract) classes `HashSet` and `TreeSet`

Interface hierarchy

- Interface Collection is extended by `List` and `Set` interface
- Furthermore, interface `SortedSet` extends `Set`

Interface implementations

- `AbstractCollection/List` implement `Collection/List`
- `HashSet` implements `Set`
- `TreeSet` implements `SortedSet`

![[Untitled 9 15.png|Untitled 9 15.png]]

## Notes

![[Untitled 10 15.png|Untitled 10 15.png]]

Notation

Dog-eared rectangle with any text you like inside, linked to the annotated element through a dashed line with no arrowheads

Meaning

- Just a comment on any part of the diagram
- Useful for things that go beyond UML’s capabilities

## Packages

![[Untitled 11 13.png|Untitled 11 13.png]]

Notation

- Tabbed folders, with elements inside
- Elements may have their simple name, or the fully qualified Package::Element name.

## Extracting UML diagrams from a system

Suppose that you are asked to use UML to document some mechanism of your system, What to do?

1. Find the core class that implements the main part of the mechanism
2. Identify the various collaborations that are required to complete this mechanism
3. For each collaboration, identify the classes and interfaces that participate and their relationship
4. Use scenarios to “walk through” the mechanism. This will help you to discover parts of your module that were missing, and parts that were simply wrong
5. Be sure to populate these entities with their contents. For classes, start by getting a good distribution of responsibilities. Over time, turn these into fields and methods

## UML to Code

![[Untitled 12 13.png|Untitled 12 13.png]]

![[Untitled 13 12.png|Untitled 13 12.png]]

## Interaction Diagrams

- Objects don’t just sit idle: they interact with one another by passing messages
- There are two ways of reasoning about interactions:
    1. how messages are dispatched across time (sequence diagrams);
    2. structural relationships between objects in an interaction and how messages are passes within the context of that structure (collaboration diagrams).
- In this module we will only consider detail sequence diagrams. You will see collaboration diagrams next year.

## Sequence Diagrams: Adventure Games

![[Untitled 14 12.png|Untitled 14 12.png]]

- First, we draw the objects and start the lifelines
- Objects have a name and type, and are underlined
- We have a Game g, a Parser p, and a CommandFactory cf
- We will build up this diagram and show the notation

![[Untitled 15 9.png|Untitled 15 9.png]]

- The leftmost object usually starts the interactions
- g asks p to produce a Command for “look north”
- p replies back with the “cmd” value

![[Untitled 16 8.png|Untitled 16 8.png]]

- Activations (method calls) can be nested
- During the getCommand activation, p asks cf to create a Command based on the “look” discriminator
- cf replies back with the “cmd” value

![[Untitled 17 8.png|Untitled 17 8.png]]

- Objects can be created in the middle of the sequence
- This is done through a special “new” message
- Here, cf creates a new LookCommand, lc

![[Untitled 18 8.png|Untitled 18 8.png]]

- p adds words to lc before returning it
- g invokes the act method on lc the execute it
- lc returns an “ended” flag

![[Untitled 19 8.png|Untitled 19 8.png]]

- Fragments can be used for modelling control structures: “opt” (if), “alt” (if … else), “loop” (while)
- Here we use a fragment for conditionally ending the game
- This is g invoking itself: notice the nested activation rectangle and the usual dashed return arrow
- During the end activation, we destroy lc (just as an example: in Java, the garbage collector will do it for you)

Draw a UML sequence diagram for the following scenario. The system requests an `EmailEncrypter` object to encrypt a message. This object manages the whole of the process as follows

1. It logs the message receipt in MIME format using logMessageReceipt on a Logger object
2. It validates the MIME structure using a MimeParser
3. It gets a key for the addressee from a KeyManager
4. It sends the encrypted message using an EmailSender object.
5. It logs the message that was sent with the same Logger object as for 1.

## Solution

![[Untitled 20 8.png|Untitled 20 8.png]]