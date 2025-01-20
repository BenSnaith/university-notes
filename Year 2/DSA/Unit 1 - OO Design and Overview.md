## Unit Objectives.

- Consider basic UML notation for class diagrams.
- Consider some core concepts underlying object-oriented (OO) programming.
- Consider how some core OO concepts can be realized in a Java program.
- Use generic types to define collection classes.

## UML Class Diagrams.

A UML class diagram describes:

- The classes in a software system.
- The attributes (fields) and operations (methods) in each class.
- The static relationships among classes.
- The constraints on the connections among objects

  

![[image 16.png|image 16.png]]

The field `income` in `Person` is constrained to be non-null.

## Class Inheritance: an Example.

Subclasses can inherit from a superclass to foster reuse and avoid duplicating efforts.

```Java
public abstract class Ownable {
	private Person owner;
	
	public Ownable() {
		// detail omitted.
	}
	
	public String getOwnerTel() {
		return owner.getTel();
	}
	
	public void changeOwner(Person newOwner) {
		// detail omitted.
	}
}

class Car extends Ownable {
	// details omitted.
}

class Pet extends Ownable {
	// details omitted.
}
```

![[image 1 5.png|image 1 5.png]]

A `Person` has the ability to own 2 different `Ownable` objects, i.e. `Car` and/or `Pet`

## Class `Person`

A `Person` class can possess up to two ownable objects.

```Java
public class Person {
	private String name;
	private String phone;
	private int income;
	private Ownable[] possessions;
	
	/* Constructor */
	public Person(String name) {
		this.name = name;
		phone = null;
		income = 0;
		possessions = new Ownable[2];
	}
	
	/* @return phone-number */
	public String getTel() {
		return phone;
	}
	
	// Other details omitted.
}
```

## UML Class Diagrams

Typical components in a class diagram include:

- Class (abstract and / or concrete)
- Interface
- Association relation
- Aggregation relation: “has a”
- Composition relation: “owns a”
- Dependency relation: “uses”
- Generalisation relation: “is a”
- Realisation relation: the relationship between a class that implements an interface

## UML Class Diagram: an association relation

![[image 2 5.png|image 2 5.png]]

## UML Class Diagram: aggregation vs composition

![[image 3 5.png|image 3 5.png]]

Aggregation

![[image 4 5.png|image 4 5.png]]

Composition

## UML Class Diagram: a dependency relation

![[image 5 5.png|image 5 5.png]]

![[image 6 3.png|image 6 3.png]]

An `Order` requires a `LineItem` to accomplish its tasks.

## UML Class Diagram: generalisation vs realisation

![[image 7 3.png|image 7 3.png]]

A Generalisation Relation

![[image 8 3.png|image 8 3.png]]

A Realisation Relation

## Depicting Class Relations in UML

![[image 9 3.png|image 9 3.png]]

## Object Orientation: A quick revision.

- An object is a fundamental data entity in a Java program.
- Java programs also manage primitive data such as numbers and characters
- An object usually represents a more complex data concept, e.g. a bank account.

## Objects, Classes and Abstraction

- How an object works and what kind of data items it represents is defined in a class, e.g. `SavingAccount`
- Class ⇒ type (i.e. blueprint)
- Object ⇒ data (i.e. product)

![[image 10 3.png|image 10 3.png]]

- A Java interface acts an an abstraction of a class. WHY?
- Abstraction does not eliminate the details. It simply confines then to the minimum scope necessary.

## Abstraction

```Java
public class Car {
	private String make;
	private String model;
	private String colour;
	private String registrationNumber;
	private String yearOfRegistration;
	
	/* Constructor */
	public Car(String make, String model, String colour,
						 String regNum, String regYear) {
		this.make = make;
		// Other implementation details omitted.
	}
	// Method details omitted.
}
```

## A Java Interface acts as an abstraction of a class

![[image 11 3.png|image 11 3.png]]

## Java Interface: an Example

A client class can interact with, and use, and object without knowing its underlying type.

```Java
public interface BankAccount {
	public abstract String accountCode();
	public abstract float balance();
	public abstract void deposit(float amount);
}

class CurrentAccount implements BankAccount {
	// details omitted
}

class MortgageAccount implements BankAccount {
	// details omitted
}

class main {
	ArrayList<BankAccount> myAccounts = new ArrayList<>();
	// other details omitted
	myAccounts.add(new CurrentAccount<>());
	myAccounts.add(new MortgageAccount<>());
	// other details omitted
	showAllAccounts(myAccounts);
}
```

## Working with Collections: a pre-Java 5.0 Example

```Java
import java.util.ArrayList;
import java.util.Iterator;

public class Auction {
	// This list of lots in this auction
	private ArrayList lots = new ArrayList();

	// Other class definitions omitted...

	// Show the full list of auction lots.
	public void showLots() {
		Iterator itr = lots.iterator();
		while(itr.hasNext()) {
			System.out.println(itr.next());
		}
	}
}
```

## Contents of generic `ArrayList` object for `Lot` objects.

A generic `ArrayList<>` object is instantiated to manage objects of the `Lot` class _only_

  

## Working with Collections: a post-Java 5.0 Example

```Java
import java.util.ArrayList;

public class Auction {
	private ArrayList<Lot> lots = new ArrayList<>();

	public void showLots() {
		for(Lot lot : lots) {
			System.out.println(lot);
		}
	}
}
```

## Modelling a box with multiple compartments

Consider writing a Java class to model a container with multiple compartments

Each compartment is used to store the same type of thing

- How to model a box with multiple compartments
- How to ensure that each compartment stores the same type of object

## Class `Box`

Defining a generic class `Box` for storing and managing other objects.

```Java
import java.util.ArrayList;

public class Box<T> {
	private ArrayList<T> contents;

	public Box() { // Constructor
		contents = new ArrayList<>();
	}

	public void put(T item) {
		contents.add(item);
	}

	public boolean find(T item) {
		return contents.contains(item);
	}
}
```

## Generic Types

- A generic class is a class which stores, operates on, and manages objects _whose type is not specified_ until the class has been instantiated
- A generic class uses type variable(s) to refer to such not-yet-specified object type(s)
- e.g. To define class `Box` for storing and managing other objects

```Java
import java.util.ArrayList;

public class Box<T> {
	private ArrayList<T> contents;
}
```

## Using Generic Types

```Java
import com.snaith.Box;

public class Raffle {
	private Box<Ticket> tickets;
	private Boc<Prizes> prizes;

	public Raffle() {
		tickets = new Box<>();
		prizes = new Box<>();
	}

	// Other class details omitted.
}
```

## Enhanced `for` (aka `for-each` )

- Provides a simple syntax for iterating through a collection of objects

```Java
import java.util.ArrayList

public class Auction {
	private ArrayList<Lot> lots = new ArrayList<>();

	public void showLots() {
		for(Lot lot : lots) {
			System.out.println(lot);
		}
	}
}
```

- General structure

```Java
for(T LHS : RHS) {
	statements
}
```

- The RHS must either be a reference to an object which implements `java.lang.Iterable` or an array.
- The LHS is an element within the collection or array.
- Internally, an enhanced for _relies_ on the use of a `java.util.Iterator` object to go through a collection object or an array element-by-element.