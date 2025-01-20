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
7. Implement operations that perform the responsibilities and collaborations in the pattern.