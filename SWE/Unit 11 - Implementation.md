### Unit Objectives

- Learn about the tasks involved in implementation.
- Techniques involved in writing maintainable code.
- What is meant by _defensive programming_ and for to enforce intention.
- What tools are used in software implementation.

### Implementation - What does it involve

Two different views:

- Bennett et al. (2010) wrote:

"Implementation is concerned with the _process_ of building the new system. This involves _writing program code_. developing _database_ tables, _testing_ the new system, setting it up with _data_, possibly transferred from an old system. _training-users_ and eventually _switching over to the new system_."

- Braude & Bernstein (2011) however stated:

"The implementation phase consists of _programming_ which is the translation of the software design developed in the design phase to a programming language. It also involves _integration_, the assembly of the software parts."

- One thing in common is that `implementation` involves constructing a software system based on a design: this involves _writing program code._
- To facilitate the coding process, one needs to consider:
	- Which programming _languages_ to use for developing the required software.
	- Which _software tools_ will be used to support the software development process.
	- How to ensure that the code, though written by different programmers, will be _easy to read, understand, and maintain_.
	- How to effectively _manage changes to programs_ throughout the development process.

### Language Choice

The choice of the programming language depends on the nature of the required software system.

- e.g., JavaScript, CSS, and HTML for _client-side_ web application
- For server side scripting we could use; _PHP, Java SpringBoot, Ruby, Python_.
- Lots of simultaneous, lightweight communications? Maybe _Node.js with websockets_.
- Where a client prefers to use Microsoft products only, the implementation is likely to be _C#_.
- If the tasks require a substantial amount of processing on _tree_ data structures, a _functional programming language_ such as _Lisp, Haskell_ or possibly _Julia_ is likely to be a good choice.
- If a system is expected to perform a lot of efficient _low-level system operations_ and _efficiency_ is paramount, _C_ may be a preferred language choice.
- If the required software system is expected to run on _different platforms_ a language like _Java_ or _Scala_ would be appropriate.

### Writing Classes

- _Class_ names should be _meaningful_, e.g., in the `Agate` example, `CampaignStaff` would be a better class name than `Staff`.
- Avoid using _ambiguous_ or _cryptic_ names such as `Record` or `C1`
- The purpose of each class should be _clearly_ and _concisely_ stated in the documentation comment.
	- _This view is not universally agreed. Some software developers adopt the "comment-free" practice, and opt to achieve clarity by structuring the source code and naming identifiers, variables, etc. in a way that makes the code feel self-explanatory._

### Documenting Methods

- The _purpose_ of each method should be clearly stated in code comments, e.g.:

```java
// Tests whether this date is after the specified date.
public boolean after(Date when)
```

- To facilitate _maintenance_ and _reuse_, it is helpful to specify the following information for methods, especially for the _non-trivial_ ones:

	- Intent
	- Return
	- Exceptions
	- Known Issues
	- Preconditions
	- Post-conditions
	- Invariant

- __Intent__:
	- An _informal_ statement of what the method is intending to do.
- __Return__:
	- The value which the method returns.
- __Known Issues__:
	- Honest statement of what has to be done, defects that have been repaired, etc.
- __Exceptions__:
	- Capture the situations when an _abnormality_ occurred during the _execution_ of the method.
	- Such situations may occur due to __preconditions__ not being met.
- __Preconditions__:
	- What must be true _when_ a method is invoked
	- Conditions on non-local variables, including the parameters, that the method assumes, e.g.:

```java
	private int price;
	// Precondition: reduction > 0
	public void reducePrice(int reduction) {
		price -= reduction;
	}
```

- Verification of these conditions is not guaranteed by the method as it is assumed to be done by the caller.

- __Post-conditions__:
	- What must be true _after_ a method completes successfully.
	- Specify the _effect_ of the method.
	- Specify the value of non-local variables after execution.
	- Notation: `x'` denotes the value of variable x after execution, e.g.:

```java
	private int price;

	// Post-conditions: price' = price - reduction
	public void reducePrice(int reduction) {
		price -= reduction; // = price'
	}
```

### Class In-variants

- _Class in-variants_ specify constraints on __Attributes__ and their relationships. object, e.g.:

```java
public class Time {
	private int hour;    // hour >= 0 && hour < 24
	private int minute;  // minute >= 0 && minute < 60
	private int second;  // second >= 0 && second < 60
}
```

- Even though the value of each attribute in an object might change at runtime, its values must conform to the _class invariants_.

### Java Assertions

- __Preconditions__, __Post-conditions__ and __In-variants__ can be specified in a Java program as __Assertions__.
- _Assertion_ in Java provides a convenient tool for run-time checking.
	- As well as a means for documentations.
- An `Assert` statement typically:
	- Performs a _check_, and
	- Displays a message when the check _fails_.
- An `Assert` statement may also:
	- Throw an exception, and
	- Include file and line info.
- By default, assertions are _ignored_ by the JVM and they are used mainly for _debugging_.
- To _switch on_ assertion checks, a Java program needs to run with the option `-ea` (i.e. enable assertions), e.g.:

```java
	java -ea ArrayRemove
```

- Where `ArrayRemove` is a compilation unit which includes a _main_ method.

_N.B. Do not confuse assert methods in JUnit with `assert` statements in Java. They serve different purposes._

### Object-Oriented Standard

- Naming standards should be agreed early in the project.
- A typical _object-oriented standard:_
	- Classes with capital letters: __Campaign__
	- Attributes and operations with initial lower case letters: `userID`

### Hungarian Notation

- The __Hungarian Notation__ is typically used in __C__ or __C++__.
- Identifiers are prefixed by an abbreviation to show the type of the `variable`
	- `b` for boolean: `bOrderClosed`
	- `i` for integer: `iOrderLineNumber`
	- `btn` for button: `btnCloseOrder`

### Underscore Convention

- Another convention commonly used for _column names_ in databases uses _underscores_ to separate parts of a name instead of capital letters, e.g.:

```SQL
Order_Closed
```

or in Postgres...

```
order_closed
```

This convention makes it easier to replace the underscores with spaces to produce meaningful column headings in reports.

### Documentation Standard

- The one who wrote a piece of code is unlikely to be the one having to maintain it in future. Hence, it is important that code is _readable_ to facilitate maintenance.
- _Good documentation is important_ to facilitate maintainability and re-usability of any written code.
- Java has well-defined _documentation standards_ which should be adhered to if coding in __Java__ (Javadoc).
- Use _XML_ tags if coding in __C#__.
- Many _IDEs_ include features for generating __Javadoc__ from comment automatically.

### Naming Conventions For...

- __Packages__: all lower case.
	- _internal use_: prefix with name of product, e.g.: `cwkl.shapes`
	- _for distribution_: prefix with domain name, e.g.: `uk.ax.aston.cs`

_The word in between each full stop corresponds to the name of a __folder__ in a file system._

- __Reference Types__ (i.e. classes/interface names): start with capital, then mixed case
	- _classes_: use a noun describing an instance, e.g.: `MyShape`.
	- _interfaces_: either a noun, e.g. `Observer`, or an adjective, e.g. `Cloneable`.
- __Methods__:
	- Active methods (i.e. __Mutator Methods__) usually start with verb, e.g. `changeSize()`
	- Getter methods (i.e. __Accessor Methods__) named by return value, e.g. `length()`, or with a '_get_', e.g. `getLength()`.
- __Fields and Constants__:
	- __Static Final__ fields (i.e. __Named Constants__): all capitals, e.g. `EQUALS_TOLERANCE`, `INITIAL_VALUE`.
- __Parameters__: some capitalisation as method names,
	- e.g. `newSize`
	- Choose fitting, yet succinct names, for parameters.
	- Keep them consistent if they have the same meaning.
- __Local Variables__: same capitalisation as method names, e.g.: `count`
	- Always use _meaningful_ names good for achieving readability.
	- Except for routine cases, e.g. `for(int i = 0; ...; i++)`

### Documentation Comments

- May contain a number of special __tags__, e.g.:
	- `@author`
	- `@version`
	- `@see` hyperlink to documentation of another member, class
	- `@param` every method parameter should have one
	- `@return` describes the return value of a method.
	- `@throws` describes potential exception propagation.

- Start with `/**` and end with `*/`

### Defensive Programming

- _Defensive Programming_ is a programming technique which seeks to minimise program errors by _anticipating_ potential errors and _implementing_ code to handle them.
- Techniques of defensive programming include:
	- Various error handling techniques.
	- Buffer overflow prevention.
	- Enforce intentions.

###### Error Handling Techniques

- _Wait for a legal data value_: typically used when getting data from an external source, e.g. user interface.
- _Set a default value_: typically used to ensure the continuity in execution of a (critical) process.
- _Use the previous result_: typically used when a constant stream of input is expected as a regular interval.
- _Log error_: Store error info for later use or analysis.
- _Throw an exception_.
- _Abort_: typically used in operations where illegal data may lead to a fatal consequence, hence the system must be aborted and reset.

###### Buffer Overflow Prevention

- Some languages (e.g. __C__ and __C++__) permit data to be written to memory and even the data require more space than what was declared in the code, _so long as_ the required space does not exceed the space allocated to the program (e.g. through the `malloc` function).
- This may lead to _overwriting_ existing data kept in the memory.
- Such overwriting, when exploited, may lead to a _security breach_.
- _Buffer overflow prevention_ attempts to prevent buffer overflow by checking the size of variables.

###### Enforce Intention

- Use suitable programming constructs to enforce the intended design or use a piece of code.
- Use keywords such as `final` and `abstract` to enforce coding intentions, e.g.:

```java
public final class String {...}
public abstract class AbstractList {...}
```

- Make constants, variables and classes as _local_ as possible e.g.:

```java
for(int i = pos; i < array.length - 1; i++) {...}
```

- Use the __Singleton__ design pattern if only one instance is expected from a class.
- Define attributes and operations as `private` if they are not intended to be accessible by other classes.
- If a class is expected to be _extended_ by other classes, make attributes `protected` and define _accessor methods_ for accessing their values.
- If a method is not expected to be used by classes in another package, do not use the `public` keyword to specify its _visibility_.
- Use _enumerate types_ to enable a variable to be assigned with a predefined set of constants, e.g.:

Rather than:

```java
int tShirtSize = 1
```

We define an _enum_ type in Java to model permissible sizes for a T-shirt:

```java
public enum Size {
	XS, S, M, L, XL, XXL
}

Size tShirtSize = XS;
```

- Consider introducing new classes to encapsulate legal parameter values so as to prevent bad data, e.g.: 

Instead of:

```java
determineRoadTax(String vehicle)
```

We use:

```java
determineRoadTax(Vehicle vehicle)
```

Where class `Vehicle` has various _factory methods_ to create the permissible types of vehicles, e.g.:

```java
Vehicle createCar() {...}
Vehicle createLorry() {...}
Vehicle createMotorbike() {...}
```

### Software Implementation Tools
###### Modelling Tools

- Many interactive development environment (IDEs) _support UML_.
	- However, the notations used might not always strictly follow the current standard.
- Some modelling tools support _automatic generation_ of program code (in __Java__, __C++__, and __VB__) from the models e.g. __Visual Paradigm__.
- Some also support _reverse engineering_ of code (i.e. generating a design model from existing code).
- Some of them map classes to a _relational database_.

###### IDEs (Integrated Development Environments)

- Manage files in a project and the dependencies among them.
- Link to __configuration management tools__.
- Use compilers to build the project, _only_ recompiling what has changed.
- Provide various facilities such as _debugging_, _refactoring_, _auto-layout_, _documentation generation_, etc.
- May include a _visual editor_ for GUI building.
- Con be configured to link to third party tools.

###### Configuration Management Tools

- Include elements of __version control__ - to _compare_ source code so as to assist in resolving potential __conflicts__.
	- Though configuration management is more than just version control.
- Maintain a record of _file versions_ and the _changes_ from one version to the next.
- Record all the versions of software and tools that are required to produce a repeatable software __build__.
- __Dockerfiles__ are a (fairly rudimentary) form of configuration management.

###### DBMS (Database Management Systems)

A DBMS typically comprises:
- Server System.
- Client Software (administration interfaces, ODBC and JDBC drivers)
- Tools to manage the database and carry out performance tuning.
- Tools to make compiled classes persistent so they can be used with object DBMS.
- Large DBMS, such as __Oracle__, come with many tools, even their own application server.

###### Application Containers

- Web Containers, e.g. __Tomcat__ (__Java__), __Flask__ (__Python__).
	- Runs servlets and small-scale applications
- Applications Servers, e.g. __Glassfish__, __WebSphere__, __nginx__, __Apache Web Server__.
	- Provide a framework in which to run large-scale, enterprise applications.

###### Installation / Deployment Tools

- e.g. __GitLab CI/CD__, __AWS CodeDeploy__, __Jenkins__.
- Automate extraction of files from an archive and setting up of configuration files and registry entries.
- Some maintain information about dependencies on other pieces of software and will install all necessary packages.
- Uninstall software, removing files, directories and registry entires.

