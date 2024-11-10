# Inheritance III

## Goals for this lecture

- Reuse interfaces through inheritance
- Combine interfaces through multiple interfaces
- Add concrete methods to interfaces safely via default methods
- Detect and fix conflicting default methods and interfaces
- Use @since, @deprecated and @Deprecated to document changes in programs
- Understand the concept of semantic versioning for signaling changes in your software

## First (BAD) solution: new interface

```Java
public interface MoveableDrawable {
	void draw(GraphicsContext gc);
	void move(int dx, int dy);
}
```

- Here is a new interface, with an additional method
- Shapes that are moveable could implement both Drawable and MovableDrawable
- ==Problem 1: you are repeating the declaration of the draw methods (breaks Don’t Repeat Yourself — DRY)==
- ==Problem 2: breaks reuse and extensibility==

## Second Solution: Interface Inheritance

```Java
public interface Drawable {
	void draw(GraphicsContext gc);
}

public interface MovableDrawable extends Drawable {
	void move(int dx, int dy);
}
```

- Now we explicitly say that a MovableDrawable “is-a” Drawable which has one more method: `move`
- We avoid code repetition
- We can pass a `MovableDrawable` to something expecting a `Drawable`: we can reuse existing code

## Using `MovableDrawable`

Approach 1: make everything movable in one go

- We make `Shape` and `MyPolygon` implement `MovableDrawable`
- Now everything must also implement `move`
- We can change `Launcher` to use `MovableDrawable`

Approach 2: make only some things things movable

- We could make only some shapes movable (e.g Circle)
- Then only these classes would implement `MovableDrawable`
- `Launcher` could use `instanceof` to see what is available

## Approach 1: Make everything movable now

```Java
public abstract class Shape implements MovableDrawable { ... }
// ... add move() method to Circle, Rectangle, Ellipse

public class MyPolygon extends java.awt.Polygon implements Polygon { ... }

public class Launcher {
	private MovableDrawable[] drawables; // replaces shapes[]
	private void draw() { ... }
	
	for (MovableDrawable md : drawables) {
		md.draw(gc);
		md.move(rnd.nextInt(50), rnd.NextInt(50));
	}
}
```

- We move everything to `MovableDrawable` in one go
- We are making one large, impactful change in the code
- On the other hand, the `Launcher` doesn’t need downcasts

## Approach 2: some things are movable

```Java
public class Circle extends Shape implements MovableDrawable {
	...
	@Override
	public void move(int dx, int dy) {
		...
	}
}
public class Launcher {
	private Drawable[] drawables; // replaces Shape[]
	private void draw() { ... 
		for(Drawable d : drawables) {
			d.draw(gc);
			if (d instanceof MovableDrawable md) {
				d.move(rnd.nextInt(50), rnd.nextInt(50));
			}
		}
		...
}
```

- We only mark sone types as movable: Launcher checks with `instanceof` and downcasts if it can move

## Example in Java: Collections and Iterable

- `Iterable` is something you can loop through
    - in `for(a : b)`, the `b` must be `Iterable`
- `Collection` is that, and more: you can get the size, check if it is empty, and many other things
- `Interable<T>` means “an `Iterable` that produces elements of type T when you loop through”

## Third Solution: Combining Interfaces

- You could also use separate interfaces, and then combine them with multiple interface inheritance

```Java
public interface Drawable {
	void draw(GraphicsContext gc);
}

public interface Movable {
	void move(int dx, int dy);
}

public interface MovableDrawable extends Drawable, Movable { ... }
```

- Now we can have some things that can be draw, some things that can be moved, and some that can be both draw and moved

## Extending interfaces with default methods

```Java
public interface Movable {
	void move(int dx, int dy);
	default void move(int d) { move(d, d); }
}
```

- Suppose we wanted to add a new convenient method to Movable for when we want to move the same distance across the X and Y axis’
- If we just added move(int d), we’d have to update all Movable implementation
- Java 8 allows us to provide default method bodies so we do not break existing classes implementing the interfaces
- Interfaces have no state, so default methods can only use arguments, local variables, and other methods

## Documenting additions across versions

```Java
public class YourClass {
	/**
	 * New feature that was added recently
	 * 
	 * @since 1.1
	 */
	 public void doSomethingNew() { ... }
}
```

- Adding new methods is quite common
- If you’re only coding for yourself, you can do what you want
- If you’re developing a library that you will share with others, they need to know when you added this method
- This way they can decide if they want to keep using their old version, or update to your version
- Javadoc @since tag takes the version number when it was added

## Documenting deprecated code

```Java
public class YourClass {
	/** 
	 * Old feature that you should stop using
   * 
	 * @deprecated Please use {@link \#doSomethingNew()};
   * This method will be removed in the future
	 */
	 @Deprecated public void doSomethingOld() { ... }
}
```

- @deprecated is a Javadoc tag that you can use to explain what you should use instead (e.g. by linking to it using @link)
- Here `\#doSomethingNew()` points at the method of the same name in the name class
- @Deprecated is a Java annotation which tells the compiler to produce warnings to anyone still invoking this method
- You can deprecate an entire class as well
- All Javadocs have a “Deprecated” section

## Semantic Versioning (I)

Problem

- How do you number the versions of your software?
- What does it mean to go from 0.1 to 1.0, or to 1.1 from 1.0?
- There are many ways to do it
- One way is called semantic versioning, where we give different meanings to the various parts of the version number

Basic Rules

Given a version number MAJOR.MINOR.PATCH, increment

- MAJOR when making incompatible changes
- MINOR when adding features without breaking code
- PATCH when making backwards compatible fixes

Reset the following numbers to 0 after the increment

## Semantic Versioning (II)

- Imagine that you are in version 1.1.0 of your image processing library, and you have many developers using your library, and you have many developers using your library: you need to keep them informed
- What would be the version number in each of these cases
    1. You revamped the design of the system
    2. You added a new class that doesn’t require implementation
    3. You fixed a bug

# Responsibility-Driven Design

## Goals for this lecture

- Understand the principles behind responsibility-driven design approach
- Be aware of role stereotypes for guiding the identification of responsibilities
- Use Candidate-Responsibility-Collaboration cards to elicit candidate concepts
- Identify the various object collaboration styles, and their pros and cons

## Beyond coding

- Remember the client-server model: a system is a collection of objects talking to each other.
- In the past few weeks, we have been focusing on how to implement OO concepts in Java
- However, we need to come up with a good design that we can code first
    - Which classes will we need
    - What are their responsibilities
    - How will they work together with each other?
- Let’s return to this idea of “system = collaborating objects” and look into ways to guide our design

## Responsibility-driven design (RDD) principles

- Originally proposed by Wirfs-Brocks and Wilkerson (1989)
- RDD sees systems as communities of collaborating objects
- Each object has its own responsibilities to accomplish
- THREE PRINCIPLES:
    - Maximise abstraction
        - Hide distinction between data and behaviour
        - Objects responsible for “knowing”, “doing” and “deciding” things, rather than “has method X” or “has field Y”
    - Distribute behaviour
        - Promote a delegated control architecture
        - Objects should be smart, not just bundles of data
    - Preserve flexibility
        - Allow objects to change their implementation details

## Object roles

- An object will usually take one or more roles: I am a “Lecturer” and also a “Researcher”
- A role is a set of responsibilities (performing tasks, organising other objects or knowing some things)
- We can identify several role stereotypes:
    - Information holder: knows and provides information
    - Structurer: maintains relationships between objects
    - Coordinator: mechanically reacts to events
    - Controller: makes decisions and directs others’ actions
    - Interfacer: transforms information and requests between different parts of a system
    - Service Provider: performs work on demand
- Class will typically follow 1-2 role stereotypes

## Usual process

- You will receive a number of stories that your system must support
- Based on those stories, you will come up with an initial set of candidates (could be classes/interfaces/subsystems)
- You iterate a number of time, refining your candidates
- Map to UML, while refining a number of times again
- Map to Java, and refine even more times
- Write tests and improve your software, keep refining your design

In general, you will never be done designing: your design will always be evolving as the needs of the system change

## User story example

- Your system must be able to simulate a day in an automated distribution center, which starts with a certain queue of orders for certain articles
- The system takes each order, assigns it to a free packing station, and asks robots to bring the items from the relevant storage shelves to the packing station
- The station takes some time to place the items in a box, which is then given to the shipping company, Robots have batteries, and need to go to their charging pod when necessary
- The simulation runs in a loop: each “tick” of the simulation makes all entries operate for one “tick” (moving, packing, sending things). The distribution center is divided into a grid of cells, containing robots, shelves, or charging pods

## Where do we start?

- First, we need to find the various objects in the previous story
- We can look for objects that support
    - System behaviours
    - Architecture
    - Performance requirements
    - Software mechanisms and machinery
- We want the key concepts in the domain: how does the software see things in the “real world”?
    - In banking: Account, Currency, Transaction
    - In a robotic warehouse: Robot, DistributionCenter, Order
- Two main types of domain objects:
    - Entity objects that have a clear identity (e.g. robot)
    - Value objects that do not (e.g. Direction, Color, Temperature)

## What to look for?

Look for things that represent

- The work the software performs
- The things the software is connected to
- The information flowing through the software
- The decision-making, control and coordination activities
- Ways to structure and manage groups of objects
- Representation of real world things

## Objects in the example

- Work performed: Simulator
- Things connected to: ShippingCompany, GraphicalInterface
- Information flowing through system: Order, Article
- Decision-making: OrderManager, RoutePlanner
- Structuring the objects: OrderQueue, Grid
- Representation of real world things: Building, Robot, ChargingPod, PackingStation, Shelf

## Characterising the candidates

- We have a rough idea of which concepts we will have: now we need to explain what they should do
- For this we can use CRC (Candidate-Responsibility-Collaborator) cards
- Pieces of paper with two sides, front has purpose and role stereotypes, back has responsibilities and collaborations

## Writing the purpose (I)

- The front of the cards has its “purpose”: 1-2 sentences summarising what the class does, and perhaps 1-2 sentences with some useful detail
- The purpose is usually related to the role stereotypes
- Some examples:
    - Information holder: “knows name and address”
    - Structurer: “organises entities into a grid”
    - Coordinator: “propagates to ticking of the simulation”
    - Controller: “assigns orders to packing stations”
    - Interfaces: “displays building and takes in user input”
    - Service provider: “computes shortest route between points”
- If you notice your class has too many roles / purpose is longer than this, break it up!

## Writing the purpose (II)

- Structurer: “organises orders into pending / assigned / completed”
- Controller: “assigns orders to packing stations”
- Extra detail: “orders are processed in a first-come-first-server manner”

## Writing the responsibilities (I)

- Again the stereotypes will usually guide you on what to put
- Sometimes we will come up with additional responsibilities beyond the strict stereotypes (e.g. the statistics tracking in the previous card)
    - However, this may also suggest we need a OrderStatistics class, as it’s slightly outside what an OrderManager would do
    - It could be and blend of an information holder / services provider, for instance: it’s only 2 roles so not too much
- Notice that a responsibility is much more than a field
    - A responsibility is not “`getName()` / `setName()` / `getAddress()` / `setAddress()`”, but rather “knows name and address”
    - Likewise, it’s not “`assignStation()` / `getStationForOrder(…)`”, but rather “assigns orders to packing stations”
    - This makes CRC cards much easier to write than class diagrams at first

## Writing the responsibilities (II)

- “Knows which orders are pending and completed”
- “Assigns orders to packing stations”
- “Reports statistics about productivity” : we found this one out as we went, maybe needs a new class

## Writing the collaborations

- To check collaborations, you have to think about specific stories in your system. Grab the OrderManager card and think aloud:
    - The order manager takes an order to be added to the queue, then it asks the packing stations in the building if they are free. If a packing station is free, it will assign it an order
    - The order manager will be told by the packing station that the order is completed, and move it from assigned to completed. It will then track how long it took in its statistics
- Whenever you see and object relying on another, it is collaborating with it:
    - Later in UML/Java, this usually means that the object will need to keep a reference to the other object in some form
    - This also means that the object receiving the requests will need to have methods to support this collaboration
- Take the cards as you go around the story, and physically place them close to their collaborators!

## Collaboration styles: centralised

- Imagine that you wrote the system so that the Simulator did everything: rest of classes are just information holders
- Simulator would become huge and unweildly, and it would be very difficult to reuse the other classes without it.

## Collaboration styles: distributed

- What if you let the Simulator just talk to the OrderManager and Building, as a coordinator
- Then OrderManager and Building can have more smarts in them, and the logic is better distributed
- PackingStation can take on some smarts, too

## Collaboration styles: dispersed

- Wirfs-Brock talks about the other extreme, when a decision is spread across many objects
- In this case, It’s hard to track exactly when something happens, and some participants add very little value
- The chain is also very hard to change if not careful

## Back to the collaborations

- We noticed that OrderManager had to ask the Building for the available PackingStations
- Noted down the collaborator on the card

## Overall Summary

- RDD sees the system as a community of collaborating objects
- Objects take on responsibilities in the system, usually across some common stereotypes
- CRC cards are a way to come up with a set of objects and specify their purpose, roles, responsibilities and collaborations
- Collaborations can be centralised, distributed or dispersed: generally, distributed is recommended as changes are typically easier to localise and medium-sized smarter objects help to distribute work better than a single big class