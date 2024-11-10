## 500 Principle from Smalltalk

1. Everything is an object
    1. An object stores data
    2. An object can accept requests to do things
2. Programs = objects that message each other
    1. fido.bark(): we ask the “fido” object to “bark”
3. An object has its own memory, made up of other objects
    1. A Kennel object will contain Dog objects
4. An object has a type (i.e. is an instance of a class)
    1. The class is the “blueprint” for all its objects
5. All objects of a type can receive the same messages
    1. All Dog objects can be asked to “bark”

## Another definition (Grady Booch)

Objects are composed of three things:

- identity (a unique address in memory)
- state (properties which can change in value)
- behaviour (things you can ask it to do)

In this module, we will talk about how to:

- Break down a problem into objects (analysis)
- Decide how to arrange the objects (design)
- Write the code for the objects (implementation)
- Try to find problems in the objects (testing)

## Some requirements

Design an object oriented application to meet the following requirements

- We want an application which displays a light
- The light uses a timer to flash on and off at regular intervals
- We must be able to manually operate the light (turn it off completely or turn it on)

## Some design principles

- OO systems have many classes talking to each other
- Deciding which are classes needed, what methods they should have, and how to integrate them is difficult
- We can follow some principles:
    - Aim for high cohesion and low coupling
    - Abstract away details to the clients — focus on the what
    - Encapsulate data with the code that operates on it
    - Hide the implementation details from other classes
- We will now visit these principles

## Cohesion and coupling

High cohesion: a class should have a single purpose

- Cohesion is a measure of the degree to which a class completely encapsulates a single notion or functionality
- When we reuse a class for a specific purpose, we don’t want all sorts of useless baggage brought along with it

Low coupling: classes do not depend on too many others

- Coupling is a measure of the degree to which class interacts with and depends on other classes.
- A class with low coupling can be developed or modified without causing changes to many others.

## First steps in designing a solution (I)

- We need to think in abstract terms (i.e. details at this stage are irrelevant)
- There are three types of “things” mentioned in the requirements, a Light and a Timer and the Main application
- The rules of high cohesion means that these should be separated out into different classes
- There are no predefined types to represent a light or a timer, we have to make our own, A class is a type. Once we have a class we can declare a variable of that type and assign it to a value. The value in each case will be an object constructed from the class (aka an instance)

## First steps in designing a solution (II)

- We eventually want to write code that constructs objects from our classes and calls their methods
- For example we need a Light and the light will use a Timer so eventually we many end up with code that looks like this (example only we are not ready to write code yet)

```HTML
public class Light
{
	// The timer for counting the time interval
	private Timer timer;

	public Light(int timeInterval)
	{
		timer = new Timer(timeInterval);
	}
	
	public void operate() 
	{
		timer.start();
	}
}
```

## Check our classes have High Cohesion

Each class must be focused on doing ONE task (point of OOP)

- The Timer has one task; count down a specified time interval in seconds and know when the timer has expired.
- The Light also has one task; implement a light flashing on and off at regular intervals. The timer behaviour is abstracted out to the Timer class.
- The Main application also has ne task: display a flashing light and allow a user to operate it. the Light behaviour is abstracted out to the Light class.

## Responsibilities of our classes

- Once we have identified the classes we need at an abstract level, we need to understand their responsibilities and how they relate to each other.
    - The Timer starts from a starting value and counts down to 0. it can be reset to the starting value and it will tell us when the timer has expired.
    - The Light needs its own Timer which it uses to control its operation. The light has an initial starting state (on or off). It can be opened which powers the light on and starts the timer, When the time has expired the light switches off to on (or on to off) and the timer is reset.
    - The Main class needs a Light and will display it on the canvas and provide the user a way of operating the light (mouse click)
- Assume three people will work independently to write each class. They need to know what public methods are provided by each class.

## What services are provided by the Timer

- The Light developer needs to know HOW to use the Timer class. We formalise that as a list of services provided by the Timer. We don’t care how the services are implemented. These services will provide a way:
    - To construct a Timer
    - To start a Timer
    - To stop a Timer
    - To tell when the Timer has expired
    - To tell how much time to go before the Timer expired (optional, but nice to know)
    - To reset a Timer

## What are services?

Services are `public` methods

- The highlighted words on the previous slide represent the behaviour of the Timer. Each behaviour will translate into a method.
- The methods are services that the timer provides the Light.
- Thinking in these terms, we can talk about a class that provides services as being a server class and those classes that use its services as clients. In this class the Timer is the server and its client is the light

## Abstraction

- Thinking in terms of services allows for abstraction.
- We think about an abstract Timer that provides a list of services
- The client (in this case the Light class) only needs to consider what services are provided (by the Timer) and not how those services are implemented.
- The details of the implementation do not concern us yet.

## Reuse by composition (I)

- Some problems repeat very often when developing software (e.g. working with dates, drawing on the screen)
- We can save effort by reusing previously existing code
- In Java, there are largely two ways to reuse code:
    - By composition: class A relies on a services of class B
    - By inheritance: class A refines the services of class B
- Inheritance is covered in the next lecture.

## Reuse by composition (II)

- Our Light class makes use of the Timer
- This scenario is an example of reuse by composition and is based on the client-server model
- By abstracting out the components we can reuse a component any time we need to consume that component’s set of services (i.e. any time we need a timer, we just include a Timer field and use its services)
- Composition occurs whenever one class implements its services by reusing services from another class. In this case the Light class is reusing services from the Timer class by including a timer in the implementation (basically the light class creates a timer inherently)

## Abstraction: documenting contracts (I)

- Abstraction requires establishing contract (aka service) between this class (aka server) and other classes (aka clients)
- Java provides javadoc comments for this /** */
- You can document classes, fields and methods with them
- You can use HTML and javadoc tags. For instance
    - `@param name description` describes a parameters
    - `@return description` describes a returned value
- Writing good javadoc comments is an art!
    - Think of who will be using your code, not you as a developer
    - Focus on what service will be provided, not so much on how
    - Make sure you mention any obligations for the client
    - Do not repeat what the code already says!
- The best way to learn is to read well-documented code: the java source code is a good start, have a look at the source code for java.lang.Math.
- `{@code double}` uses the highlighting of normal java code
- `<i>pi</i>` puts some text in italics
- This is a field of the class, not an object (static)
- This is a constant and cannot be changed (final)
- Java naming convention is to use ALL_CAPS for constants

## Documentation of Timer

INSERT THE PHOTO FOR THE TIMER

Read the source code to see the Javadoc comments used to create this.

## Documentation of a Light

INSERT THE PHOTO FOR THE LIGHT

Read the source code to see the Javadoc comments used to create this.

## Implementing a Timer

- Implement all methods in the documentation
- To implement the methods, each timer must have some internal state made up of a set of variables and their values
- The private visibility means he variables are fully encapsulated within the class
- The timer class does not depend on any other class. it has low coupling.

```Java
public class Timer
{
	// the number of seconds we want to time
	private long timeInterval;
	// true when the timer has been started, false otherwise
	private boolean isStarted;
	// the time in seconds when the timer started/
	// this variables only has a value when isStarted is true
	private long startValue;
	
	// public constructor and public methods omitted.
}
```

## Implementing a Light

- Implement all methods in the documentation
- That requires some internal state made up of a set of variables and their values
- The private visibility means the variable are fully encapsulated within the class
- The light class depends on the Timer but it will only use its documented services. It has low coupling.

```Java
public class Light
{
	// The timer for counting a time interval
	private Timer timer;
	// whether the light is illuminated or not
	private boolean isIlluminated;
	// whether the light is powered or not
	private boolean isInUse;
	// a processing object so we can display the light on a canvas
	private PApplet processing;

	// public constructor and public methods ommitted.
}
```

## Implementing the Main Application (I)

- Implemented using the Processing library

```Java
public class Main extends PApplet
{
	private Light light;
	
	public void settings()
	{
		size(600, 400);
	}

	public void setup()
	{
		light = new Light(5, this);
	}
	
	public void draw()
	{
		background(0);
		light.display();
	}

	public void mousePressed()
	{
		light.operate();
	}
}
```

## Implementing the Main Application (II)

- Note that the Main class does not have any access to, or care about, the variables used to implement the Light class
- It also has no knowledge of a Timer being used because the Timer is fully encapsulated within the Light class
- Hiding implementation details in this way reduces the coupling between the three classes

## Grouping classes: packages

- A Java program can have many, many classes.
- We need to qualify their names somehow, or name clashes can happen: consider how many people create their own Date class
- We want to group them as well, for instance:
    - The classes dealing with file I/O
    - The classes dealing with the user interface
    - … and so on
- Packages deal with two problems

## Placing classes in a package (I)

```Java
package uk.ac.aston.timerLight;
class YourClass { ... }
```

- Convention: your package is your reversed domain name plus some segments depending on your subsystem (here “aston.ac.uk” + “timerLight”)
- You need to add a package declaration at the top of the file
- Packages are folders/subfolders within the source code
- You can nest packages
- The Timer class is a utility class, we have to put it in a package called uk.ac.aston.timerLight.util
- The source code for the Timer class needs the following first line to specify which package it belongs to

```Java
package uk.ac.aston.timerLight.util;
class Timer { ... }
```

## Placing classes in a package (II)

- The light class is a model class — it is modelling a physical thing, but its not really a utility in the way a Timer is.
- We have put the Light class into a package called uk.ac.aston.timerLight.model
- The source code for the Light class needs the following first line to specify which package it belongs to:

```Java
package uk.ac.aston.timerLight.model;
class Light { ... }
```

## Importing classes from a package

- You have used import statements before. For example.

```Java
import java.util.ArrayList;
```

- The Timer class is in a different package to the Light class so we need to import it (we also import the PApplet class from the processing library):

```Java
package uk.ac.aston.timerLight.model;
import processing.core.PApplet;
import uk.ac.aston.timerLight.util.Timer;
public class Light { ... }
```

- The main class needs to import the Light and PApplet

```Java
package uk.ac.aston.timerLight;
import processing.core.PApplet;
import uk.ac.aston.timerLight.model.Light;
public class Main extends PApplet { ... }
```

## Quick aside Java9+ modules

- Since Java9+, you can group package into modules
- Java std. libraries and JDK are broken up into modules: users can distribute executables of Java programs, bundling only the parts of Java they need
- Using a creating modules is outside the scope of CS1OOP
- Just know that they exist, so you can read the Java 11 docs
- In this module, we mostly deal with the java.base module

## Summary of the software engineering process

- We can start some requirements
- We think in abstract terms to identify the components/classes we will require in the solution
- We identify the responsibilities of those components
- We identify the relationships between the components (clients and servers)
- We identify the services provided by each component
- We document those services
- Components (classes) are organised into packages
- Only at this stage are we ready to start writing code by implementing the services
- We stopped at this this point but the developers will use unit tests and implement and test ONE services at a time and when each is complete the components will be brought together to create a software solution

# =-=-=-=-=-=-=-=-Inheritance=-=-=-=-=-=-=-=-=

## Review of reuse approaches

Types of reuse in object orientation

- By composition: class A relies on services of class B
- By inheritance: class A refines the services of class B

In this lecture

We will show how to implement reuse by inheritance

## Implementing shapes: Rectangle

```Java
public class Rectangle
{
	private double upperLeftX, upperLeftY;
	private double width, height;

	public Rectangle(double ulX, double ulY, double w, double h)
	{
		this.upperLeftX = ulX;
		this.upperLeftY = ulY;
		this.width = w;
		this.height = h;
	}

	public double getX() { return upperLeftX; }
	public double getY() { return upperLeftY; }
	public double getWidth() { return width; }
	public double getHeight() { return height; }

	public void draw(GraphicsContext gc)
	{
		gc.strokeRect(upperLeftX, upperLeftY, width, height);
	}
}
```

- With JavaFX, Rectangle would look like this
- GraphicsContext provides basic 2D drawing methods

## Implementing shapes: Ellipse

```Java
public class Ellipse
{
	private double upperLeftX, upperLeftY;
	private double width, height;

	public Ellipse(double ulX, double ulY, double w, double h)
	{
		this.upperLeftX = ulX;
		this.upperLeftY = ulY;
		this.width = w;
		this.height = h;
	}

	public double getX() { return upperLeftX; }
	public double getY() { return upperLeftY; }
	public double getWidth() { return width; }
	public double getHeight() { return height; }

	public void draw(GraphicsContext gc)
	{
		gc.strokeOval(upperLeftX, upperLeftY, width, height);
	}
}
```

- And now you do an ellipse: almost everything is the same!
- It’s only draw that is different

## Implementing shapes: Circle

```Java
public class Circle
{
	private double cx, cy, r;

	public Rectangle(double centerX, double centerY, double radius)
	{
		this.cx = centerX;
		this.cy = centerY;
		this.r = radius;
	}

	public double getX() { return cx; }
	public double getY() { return cy; }
	public double getWidth() { return r*2; }
	public double getHeight() { return r*2; }
	public double getRadius() ( return r; }

	public void draw(GraphicsContext gc)
	{
		gc.strokeOval(cx - r, cy - r, r * 2, r * 2);
	}
}
```

- This time we’re doing circles
- draw changes, and we have an extra method (getRadius)

## Problems with the previous code

- There is far too much repetition here
- Golden rule: DRY (don’t repeat yourself)
- If we needed to make a change, we may have to change things in 3 places
- All these things are just shapes anyway, can’t we generalise?

## Inheritance: concept and syntax

```Java
class Animal
{
	private String name;
	public Animal(String name)
	{
		this.name = name;
	}

	public String getName() { return name; }
}

class Dog extends Animal
{
	public Dog(String name)
	{
		super(name);
	}
		
	public void bark()
	{
		System.out.println("woof!");
	}
}
```

- Conceptually, we know that a Dog “is-an” Animal
- Therefore, a Dog can do all the things Animal does
- Dog can therefore inherit all fields and methods of Animal
- This is done in Java with the extends keyword

## Inheritance vs Composition

Examples

- Car “has-an” Engine → composition
- Car “is-a” Vehicle → inheritance
- Circle “is-a” Shape → inheritance
- Banana “is-a” Fruit → inheritance

If Car “is-a” Vehicle

- Vehicle is the “superclass” or “base class”
- Car is the “subclass”

## Applying inheritance: Shape

```Java
public class Shape
{
	private double upperLeftX, upperLeftY, width, height;
	
	public Shape(double ulX, double ulY, double w, double h)
	{
		this.upperLeftX = ulX;
		this.upperLeftY = ulY;
		this.width = w;
		this.height = h;
	}

	public double getX() { return upperLeftX; }
	public double getY() { return upperLeftY; }
	public double getWidth() { return width; }
	public double getHeight() { return height; }

	public void draw(GraphicsContext gc)
	{
		System.out.println("Forgot to override draw in" + getClass().getName());
	}
}
```

- To avoid repetition, we first create the Shape class
- This is the most general concept: a Circle “is-a” Shape
- We will have the other shape extends this one

## Applying inheritance: Rectangle

```Java
public class Rectangle extends Shape
{
	public Rectangle(double ulX, double ulY, double w, double h)
	{
		super(ulX, ulY, w, h);
	}
	
	@Override
	public void draw(GraphicsContext gc)
	{
		gc.strokeRect(getX(), getY(), getWidth(), getHeight());
	}
}
```

- We get all methods from Shape, avoiding repetition
- We do not get the constructors, though
    - Constructors in subclass must invoke the superclass constructor with super() must build the shape part before the rectangle part.
    - If we omit the super call, then Java adds super() ← empty constructor
- We replace (’override’) the definition of the draw method
    - @Override is an optional (but recommended) annotation: it makes the Java compiler check that we are actually overriding something

## Applying inheritance: Ellipse

```Java
public class Ellipse extends Shape
{
	public Ellipse(double ulX, double ulY, double w, double h)
	{
		super(ulX, ulY, w, h);
	}
	
	@Override
	public void draw(GraphicsContext gc)
	{
		gc.strokeOval(getX(), getY(), getWidth(), getHeight());
	}
}
```

- Very similar to Rectangle actually!
- We simply provide a constructor and override the draw method: strokeOval will draw the ellipse for us

## Applying inheritance: Circle

```Java
public class Circle extends Ellipse
{
	public Circle(double cx, double cy, double r)
	{
		super(cx - r, cy - r, r * 2, r * 2);
	}
	
	public double getRadius() { return getWidth()/2; }
}
```

- A Circle is not just a Shape, it’s a special case of an Ellipse: we can reuse even the draw method
- super call computes the upper-left corner, width and height
- We add a getRadius() method (this is a circle, after all)

## Review: constructors and inheritance (I)

```Java
class Superclass
{
	public Superclass() { System.out.println("Superclass"); }
}

class Subclass extends Superclass
{
	public Subclass() { System.out.println("Subclass"); }
}
```

## Review: constructors and inheritance (II)

```Java
class Superclass
{
	public Superclass(int x) { System.out.println("Superclass"); }
}

class Subclass extends Superclass
{
	public Subclass() { System.out.println("Subclass"); }
}
```

## Review: overriding (I)

```Java
class Superclass
{
	public void foo() { }
}

class Subclass extends Superclass
{
	public void foo() { }
}
```

## Review: overriding (II)

```Java
class Superclass
{
	public void foo() { }
}

class Subclass extends Superclass
{
	@Override
	public void foo() { }
}
```

## Protected fields and methods (I)

```Java
public class Shape
{
	... private double width; ... 
}

public class Circle extends Ellipse
{
	...
	public double getRadius()
	{
		// does not compile: width not accessible
		return width/2;
	}
}
```

Problem

- Say that we wanted to access width from getRadius()
- private members (fields and methods) are not accessible outside of their classes
- public members are open to everyone: too much!
- We need a middle ground

## Protected fields and methods (II)

```Java
public class Shape
{
	... protected double width; ... 
}

public class Circle extends Ellipse
{
	...
	public double getRadius()
	{
		// does compile: width now accessible
		return width/2;
	}
}
```

Solution: the protected access level

- protected members are accessible from subclasses
- Superclasses can expose impl. details to subclasses this way
- It partially breaks implementation hiding, but it can be useful sometimes (use carefully!)

## Calling overridden methods (I)

```Java
public class FilledRectangle extends Rectangle
{
	private Color color;

	public FilledRectangle(Color fill, double ulX, double ulY, double width, double height)
	{
		super(ulX, ulY, width, height);
		this.color = fill;
	}
	
	@Override
	public void draw(GraphicsContext gc)
	{
		gc.setFill(color);
		gc.fillRect(getX(), getY(), getWidth(), getHeight());
		super.draw(gc);
	}
}
```

- FilledRectangle: Rectangle filled with color
- Rather than copy-paste from draw, we can call the Rectangle version of our draw() method
- In line 12, super refers to the Rectangle part of our FilledRectangle: we can invoke its methods as usual

## All Java objects are Objects! (I)

Java allows you to ask an object for its class, and to ask a class for its methods

```Java
Dog d1 = new Dog("Fido", 1);
for (Method m : d1.getClass().getMethods())
	{
		System.out.println(m);
	}
}
```

This ability to have programs check their own structure is known as reflection. Let’s see what prints

## All Java objects are Objects! (II)

We will get something like this

```Java
too long
```

These are all methods from java.lang.Object, not from our Dog class!

## All Java objects are Objects! (III)

Java implements a single-rooted class hierarchy

- If your class does not extend any other, then it will extend java.lang.Object
- Object is the one root of the Java inheritance hierarchy
- Useful for writing code that can work with “any object”

Useful methods in Object

|   |   |
|---|---|
|equals|can check any object with any other for equality|
|hashCode|computes number as a summary (for HashMaps)|
|toString|produces a text representation of the object|
|getClass|provides Class objects with method/field information|
|wait|used for low-level concurrent programming (creating programs which do things simultan)|