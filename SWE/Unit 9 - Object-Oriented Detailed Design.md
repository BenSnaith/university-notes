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

