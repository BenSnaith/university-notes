**Bouncing a circle with methods**

This program bounces a circle around the screen. The variables and the methods are all related to the circle

```Java
float cX;
float cY;
float cWidth;
float speedX;
float speedY;

void setup() {
	size(600, 600);
	cX = 10;
	cY = height/2;
	cWidth = 60;
	initializeSpeed();
}

void initializeSpeed() {
	speedX = random(5, 10);
	speedY = random(5, 10);
}

void draw() {
	background(127);
	display();
	move();
	bounce();
}
```

## Bouncing multiple circles

- Moving a circle around the screen become complicated if we want two circles.
- Exercise: try writing the code to bounce two circles based on the previous slide.
- What is we wanted 100 circles all bouncing around the screen.
- Thinking about it means we have several variables for each circle and we need some way of keeping track of moving each circle.
- Clearly we want some way to organise out code so that we can separate the code related to one moving circle from the others.

## Thinking about a Mover object

- If we could invent a thing called a Mover, we could make it behave like a bouncing circle;
    - Variables: we need to store the position, size and speed for the Mover.
    - Some way to construct one of these Movers with its variables initialised, need to assign values for the position, size and speed.
    - We would need a display method to draw it on the canvas as a circle (or whatever we wanted)
    - We would need a move method to update its position
    - We would need a bounce method to make it bounce off the edges of the canvas and inverse the direction of speed.

## Where does Mover come from?

- We just invented a Mover type, How does Java know what it is.
- In Processing, we create a new tab, call it Mover and write the definition in this file
- This Mover type is an example of what we call a class
- Classes are just types we invent to represent things in our applications — in this case a moving, bouncing circle.
- When we want a Mover, we just construct one from the class. We can construct as many as we want, each with its own position, speed and colour.

## OOP design for using our Mover class

If our program was written to use a Mover class, here is how the design would look.

- Data: A variable of type Mover
- Setup: Assign a value of the Mover variable. Its value will be a new mover object.
- Draw:
    - Set the background
    - Display the Mover
    - Move the Mover
    - Bounce the Mover

The difference is that all the data concerning the position and speed of this moving/bouncing object has moved into the Mover class. Here we just require an instance of one Mover object.

## The code to use the class mover

- If we invent a new type called Mover, We can use it to write the bouncing circle application
- Here is what the main file will look like

```Java
Mover mv; //A variable of the type Mover

void setup() {
	size(600, 600);
	mv = new Mover(); //Initialise mv to be a new Mover object
}

void draw(){
	background(127);
	//Make mv behave like a bouncing circle
	mv.display();
	mv.move();
	mv.bounce();
}
```

## OOP syntax

- Every class need a name. Class names begin with a capital letter. In our example, the class is called Mover. A class name becomes our new type for variables, like String, char, int, boolean etc.

```Java
Mover mv; // a variable called mv of type Moover
```

- We need to construct an object from the class. For this we need to use the keyword new.

```Java
mv = new Mover(); // construct the Mover object
```

- In order to use the functionality of the Mover, we use the “dot” syntax which allows us to call the methods defined in the class.

```Java
mv.display(); // display the Mover
mv.move(); // move the Mover
mv.bounce(); // bounce the Moover
```

## Thinking about defining a class

To create a class we need;

The class name: We define the class name by writing a new block of code. We should do this in a new tab of processing,

```Java
class WhateverNameWeWant {
	// all code for the class here.
}
```

Data: The data for a class is a collection of variables, just like the global variables we have been using.

A constructor: This is a special method which is equivalent to a setup for new objects

Functionality: We write methods (also known as methods) in the same way we saw in the previous unit.

## The Mover class

This is the complete code for the mover class

```Java
class Mover {
	private float mX;
	private float mY;
	private float mWidth;
	private float speedX;
	private float speedY;

	public Mover() { // constructor
		mX = 10;
		mY = height/2
		mWidth = 60;
		initializeSpeed();
	}

	private void initilizeSpeed() {
		speedX = random(5, 10);
		speedY = random(5, 10);
	}

	public void display() {
		fill(color(255, 0, 0));
		circle(mX, mY, mWidth);
	}

	public void move() {
		mX += speedX;
		mX = constrain(mX, mWidth/2, width-(mWidth/2);
		mY += speedY
		mY = constrain(mY, mWidth/2, height-(mWidth/2);
	}

	public void bounce() {
		if 







```

## Visibility outside of the class

- We need two new keywords in the Mover class, these are private and public
- Private methods are only visible INSIDE the class
- Methods labelled public are visible outside of the class (i.e for the setup and draw methods)
- All variables are defined as private, this stops anyone from changing that values of the variables outside the logic contained in the class

## A closer look a the Mover class

- At he top of the class the variables that used to be global variables. These represent the Mover’s position, size and speed.
- The variables hold all od the data values needed to represent a Mover on the canvas.
- With more requirements we might need more data values which means more variables. For example
    - If we required each individual Mover object to be a different colour, we would need another variables to hold the Mover’s colour values
- Note that UNTIL we have that extra requirement for colour. We should NOT add a variables to hold the colour. Programmers do not add features on a just in case basis

## The constructor

- The constructor for a class is equivalent to its setup. The job of the constructor is to ensure that all variables are initialised with sensible value

```Java
public Mover() {
	mX = 10;
	mY = height/2;
	mWidth = 60;
	initializeSpeed();
}
```

- Note that the constructor is public and its name is the same as the class name, but it does not have a return type. That sets it apart from all other methods
- Now we can call a method from the constructor is necessary. This constructor calls the initialiseSpeed method to complete the initialisation of all variables

## Class functionality

- The functionality or behaviour of the class is defined using methods. These are much as before except they are labelled public.
- We can label a method as private if we want to restrict its use to within the class only
- Here is the method to display the mover on the canvas:

```Java
public void display() {
	fill(colour(255, 0, 0));
	circle(mX, mY, mWidth);
}
```

## The move behaviour in the Mover class

- The behaviour of moving the Mover is implemented by the move method

```Java
public void move() {
mX = mX + speedX;
mX = constrain(mX, mWidth/2, width−(mWidth/2));
mY = mY + speedY;
mY = constrain(mY, mWidth/2, height−(mWidth/2));
}
```

- This code is familiar to us, but now that it is in a class, it becomes a behaviour that we use to invoke when we have an object from that class in our program.

## The bounce behaviour in the Mover class

- The behaviour of bouncing the Mover off the edge of the canvas is implemented by the bounce method.

```Java
public void bounce() {
	if (mX >= (width−mWidth/2) ||
	mX <= (0 + mWidth/2)) {
		speedX = −speedX;
	}
	if (mY <= (0 + mWidth/2) ||
	mY >= (height−mWidth/2)) { 
		speedY = −speedY;
	}
}
```

- Again, this code is familiar to us, but now that it is in a class. it becomes another behaviour we can use with objects of type mover.

## Creating a new class

- Each class should go in a new TAB on processing. That tab should have the same name as the class

## Another example: a Car class

- Lets say that we are implementing a car race game
- A number of cards move across the screen on a track towards the finish line
- The track has a start and finish line
- The cars start behind that start like and move forward at a random speed each time
- The race ends when the first car reaches the finish line

## A plan of action

Working in bite sized chunks of work, here is a plan for working towards the application described on the previous page

1. Create some variables: position, size & colour of the car. Initialise the variables in setup.
2. Write a display method to display the car at the specified postion and colour
3. Write the draw method to call the display method
4. The next step is to be able to move the car. Again this will be done in a method. Update the draw to display and then move the car.
5. Create a class to represent a car and move that data we need to control the car into the class
6. Create a constructor for the class. We need to assign values to all the data variables. Add a Car variables to the draw/setup tab and assign it a value in setup
7. Now we can move the display and move methods into the car class
8. Now we can change draw to display and move our car. This functionality is the same as step 4.

## Things to note about our plan

- It doesn’t go all the way to the final application. That is fine, 8 steps are enough for now
- At step 4, we can draw and move the car. At step 8 we can draw and move a car but using a class to represent the car
- Although step 8 does not change the functionality, the design of the code is much better
- We don’t notice much benefit yet, but when we come to want to move two cars, we will find that the code is much simpler

## Step 1: Data for the car

```Java
float x;
float y;
color clr;
float theSize;

void setup() {
	size(800, 200);
	x = 20;
	y = 100;
	clr = color(200, 100, 100); //pink
	theSize = 60;
}
```

## Step 2: A display method

```Java
public void display() {
	float wheelOffset = theSize / 4; // for positioning the wheels
	rectMode(CENTER);
	stroke(0);
	fill (clr); // draw the body of the car
	rect(x, y, theSize, theSize/2);
	fill (0); // draw the wheels of the car
	rect(x − wheelOffset, y − wheelOffset,
	wheelOffset, wheelOffset/2);
	rect(x + wheelOffset, y − wheelOffset,
	wheelOffset, wheelOffset/2);
	rect(x − wheelOffset, y + wheelOffset,
	wheelOffset, wheelOffset/2);
	rect(x + wheelOffset, y + wheelOffset,
	wheelOffset, wheelOffset/2);
}
```

## Step 3: A draw method

```Java
void draw() {
	background(70);
	display();
}
```

## Step 4: Move the car