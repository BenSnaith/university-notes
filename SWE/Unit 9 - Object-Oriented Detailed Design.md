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

- _Collection_ classes are used to hold the object identifiers (i.e. object references) when 