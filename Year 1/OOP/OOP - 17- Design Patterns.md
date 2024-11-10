## What is a design pattern?

Christopher Alexander (A Pattern Language, 1977)

Each pattern describes a problem which occurs over and over again in our environment, and then describes the core of the solution to that problem, in such a way that you can use this solution a million times over, without ever doing it the same way twice.

Concept

- A common solution to a common problem
- Above quote is about architecture, not programming
- Design Patterns, Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides

## How do we describe a Pattern?

Every pattern has four main parts:

- Name: one or two words that capture the general concept. We can build a vocabulary out of these, for our discussions and documentation
- Problem: when show we apply this pattern? There may be a certain context or some conditions when it makes sense
- Solution: what are the elements involved, what are their responsibilities, and how do they collaborate towards the solution?
- Consequence? what are the pros and cons that we need to balance

## What types exist?

Criteria

- Purpose: creational, structural and behavioural
- Scope: organising classes, or objects

![[Untitled 52.png|Untitled 52.png]]

## Some caveats about design patterns

If you have a hammer, everything looks like a nail…

- You should only apply patterns when it makes sense!
- Don’t use patterns just for the sake of using patterns

Patterns depend on context

- Available patterns depend on the programming language
- For instance, in the Scala programming language you don’t need the Singleton pattern, you can just write `object MyObject { … }`
- Many patterns have several ways of being used
- Many patterns have also several ways of being coded
- In this module we will focus on Java

## Pattern Abstract Factory: Problem

Provide a way to create families of related objects without specifying their concrete classes

![[Untitled 1 30.png|Untitled 1 30.png]]

## Abstract Factory: Motivation

- Suppose that we are building a library for doing GUIs, with concepts like Window or Button
- We want to support multiple operating systems, so we will need to have Windows/Mac/Linux versions.
- We want to allow developers that use our library to write one program, and have it work everywhere

![[Untitled 2 28.png|Untitled 2 28.png]]

## Abstract Factory: Participants

- AbstractFactory:
    - Specified methods for creating the various types of abstract products in the family
- ConcreteFactory (MacFactory, WindowsFactory):
    - Creates the concrete products
- AbstractProduct (Window, Button):
    - Specified methods for the products
- ConcreteProduct (MacWindow, MacButton, WindowsWindow, WindowsButton):
    - Implements a product for a certain family
- Client:
    - Uses only the abstract factory / products

## Abstract Factory: Consequences

Pros

- Isolates concrete classes: the client only works with the abstract product. For the GUI, the user of our libraries never deals with “Windows” components, just “our” components.
- Changing product families is easy: swap the concrete factory
- Promotes consistency: since everything is created through the factory, there’s no risk of mixing products from families

Cons

Adding a new kinds of product is difficult: if we add a product (e.g. Slider), we need to add it to all the families we have (e.g. Windows, Mac and Linux).

## Abstract Factory: Details

Where does Client get the factory from?

It’s quite common for the factory to be a Singleton (one object shared across the program). We’ll discuss this later.

How do we pick this concrete factory?

- We could have a function that creates the right one based on the detected OS
- We could distribute OS-specific versions of our library, which only have the parts needed for that OS, and have the concrete factory hard-wired
- There could be a configuration file that tells our library which one to instantiate

## Pattern Factory Method: Problem

It is a creational pattern that uses factory methods to deal with the problem of creating objects without having to specify the exact class of the object that will be created Define a method for creating an object, but let subclasses decide which class to instantiate

![[Untitled 3 26.png|Untitled 3 26.png]]

## Factory Method: Motivation

- Suppose we are implementing a “Wacky Races” car race game but each of the cars is different in the way it looks and the way that it behaves
- The “Mean Machine” always gets setbacks and loses
- The “Crimson Haybaler” is a plane so moves up and down as well as forward
- The “Pink Pussycat” moves only forwards, no setbacks

## Factory Method: Solution

![[Untitled 4 23.png|Untitled 4 23.png]]

## Factory Methods: Participants

- Product (WackyRacer):
    - Defines the method in the objects created by the factory method
- ConcreteProduct (MeanMachine, PinkPussycat, CrimsonHaybaler):
    - Implements the methods listed in the Product
- Creator (WackyRacerFactory):
    - Defines the factory method, which returns a Product object
    - May call the factory method to create the Product objects it needs
- ConcreteCreator (MeanFactory, PinkFactory, HayBalerFactory):
    - Implements the factory methods in the Creator

## Factory Methods: Consequences

Pros

- Creator logic only needs to work with abstract products (WackyRacer), without knowing about the specific subtype

Cons

- Creating a particular product always requires subclassing the Creator

## Pattern Singleton: Problem

Ensure a class has only one instance, and provide a global point to access it

![[Untitled 5 23.png|Untitled 5 23.png]]

## Singleton: Motivation

Some motivations

- You want to create a single log file from a Logger class, which is accessible from everywhere in your application
- Your application may need a global GadgetRegistry for make Gadget objects available for everyone by key: there should only be one
- Your webserver needs to have access to the ThreadPool that splits work across your CPUs: there should only be one

## Singleton: Solution with eager initialisation

```SQL
public class Logger {
	private static field Logger _INSTANCE = new Logger();

	// prevents others from creating a Logger
	private Logger() { /* ... */ }

	public Logger getInstance() {
		return _INSTANCE;
	}
}
```

This will create the logger as soon as anyone mentions the Logger class (even in a simple import). Sometimes even that is too soon.

## Singleton: Solution with lazy initialisation

```SQL
public class Logger {
	private static Logger _INSTANCE;

	// prevents others from creating a Logger
	private Logger() { /* ... */ }

	public Screen getInstance() {
		if (_INSTANCE == null) {
			_INSTANCE = new Logger();
		}
		return _INSTANCE;
	}
}
```

This will create the logger the first time `Logger.getInstance()` is called. This is know as lazy initialisation.

## Singleton: Consequences

Pros

- Controlled access to the sole instance
- Singleton can be subclassed, and application can be reconfigured accordingly
- We can actually have more than one instance in the future if needed: `getInstance()` could be tweaked further

Cons

- Singletons can complicate testing, as they are “hidden dependencies” of our classes and are difficult to “fake out”
- Sometimes its better to use the Dependency Injection design pattern: just pass the Screen to whoever needs it
- There are dedicated libraries for DI, e.g. Spring or Guice

## Adapter: Problem and Motivation

Problem

Convert the set of methods available in a class to the methods that are expected by the clients

Motivation

- Suppose we are writing an application that includes a ListView that will be used to format arrays of data as text to be printed. The data can be objects of any class
- For an array of names and cities, we want to number the list and put city name after the number.
- For an array of Module objects, we want to format the data as module core followed by module name followed by the number of credits

## Adapter: Solution

![[Untitled 6 19.png|Untitled 6 19.png]]

## Adapter: Participants

- Client (Application):
    - Uses objects of the Target type
- Target (ListView):
    - Specifies the methods that we want
- Adapter (Adapter<T>):
    - Uses the methods in Adaptee to implement the methods in Target
- Adaptee (String[], Module[]):
    - Has methods that needs to be adapted

## Adapter: Consequences

Pros

- We can take advantage of existing libraries or classes without having to conform to their method names
- The same Adapter could adapt the Adaptee itself, or a subclass of the Adaptee

Cons

- If the Adapter creates the Adaptee, using an Adaptee subclass requires changing the Adapter
- Instead, we could have the Adapter receive the Adapter through the constructor — someone else will have to decide which Adaptee to use

## Decorator: Problem

We want to add additional responsibilities to an object dynamically, without using an interface

![[Untitled 7 18.png|Untitled 7 18.png]]

## Decorator: Motivation

- We are writing an input/output library, and we want to support reading bytes from files/network connections, with/without speed statistics, with/without speed statistics, with/without checksum calculation.
- Supporting these with inheritance would need 16 classes!
- Doing everything in one class with flags would result in a large, complicated class with bad cohesion

## Decorator: Solution (Java file I/O)

![[Untitled 8 17.png|Untitled 8 17.png]]

## Decorator: Participants

- Competent (InputStream):
    - Defines the methods for objects that can have responsibilities added dynamically
- ConcreteComponent(FilterInputStream, BufferedInputStream):
    - Implements the methods in Component
    - Can have additional responsibilities attached to it
- Decorator (skipped in this example):
    - Intermediate subclass between Component and ConcreteDecorator which adds a reference to a Component
- ConcreteDecorator (FilterInputStream, BufferedInputStream):
    - Adds responsibilities to the Component

## Decorator: Consequences

Pros

- More flexible than inheritance: we can add and remove responsibilities during execution
- Avoids having large classes with many features

Cons

- Lots of little objects in the system, which all look alike: this can make it more difficult to lean the system and debug it

## Pattern State: Problem

Allows an object to change its behaviour when its internal state changes, as if it had changed class

![[Untitled 9 16.png|Untitled 9 16.png]]

## Pattern State: Motivation

- Suppose that we are modelling a greeter who is alert at first but over time gets bored and finally gets tired
- We are writing a simulation of an Elevator, which can be in several states: opening, open, closing, closed

## State: Solution

![[Untitled 10 16.png|Untitled 10 16.png]]

## State: Participants

- Context (Greeter):
    - Defines the methods of interest to clients
    - Refers to an instance of a State implementation
- State (GreetState):
    - Defines the methods associated with a particular state
- ConcreteState (AlertGreeter, BoredGreeter, TiredGreeter):
    - Implements the methods of a particular state

## State: Consequences

Pros

- ConcreteState subclasses can replace having long if-elses in all the methods which depend on the state
- State transitions are much more explicit
- New states can be easily added as new impl. of State

Cons

- More small objects to manage

## Strategy: Problem and Motivation

Problem

Define a family of algorithms, and make them interchangeable, Clients can pick and algorithm within that family

Motivation

- In your game, you want to have an “easy”, “normal” and “hard” AI. Enemies will have the same basic behaviour, but they will take a different approach to decide where to go
- In your robot, you want to support different ways of estimating the distance to your goal, e.g. straight line distance, Manhattan distance, or one that takes into account the observed terrain.

## Strategy: Solution

![[Untitled 11 14.png|Untitled 11 14.png]]

## Strategy: Participants

- Strategy (EnemyAI):
    - Defines the methods for all the supported algorithms
- ConcreteStrategy (EasyEnemyAI, NormalEnemyAI, HardEnemyAI):
    - Implements the methods in the Strategy
- Context (Enemy):
    - Keeps a reference to a ConcreteStrategy
    - Relies on the ConcreteStrategy in its methods
    - May provide accessors to Strategy

## Strategy: Consequences

Pros

- Clearly defines a family of related algorithms
- Provides an alternative to subclassing
- Eliminates conditionals (e.g. “if in easy mode, do X”)

Cons

- Communication overhead: Strategy needs to call Context accessors to fetch the information it needs
- More objects!