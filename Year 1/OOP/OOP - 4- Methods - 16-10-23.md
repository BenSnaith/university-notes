**Methods are a way we can organize our code.**

For example if we were making a space invaders game, the steps to implement the game could look like this;

```Java
void draw() {
	background(0);
	drawSpaceShip();
	drawEnemy();
	moveShip();
	moveEnemy();
}
```

A basic prototype of a space invader game can be created with just 2 squares on a black background, have a go doing this yourself…

## Why do we use methods?

Methods can make our life easier by allowing us to organise our code. You have already been calling methods like; line(); ellipse(); rect(); which are already pre-baked into processing however if we could view the code behind these methods we could see how they function.

Like these method, we can create our own the achieve specific tasks we want to do, line() already exists but what if we wanted snowMan() so we can use this simple method to output what we want.

## Software design principles

- Methods are one way of allowing the software design principles of modularity and reusability.
- **Modularity** refers to the practice of diving a large program into smaller modules, for example the method the code to draw the spaceship.
- Reusability refers to the practice of reusing code without having to retype it all. Once you write the method you can call upon it as many times as you like.

## How do we write our own methods?

- There are three parts to defining a method
    - Return type
    - Method name
    - Parameters

  

```Java
returnType methodName(parameters) {
	// Code to implement into method
}
```

  

## An example method

- Our method to draw the spaceship could be implemented simply as “draw a red rectangle”
- There is nothing to return so we denote that by writing `void` as the return type.
- The method name in this case is `drawSpaceShip`
- We don’t need any parameters, so the parameter list is empty.
- Here is the method:

```Java
void drawSpaceShip() {
	fill(255, 0, 0);
	rect(shipX, shipY, 50, 50);
}
```

## Calling a method

Calling our methods is no different to calling the background or rect methods.

```Java
void draw() {
	drawSpaceShip(); // This would run the code above.
}
```

## Breaking a program down into methods.

- Lets look back at the bouncing ball program and see how it can be broken down into methods.
- First lets look at the properties of the ‘ball’ as defined by a set of variables.

```Java
int x;
int y;
int speed;
int colour;

void setup() {
	size(200, 200);
	//set up the properties of the moving circle
	x = 0; // Ball will start on left hand side.
	y = height/2;
	speed = 1; // slow speed
	colour = 127; // grey colour
}
```

Here is the draw method that uses the variables described on the previous side.

```Java
void draw() {
	background(255);
	// display the ball
	stroke(0);
	fill(colour)
	ellipse(x, y, 32, 32);
	// move the ball
	x = x + speed;
	// if necessary, bounce the ball
	if ((x <= 0) || (x >= width)) {
		speed = speed * -1;
	}	
}
```

## Bounce with methods

On the previous slides, we comments identify the logical steps, we can turn each logical step into a method so draw only contains method calls.

```Java
void draw() {
	background(255);

	//display the ball
	display();

	//move the ball
	move();

	//bounce the ball
	bounce();
}
```

- The **display** method contains the code to set the colour and draw the ball.

```Java
void display() {
	stroke(0);
	fill(colour);
	ellipse(x, y, 32, 32);
}
```

- The **move** method only contains the code to update the position of the ball

```Java
void move() {
	x = x + speed;
}
```

- The bounce method only contains the code to reverse the speed when the ball hits the edge of the canvas.

```Java
void bounce() {
	if ((x <= 0) || (x >= width)) {
		speed *= -1;
	}
}
```

## The benefits of methods

Although the program does not do anything different to the version without the methods there are several benefits.

- The heart of the program, the **draw** method becomes much more readable.
- If we want to change what is displayed, we only change the display method.
- The program is much more **modular** - each method can be thought of as a module
- The methods are **reusable** whenever we need that code it can be called again with that method.

## Methods can have parameters.

- The fill method requires a parameter which provides the colour of the fill
- Parameters provide values that the method needs in order to complete
- We will now look at methods with parameters

## A Method to draw a black circle

- Let’s define a method drawBlackCircle which requires us to provide the diameter of a circle.

```Java
void drawBlackCircle(int diameter) {
	fill(0);
	circle(50, 50, diameter);
}
```

The declaration of the parameter goes inside the brackets. The parameter is a local variables that we can then use only inside this method.

## More than one parameter.

- Here is a fully parameterised version of the method. We have changed the name because it doesn’t always draw a black circle

```Java
void drawGreyCircle(float x, float y, int diameter, int greyValue) {
	fill(greyValue);
	circle(x, y, diameter);
}
```

- The X and Y coordinates are passed as floats and used in the circle command.
- The gray value is passed as an int and is used in the fill command.
- We can call this method whenever we need it like so.

```Java
drawGreyCircle(50, 72, 32, 127)
```

## Drawing a car using methods.

- We would like the be able to draw multiple cars, each at different positions and of different sizes without repeating the code.
- Create a method called `drawCar`
- The method should draw the car at a given position with some given size.
- The ‘given’ information will become the parameters.
- The position requires two int parameters, which we will call `x` and `y`, and the size will require one int parameter which we will call `theSize`.
- The method should be self contained. It should have all the information it needs via the parameters.

```Java
void drawCar(int x, int y, int theSize) {
	int offset = theSize / 4;
	rectMode(CENTER);
	stroke(0);
	fill(127);
	rect(x, y, theSize, theSize/3);
	fill(0);
	rect(x - offset, y - offset, offset, offset/2)
	rect(x + offset, y - offset, offset, offset/2)
  rect(x - offset, y + offset, offset, offset/2)
  rect(x + offset, y + offset, offset, offset/2)
}
```

## Calling out car method

```Java
void setup() {
	size(400, 200);
}

void draw() {
	drawCar(100, 100, 75);
	drawCar(150, 150, 50);
}
```

## Coloured cars

- As written the `drawCar` method will draw cards of different sizes but they will all be the same colour.
- If we want to specify the colour of each individual car, that means one more parameter
- How can we pass the value? Grey? RGB?
- Processing has a data type called `color` and a method called `colour()` that will return a single colour value that could be greyscale or RGB based.

## Using the color method

- The first thing to note is that the colour method returns a value.
- We should store that value using an assignment operator.
- The returned value is type color.
- Here is how we create a grey colour

```Java
color grey = color(127);
```

- Here is how we create and RGB based colour

```Java
color purple = color(200, 0, 200);
```

- This new found knowledge means that we could have a new parameter in out `drawCar` method which is the colour of the car.

## Cars in colour

```Java
void drawCar(int x, int y, int theSize, color c) {,
	int offset = theSize / 4;
	rectMode(CENTER);
	stroke(0);
	fill(c);
	rect(x, y, theSize, theSize/3);
	fill(0);
	rect(x - offset, y - offset, offset, offset/2)
	rect(x + offset, y - offset, offset, offset/2)
  rect(x - offset, y + offset, offset, offset/2)
  rect(x + offset, y + offset, offset, offset/2)
}
```

## Calling drawCar in colour.

```Java
void setup() {
	size(400, 200);
}

void draw() {
	drawCar(100, 100, 75, color(244, 102, 55);
	drawCar(150, 150, 50, blue);
}
```

## A word on noLoop.

- Remember that the draw method is repeatedly called over and over and over
- Sometimes we just want the draw to be called once and then stop.
- We can stop it by calling `noLoop();`
- If necessary we can make draw be called again by using `loop()` perhaps after a `keyPressed`

## The return type.

- Up until now, our methods were declare with a return type of void, That means no value is returned
- We saw an example of the color method that returned a value representing a colour
- We will now look at how we can define our own methods that return values.

## A method to return distance.

- Imagine we want to measure the distance between two objects on the screen
- Let’s say the objects are the center of a circle positioned at (100, 100) and the position of the mouse cursor.
- We can use Pythagoras theorum to do this.
    
    $A^2 = B^2 + C^2$﻿
    

## Calculating distance

- Ptheorem, says the hypotenuse of a right angled triangle is:
- Here is how we can calculate the distance between point (100, 200) and the mouse cursor based on Pythagoras.

```Java
float side1 = 100 - mouseX;
float side2 = 200 - mouseY;
float distance = sqrt((side1*side1) + (side2 * side2))
```

the resulting value of distance is the distance between the two points.

The code only does this once, what if we wanted it to do this repeatedly so we could get different values as the cursor moves.

## A method to return the distance between two objects.

```Java
float calculateDistance(float x1, float x2, float y1, float y2) {
	float side1 = x1 - x2;
	float side2 = y1 - y2;
	float result = sqrt((side1*side1) + (side2 * side2));
	return result;
}
```

## Calling a method that return a value

```Java
float howFar = calculateDistane(args);
print(howFar);
```

## Colour depending on distance from mouse

```Java
void draw() {
	background(255);
	float howFar = calculateDistance(args);

	fill(howFar, 0, 0);
	circle(100, 100, 70);
}
```

## Calling a method inside another method

- Lets say we want to know when the mouse cursor is over the top of a circle of diameter d positioned at some point (x, y)
- A method to tell us this would return true when the mouse is over and false when it isn’t

```Java
boolean isOver(float x, float y, float diameter) {
	float d = calculateDistance(x, y, mouseX, mouseY)
	if (d <= diameter/2) {
		return true;
	} else {
		return false;
	}
}
```

## Using our new method

```Java
void draw() {
	background(255);
	boolean over = isOver(100, 100, 70);
	if (over == true) {
		fill(255, 0, 0);
	} else {
		fill(0, 255, 0)
	}
	circle(100, 100, 70);
}
```

# Summary

- We introduced methods.
- Methods make code readable and more organised.
- Methods are written once and can be called repeatedly.
- Methods may have parameters so that values can be passed to them.
- Methods have a return type so that calculated values can be returned.