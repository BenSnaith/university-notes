## Why do we need arrays?

- If we look back on some of the programs we wrote using classes, we found it was easy to create two or more objects
- The problem is we need a variable for each object
- Here is some example code

```Java
Ball b;
Ball b2;

void setup() {
	size(600, 600);
	// construct ball
	// objects
	b = new Ball();
	b2 = new Ball();
}

void draw() {
	background(127);
	// draw the ball
	b.display();
	b2.display();
	// move the ball
	b.move();
	b2.move();
	// bounce the ball
	b.bounce();
	b2.bounce();
}
```

## How does this scale up?

- The code on the previous slide use two ball objects
- What if wanted 100 or 1000 objects. We would need code that started like this:

```Java
Ball b1;
Ball b2;
Ball b3;
Ball b4;
// etc
```

- Then we would need to construct all those objects:

```Java
b1 = new Ball();
b2 = new Ball();
b3 = new Ball();
b4 = new Ball();
// etc
```

- This makes life harder

## A simpler way

- Declare a pre-packaged box of variables all of the type `Ball`. We call the “box of variables” an array
- Here is the way to change the program to use box of ball variables

```Java
Ball [] ballVariables;
int arraySize;
```

- I can then create this box and say exactly how many variables I want. Here is how I ask for 100 variables in a box:

```Java
arraySize = 10;
ballVariables = new Ball[arraySize];
```

- Then I could use repetition to assign a value to all the variables in the box

```Java
for (int index = 0; index < arraySize; index++) {
	ballVariables[index] = new Ball();
}
```

## What is an array

- Our “box of variables” has some structure to it.
- The array is accessed using an index which is a number that indicated which variable we are referring to.

![[Untitled 48.png|Untitled 48.png]]

- In the illustration above (from Learning Processing) the index numbers can be seen and each variable is represented as one box in the list
- Note that the first index value is 0.
- An array containing 10 variables has indices in the range 0 to 9

## Drawing the animated circles

To process everything in an array, we need to use a for statement (or a while statement) to repeat the steps to draw the animation with each object in the array.

```Java
void draw() {
	background(127);
	// for each ball in the array
	for (int index = 0; index < arraySize; index++)
		// display the ball
		ballVariable[index].display();
		// move the ball
		ballVariable[index].move();
		// bounce the ball
		ballVariable[index].bounce();
	}
}
```

## How do we use the array

- Each entry in the array contains an object (of type ball in this example)
- We use this syntax to refer to a specific object in the array `arrayName[index]`

## Creating arrays

- All variables in the array are the same time. All int or Ball or Car
- There are two steps to be completed before we can use the array

1. Declare an array-type variable. This step is rather similar to the declaration of any variable
2. Assign a value to the array variable constructing the array. This second step actually reserves the space in the computers memory for the “box of variables”

## An array to store a list of integer values

- Lets assume we need to keep track of 15 integer values that are all related (i.e top 15 scores in a game or attendance at 15 games)
- We can use an array of integer variables to hold that data

1. Declare the array variable: In this first step we declare a variable of type “array of int”. That looks like this.

```Java
int[] = arrayOfIntVariables;
```

This is not an int variable. It is a variable whose value will later be a “box of variables” indicated the type `int[]`.

1. Construct the array: In this step we assign a value to the variable above by constructing the array. That looks like this:

```Java
arrayOfIntVariables = new int[15];
```

This special syntax, `new int[15]`, creates the box which can hold exactly 15 variables all of type int.

## How do we refer to each variable

- The array is a box containing many variables
- How do we refer to the first variable, or the fifth?
- We use the array variable and add the index of the variable we want:
    
    - The first variable in the array we created:
    
    ```Java
    arrayOfIntVariables[0];
    ```
    
    - The second variable in the array we created:
    
    ```Java
    arrayOfIntVariables[1];
    ```
    
    - The fifth variable is:
    
    ```Java
    arrayOfIntVariables[4];
    ```
    

## How do we use variables from our array?

- We can use the variables inside our array in the same way we would use a normal variable.

1. Assigning a value:

```Java
arrayOfIntVariables[0] = 507;
arrayOfIntVariables[1] = 469;
int thisScore = 100;
arrayOfIntVariables[5] = thisScore;
```

1. Access the current value:

```Java
int topScore = arrayOfIntVariables[0];
print(arrayOfIntVariables[9]);
if (arrayOfIntVariables[3] > 10) {...}
```

## What else do we need to know?

- We can set up an array with values all in one go:
    
    - Here is an array of char variables
    
    ```Java
    char[] letters = {'a', 'e', 'i', 'o', 'u'};
    ```
    
    - This example creates an array containing five char variables and initialises each one to the characters listed.
    - `letters[0]` has the value ‘a’
    - `letters[0]` has the value ‘a’
    - `letters[0]` has the value ‘a’
    - `letters[0]` has the value ‘a’
    - `letters[0]` has the value ‘a’
- All arrays have a length property which holds the total number of variables in the array:
    - `letters.length` has the value 5

## An example using the array of `char`

- Our example will use the array set up on the previous slide:

```Java
char[] letters = {'a', 'e', 'i', 'o', 'u'};
```

- What we would like to do is to display each letter on the canvas in a random `textSize` and color:

## Planning our application

- To set up this application, we need the array and a canvas:

```Java
char[] letters = {'a', 'e', 'i', 'o', 'u'};

void setup() {
	size(300, 300);
	frameRate(2);
}
```

- In the draw we want to repeatedly display letters, first `letter[0]`, then `letter[1]` and so on until `letter[4]`. We can do that using a for statement:

```Java
for (int index = 0; index < letters.length; index++) {
	x = random(0, width);
	y = random(0, height);
	// choose a fill colour and textSize at random
	text(letters[index], x, y);
}
```

## A closer look at that repetition

- When we process the variables in an array, we nearly always treat each one in the same way:

```Java
float x;
float y;
background(255);
x = random(0, width);
y = random(0, height);
fill(colour(random(0, 200)));
text(letters[0], x, y);
x = random(0, width);
y = random(0, height);
fill(colour(random(0, 200)));
text(letters[1], x, y);
x = random(0, width);
y = random(0, height);
fill(colour(random(0, 200)));
text(letters[2], x, y);
// and so on
```

## Using repetition with arrays

We can handle that repetition on the previous slide with a while or a for statement:

![[Untitled 1 27.png|Untitled 1 27.png]]

We just need one extra variable to count each index string at 0 and finishing at `letter.length - 1` (the last valid index)

## Other uses for repetition with arrays

Assume we need 1000 random numbers and we will store them in an array. Here is the code to declare and construct the array:

```Java
float[] values;
values = new float[1000];
```

- We would not want to write 1000 assignment statements

```Java
values[0] = random(0, 10);
values[1] = random(0, 10);
values[2] = random(0, 10);
// etc
```

- The only sensible way to assign values into the array is to use repetition to assign a value to each variable

```Java
for (int index = 0; index < 1000; index++) {
	values[index] = random(0, 10);
} 
```

## Plotting the last 50 mouse cursor locations

- Could we draw a snake by keeping a record of the last 50 mouse locations and then plot each of those locations by drawing a circle.
- The size of each circle gets larger as we plot more recent locations
- The fill colour gets darker as we plot more recent locations.

## The plan to develop the application

- We will write a class to represent a canvas position called `CanvasPosition`. It has two variables, x and y.
    - An alternative solution using TWO arrays, one for the X values and the other for the Y value is in Leaning Processing
- We will declare an array called `trail` to hold variables of type `CanvasPosition` and create the array with 50 variables
- The current `CanvasPosition` always goes as the last entry in the array which is: `trail[trail.length - 1]`
- Before we add the current `CanvasPosition` to the end of the array, we need to make space by shifting all the previous entries up.
- Add the current `CanvasPosition` at `trail.length - 1`.
- Plot all the `CanvasPositions` objects, starting with the oldest.

## Things to note

- The most recent `CanvasPosition` is in `trail[trail.length-1]`
- The previous `CanvasPosition` will be in `trail[trail.length-2]`
- The `CanvasPosition` before that will be in `trail[trail.length-3]`
- And so on until the oldest canvas position which is in `trail[0]`
- Every time we shift the values up, the most recent `CanvasPosition` moves to `trail[trail.length-2]` to make space for the new `CanvasPosition` which is inserted into `trail[trail.length-1]`

## The `CanvasPosition` class

```Java
class CanvasPosition {
	private float x;
	private float y;

	public CanvasPosition(float xp, float yp) {
		x = xp;
		y = yp;
	}

	public float getX() {
		return x;
	}

	public float getY() {
		return y;
	}
```

## Setting up everything

```Java
// Declare a variable of type array-of-CanvasPosition
CanvasPosition[] trail;

void setup() {
	size(400, 400);
	// construct the array
	trail = new CanvasPosition[50]
	// we need to initialise all 50 variables
	for (int index = 0; index < trail.length; index++) {
		// intially every CanvasPosition is (0, 0)
		trail[index] = new CanvasPosition(0, 0);
	}
}
```

- Note that we initialise each variable in the array with `CanvasPosition` objects representing the mouse coordinated (0, 0)

## The `draw` method

The `draw` method calls other methods to make the code easier to follow:

```Java
void draw() {
	background(255);
	// shift all the values up in the array
	shiftEverythingUp();
	// add current CanvasPosition at the end of the array
	trail[trail.length-1] = new CanvasPosition(mouseX, mouseY);
	// plot all 50 CanvasPositions
	drawTrail();
}
```

## Shifting the entries in the array

- We start at index 0 and overwrite it with the value at index 1
- New we overwrite the entry at index 1 with that from index 2, and so on. Eventually index (length-2) is overwritten with index (length-1).
- Here is the code to do that using a for statement

```Java
void shiftEverythingUp() {
	// repeat for all enteries except the last
	for (int index = 0; index < trail.length-1; index++)
		//copy the values at index+1 into location index
		trail[index] = trail[index+1];
	}
}
```

## Drawing the complete trail of positions

- The oldest position is plotted with a tiny pale circle, the next oldest is a slightly larger, less pale circle and so on until the most recent circle is the largest and darkest

```Java
void drawTrail() {
	// for each entry in the array
	for (int index = 0; index < trail.length; index++) {
		noStroke();
		// lightest fill at index 0, gradually darker
		fill(255-(index*5));
		// draw a circle to plot CanvasPosition at index
		// use index as the diameter of the circle
		circle(trail[index].getX(), trail[index].getY(), index);
	}
}
```

## Calling object methods

- Lets look at the last line of `drawTrail`

```Java
// draw a circle to plot the CanvasPosition at index
circle(trail[index].getX(), trail[index].getY(), index);
```

- Remember, trail[index] is just a variable of type `CanvasPosition` and so it makes sense that we can call the `getX` and `getY` methods directly
- If you prefer you can use a local variable to make things easier to follow:

## Remember the flower exercise?

- In week 5, the lab exercise was to create a flower class and the flower grew and the sun smiled.
- It wasn’t too difficult to declare two variables and have two flowers
- If we use an array, we can have as many flowers as we like

## Setting up the garden

```Java
// declare an array of flower variables
Flower[] flowers;
Sun sun;

void setup() {
	size(800, 600);
	// construct the array of 20 variables
	flowers = new Flower[20];
	// for every variables in the array
	for (int index = 0; index < flowers.length; index++)
		flowers[index] = new Flower(300, 400);
	}
	sun = new Sun(600, 150);
}
```

## Drawing the garden

```Java
void draw() {
	background(200, 200, 250);
	sun.display();
	// assume nothing is in bloom
	boolean inBloom = false;
	// for every Flower variable
	for (int index = 0; index < flowers.length; index++) {
		// call the display method
		flowers[index].display();
		// call the grow method
		flowers[index].grow();
		// inBloom is true when a flower is fully growm
		inBloom = inBloom || flowers[index].isMaxHeight();
	}
	// sun smiles when at least one flower is in bloom
	sun.setSmiling(inBloom);
}
```

## What we have learned thus far

- There is an order to how we use arrays
- As well as single variables, we can have a “box-of-variables”, otherwise known as an array
- Such variables get declared using the “box” syntax [];

```Java
Flower[] flowers;
int[] topScores;
CanvasPosition[] positions;
```

- After declaring the variable, we need to construct the array using the syntax new type[n] where n is the number of variables and type is their type:

```Java
flowers = new Flowers[12];
topScores = new int[10];
positions = new CanvasPosition[50];
```

## All variables need to be intilialised

- Just as we do in setup, we must assign an initial value to all variables, even those in an array.
- After declaring the array variable and then contructing the array, we can assign initial values to every variable in the array.
- It is possible to do that all in one go, as we did here:

```Java
char[] letters = {'a', 'e', 'i', 'o', 'u'};
```

- More often we will use a for or while loop to assign initial values

## What if we don’t assign a value

- All variables have a “default” value although that values is often not what we want as an initial value.
- It is a good practice to always assign an initial value. In fact processing often tells us when a value has not been assigned
- What if we have this sequence of statements

```Java
int[] b;
b = new int[5];
print(b[0]); // prints 0
```

- Numeric values such as int, float, etc all get given the initial value of 0 if we don’t assign a value
- boolean variables get the default value of false.
- What if we have this sequence of statements

```Java
Flower[] flowers;
flowers = new Flower[15];
print(flowers[0]);
flowers[0].display(); // error: null has no methods
```

- Object variables get the default values of null. This special value means “no value yet”.
- If the value of `flowers[0]` is null, then trying to use the Flower class methods will give an error
- Trying to call `flower[0].display()` or `flowers[0].grow()` will generate a `NullPointerException`

## Using `null`

- Object type variables (anything we need to use new to initialise) are the ONLY variables that can be assigned the value `null`.
- We often have to check object variables for non-null values

```Java
CanvasPosition cp = null;
if (cp != null) {
	// we have a usefull value
} else {
	// we have no useful value
}
```

## Another source of errors

When using an index to access a variable in an array, that index MUST be a valid location in the array

```Java
int[] topScores = new int[10];
print(topScores[0]);
print(topScores[9]);
print(topScores[10]); // error
print(topScores[-1]); // error

int index = ...
if (index >= 0 && index < topScores.length) {
	print(topScores[index]);
} else {
	// its not a valid index
}
```

- If the index is not valid we will get an `ArrayIndexOutOfBoundsException`

## One more example, animating stripes

- We will make a class that represents a vertical stripe on the canvas
- The stripe class needs variables to hold its X coordinate, its speed as it moves across the canvas, its width and its colour
- The constructor for Stripe sets the X coordinate to 0, the speed, width and colour to random values
- The stripe methods are display and move, Stripes move from left to right and then reset back to left

## Variables for the `stripe` class

```Java
class Stripe {
	private float x;
	private float speed;
	private float w;
	private color clr;

	// constructor
}
```

- Stripe are just vertical rectangles on the canvas
- Each stripe starts at the left hand edge and moves across the canvas
- They are positioned at some X position, `x`, they have a width, `w`, they have a colour, `clr`. and they move horizontally by `speed` pixels each frame

## The `stripe` constructor

```Java
class Stripe {
	public Stripe() {
		reset();
	}

	private void reset() {
		speed = random(0.5, 1.5);
		w = random(10, 30);
		x = 0 - w;
		clr = colour(random(0, 255), random(0, 255), random(0, 255))
	}
}
```

- The reset method inilialises all of the variables. We use a separate method for that because we want to use it to reset each stripe when it has moved across the canvas

## The `stripe` behaviour

```Java
class Stripe {
	void display() {
		fill(clr);
		noStroke();
		rect(x, 0, w, height);
	}

	void move() {
		x += speed;
		if (x >= width) {
			reset();
		}
	}
}
```

- The display method draws the stripe
- The move method updates the position of the stripe

## An array of `stripe`

- To animate a number of stripes across the screen we will maintain an array of stripe variables.

```Java
// An array of stripes
Stripe[] stripes;

void setup() {
	size(480, 270);
	// construct the array size 10
	stripes = new Stripe[10];
	// initialise all Stripe variables in the array
	for (int i = 0; i < stripes.length; i++)  {
		stripes[i] = new Stripe();
	}
}
```

## Using the array

- In the draw method we need to repeatedly `display` and then `move` each `stripe`

```Java
void draw() {
	background(100);
	// display and move all Stripe objects
	for (int i = 0; i < stripes.length; i++) {
		stripes[i].display();
		stripes[i].move();
	}
}
```