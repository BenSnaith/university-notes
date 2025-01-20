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
- To improve a design by breaking up long sequences of script and method calls into classes.

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
	- Move a field or method to a superclass of its declaring class or (in the case of methods) declares the method as abstract in the superclass.
- __Push Down Field__
	- When a field is used by some subclasses only, but not all subclasses, move the field to those subclasses which use that field.
- __Push Down Method__
	- When there is a method in a superclass that is relevant to only some of its subclasses, move that method to those subclasses.
- __Extract Subclass__
	- When there is a feature in a class that is applicable to some instances only, create a subclass for that class and move the feature to it.
- __Extract Superclass__
	- Make a new class from the common field(s) and method(s) in a set of existing classes, with the extracting classes becoming the direct subclasses of the new class.
	- Extract a common class from a set of sibling types which has the same subset of methods. The selected sibling types become direct subclasses of the new class after applying the refactoring.
- __Extract Interface__
	- Make a new interface from an existing class, with the class becoming one which implements the new interface.
- __Extract Hierarchy__
	- Make a class design more flexible by introducing or extending inheritance relationships.