# Inheritance II

## Goals for this lecture

- Forbid overriding and extension, and create constants with the final keyword
- Use polymorphism to implement more extensible programs
- Tell apart static type and dynamic type
- Use co-variant return types to reduce need for explicit casts
- Apply upcasting and downcasting across the inheritance hierarchy when appropriate

## Last lecture: What did we learn

- This is a UML program
- White triangle arrow = inherits
- Typically, the superclass is drawn at the top
- Ellipse extends Shape and Circle extends Ellipse
- Reuse behaviour from the base class with super
- Overriding and method protected
- private and protected

## Preventing overriding with final

```Java
public final native void java.lang.Object.wait(long) ... 
public final void java.lang.Object.wait(long, int) ...
public final void java.lang.Object.wait() ...
...
public final native java.lang.Class java.lang.Object.getClass()
public final native void java.lang.Object.notify()
public final native void java.lang.Object.notifyAll()
```

- Remember these Object methods from the last lecture?
- final methods cannot be overriden in subclasses
- This is usually done for security or reliability
- Java does not want you to break the getClass method or any of the others

## Creating random shapes

```Java
private Random rnd = new Random(3);
private ??? createRandomShape() {
	final int option = rnd.nextInt(3);
	final int rndX = rnd.nextInt((int) canvas.getWidth());
	final int rndY = rnd.nextInt((int) canvas.getHeight());
	final int rndH = rnd.nextInt(200);
	final int rndH = rnd.nextInt(200);

	if (option == 0)  return new Rectangle(rndX, rndY, ...);
	else if (option == 1) return new Ellipse(rndX, rndY, ...);
	else return new Circle(rndX, rndY, rndW);
}
```

- We want to create one of three random shapes in each execution
- Method should return a Rectangle, Ellipse or a Circle.
- We can only specify one return type, though!
- What should the return type be?

==SHAPE: as each of the three shapes inherits shape, it can still be identified as a case, it kinda like how a dog can be the dog class but it is also still an animal and it wouldn’t be wrong to classify it as an animal.==

## Why did that work?

(i kinda explain this above)

- A rectangle is a shape, so you can assign a rectangle object to a shape variable
- Obviously, a rectangle is not a circle
- Last one fails because the compiler only looks at the declared type of s1 for the assignment: a Shape may not be a Rectangle

## Review: Assignment and Inheritance

THERE IS A UML THAT I DONT HAVE, FIND IT AND PASTE IT 🙂

- Another hierarchy of classes
- Is a Student a Person?
- Is a Teacher a Person?
- Is a Person a Teacher? Not necessarily, The person doesn’t have to be a teacher but the could be!

```Java
Person p1 = new Student(); // legal
Person p2 = new PhDStudent(); // legal
PhDStudent phd1 = new Student(); // illegal
Teacher t1 = new Person(); // illegal
Student s1 = new PhDStudent(); // legal

// quick way to figure this out, the thing of the left needs to have
// more power than the thing on the right, e.g the thing on the right is a child of the
// left either direct or indirect.
```

## Preventing Subclassing with final

From the official Java source code:

```Java
/**
 * The code class represents character strings. All string literals in Java programs
 * such as "abc", are implemented as instances of the class.
 * <p>
 * Strings are constants; their values cannot be changed after they are created.
 * String buffers support mutable strings. Because string objects are immutable they
 * can be shared.
*/
public final class String ... {
 ...
}
```

- Sometimes you don’t want a class to be overextended
- The main reason to prevent inheritence is to make sure the way a class behaves is not affected/corrupted by a sub-class

## Reviewing all valid uses for final

```Java
// Final for primative type field: value will always be 3.14
private final double PI = 3.14;

// Blank final for type field: value cannot be changed after being created
private final int y;

// Final for reference field: will always point to this object
private final Rectangle r = new Rectangle(...);

// Blank field for ref. field: cannot retarget after ctor
private final Rectangle;

// Final variables: cannot be changed after init
final int x = 42; final Circle c = new Circle(...);

// Final classes: cannot be extended
public final class String { ... }

// Final methods: cannot be overridden
public final void java.lang.Object.wait() { ... }
```

## Polymorphism: concept and use

```Java
...
private Shape[] shapes;
...
private void draw() {
	...
	for (Shape shape : shapes) {
		shape.draw(graphics);
	}
	...
}
```

- A variables can hold objects of multiple types: shapes could be a rectangle, a circle, an ellipse or a filledRectangle
- During execution, Java knows which draw to use, even if the variable is of type Shape
- This is known as late binding of method calls, and it matches the idea of objects sending messages to each other and reacting to them
- A new Shape subclass does not require changing draw(): our program is easier to extend

## Polymorphism: static vs dynamic type

- Let’s see a generic example before going back to shapes
- static type of a variable or argument is the declared type.
- dynamic type of a variable or argument is the type of the object the variable/argument refers to.

```Java
class A {

}
class B extends A {

}
public static void main(String[] args) {
	A x; // x static type A
	B y; // y static type B
  x = new A(); // x dynamic type A
  y = new B(); // y dynamic type B
  x = y;
}
```

Static vs Dynamic type, again back in the shapes example

- Static type of a variable: as declared, never changes
- Dynamic type: depends on current reference, changes
- Compilation uses static type, execution uses dynamic types

## Covariant return in Java

```Java
class SuperClass {
	public SuperClass myMethod() {
		return new SuperClass();
	}
}

class SubClass extends SuperClass {
	@Override
	public SuperClass myMethod() {
		return new SubClass();
	}
}
```

- Java allowing overriding by changing the return type, but only Covariant return types are allowed (like shape, rectangle, circle, ellipse)

## Upcasting versus downcasting

- Remember
    - This is a UML diagram with the classes in our program
    - White triangle arrow = extends
    - Typically, superclass is drawn at the top (class hierarchy)
- Casting “up” from circle to shape is “upcasting”: it’s always safe as the circle already inherits the shape
- Casting “down” from shape to rectangle is “downcasting”: it is potentially unsafe unless we first check with `instanceof`

## Reviewing some reccomendations

- Writing most code outside the hierarchy (e.g. main class program) only depending the services of the base class provides the most extensibility
    - We can add a new Shape subclass without touching the main program
    - Java will know which specific draw method to call during execution (late binding)
- If we cannot extend the hierarchy with methods, we can use instanceof and downcasting to write a function that does different things depending on the subclass
    - This is brittle: ever new class will require that we review the code

# Abstract Classes & Interfaces

## Goals for this lecture

- Understand the value of abstract classes as base classes in a hierarchy
- Apply interfaces to decouple client code from specific implementations of the services it requires
- Combine extends and implements to create classes with multiple supertypes
- Justify the design of the Java Collections Framework as a combination of abstract classes and interfaces

## Revisiting Shape

- If we think back to the shape class, we will recall that the draw method is essentially useless, it just tells us to implement it properly.
- You can’t just draw a shape, the concept is abstract, so what is the point of having it.
- For these cases, Java allows you to mark a method as abstract and leave it without a body: see draw above
- As soon as anything is abstract, the entire class must be abstract: you cannot create instances of it
- Subclasses will need to “fill the gaps” by overriding the abstract methods, or they will have to be abstract too

```Java
public class Rectangle extends Shape {
	public Rectangle(double ulX, double ulY, double w, double h) {
		super(ulX, ulY, w, h);
	}
	@Override public void draw(GraphicsContext gc) {
		gc.strokeRect(getX(), getY(), getWidth(), getHeight());
	}
}
```

- Rectangle implements the only abstract methods from shape, so we don’t need to mark it as abstract
- That means we can do new Rectangle( … ) normally

## Abstract Classes vs Concrete Classes

- Shape is an abstract class
- The others would be concrete classes (if they don’t have abstract methods)
- Concrete classes offer the implementation of the inherited abstract methods

```Java
public abstract HttpServlet ... {
	...
	protected void doPost( ... );
	protected void doGet( ... );
	...
}
```

- If you have abstract methods, class must be abstract
- However, a class doesn’t need abstract methods to be abstract: you can generally just mark it as so
- One common example is HttpServlet (outside scope of CS1OOP): designers wanted to force you to override at least one of the do methods (it was a design choice)

## Non-Boxy Shapes

```Java
private void draw() {
	...
	for (Shape shape : shapes) {
		shape.draw(graphics);
	}
	...
}
```

- So far, all we have in the program are “boxy” shapes: they have one corner, a width and a height
- What if we want to add things which are not as boxy
- Let’s try to generalise even further: what is the bare minimum that draw in Launcher needs? Launcher makes the calls
- It just wants things that can be asked to draw() themselves

## Final version: Drawable

```Java
public abstract class Drawable {
	public abstract void draw(GraphicsContext gc);
}
```

- Our first intuituion is the create it as an abstract superclass of shape
- Shape would now extend Drawable and drop its own declaration of draw( )
- The launcher class could be changed to only deal with Drawables.

```Java
/*
 * We can only extend (inherit from) one class: we cannot
 * extend from drawable and java.awt.Polygon at the same
 * time.
 */
public class MyPolygon extends java.awt.Polygon {
	// We're not extending Drawable, so this will not compile
	@Override public void draw(GraphicsContext gc) { ... }
}
```

- Suppose we want to repurpose the java.awt.Polygon class for our program
- We want to expose all its methods for changing the points, so we are going to extend it
- But if we extend Polygon, we cannot extend Drawable
- We seem to be stuck - luckily, Java has something for this

## From all-abstract class to inheritance

```Java
public interface Drawable {
	void draw(GraphicsContext gc);
}

public class MyPolygon extends java.awt.Polygon implements Drawable {
	@Override public void draw(GraphicsContext gc) {
		// Code for the method
	}
}
```

- An interface is a type that has no state and no constructors, only methods and public static final fields
- Methods in interfaces are public abstract by default
- A class implements 0+ interfaces
- If you have extends and implements, the extends goes first
- MyPolygon “is an” AWT Polygon, and it also “is a” Drawable

## Implementation in Shape

- Shape is now Drawable as well
- Notice how we don’t use the draw here, since drawable already has it and if we remember shape never used it anyways (and is abstract)

```Java
interface Steerable {
	int TURN_LEFT = 1, TURN_RIGHT = 2;
	void turn(int direction);
}

// is equivalent to...
interface Steerable {
	public static final int TURN_LEFT = 1;
	public static final int TURN_RIGHT = 2;
	public static void turn(int direction);
}
```

- Interfaces can have fields, but these will always be public static final
- These are generally useful for “special values” that have some meaning to the interface (e.g turn direction and the turn method)

## When to use ACs or interfaces

Abstract class

- Useful for the base/root classes of a hierarchy
- For instance, Shape in our example
- Leaves clear indications of the “gaps” to be filled
- The compiler will make sure gaps are filled for you

Interface

- Useful in code only needing objects with certain methods:
    - For instance, draw in Launcher not only requires Drawables, and not shapes in particular: anything with a draw(GraphicsContext) method will do
- Also useful when we want to return an object that has certain methods, without saying what it actually is:
    - A new version of the Lab 2 random shape generator could return drawables, and then return MyPolygon

## Example: Maps in Java

INSERT THE THING ABOUT THE MAPS AND THE ABSTRACT CLASS THING

- HashMap actually inherits from AbstractMap, which provides much of the code it needs
- AbstractMap implements the Map interface, which defines the operations for all maps (dashed line for implements)
- Good Java code will typically do this

`Map<String, Integer> m = new HashMap<>();`

- Can you guess why?
    - We should code against interfaces and not concrete classes, this allows for more flexibility