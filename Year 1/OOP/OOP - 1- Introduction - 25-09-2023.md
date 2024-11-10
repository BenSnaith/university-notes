## What is programming?

Writing a sequence of instructions to tell the computer what to do, the potential is almost unlimited.

There are sequences of computer interaction you interact with everyday.

- Text entered into a phone app
- The scheduling system in the university
- Processing the video feed of a car and using data to find obstacles.

Computers cannot get tired and can work much faster than a human can repeatedly with minimal mistake

- Code controls things such as fitting components
- Code monitors data such as water level or heart rate or anything.

We can write a program to make a computer do work we dont want to or can’t quick enough.

There are social, legal and ethical issues which need to be taken into account.

## How do we program?

We write statements in some programming language by editing a file.

Depending on the choice of programming language and environment those statements may be interpreted or compiled to an intermediate code that is native to the specific computer.

Native code can be ran directly but is specific to a type of processor.

Writing code is a manual task this module is about learning the principles and practice of how to do that.

If you know what you are doing you can manually compile code.

We use an IDE because compiling and running code that we have writing is a task that computers can do easily, IDE’s are designed to assist and help us with spellchecking, syntax etc.

## The Canvas

The canvas top left is 0,0 not the bottom left.

Everything we see on the screen is made up of pixels.

A pixel is a point on the screen, imagine filling one of the squares on a piece of graph paper.

The higher the resolution, the smaller the pixels.

## Lines

To draw a line in processing we need to give it the line command.

`line(1,1, 8,8);`

`line(1,3, 8,3);`

## Shapes

We can draw shapen on a screen by filing in pixels that form the outline of a shape

`rect(10,17, 12,6);`

first coordinate is the top left position, the second coordinate is the length and the height.

`rect(topleftx, toplefty, width, height);`

## How big is the canvas?

We must first set the size of the canvas so we can have the correct size for them.

We use a command called `size(width, height);`

## Ellipse

`ellipse(centrex, centrey, width, height)`

## Set the colours of shapes

Stroke is the outline of the shape

Fill is the centre of the shape

`fill(0), fill(255), fill(redvalue, greenvalue, bluevalue, opacity);`

Processing uses RGB and Greyscale in order to colour shapes.

We can specify a shape with no fill with the command `noFill();`

## Background

We can set the colour of the background

`background(colourvalues)`

==IF YOU DRAW THE BACKGROUND AFTER YOUR SHAPES IT WILL COVER THE SHAPES.==

## rectMode();

`rectMode(centre);`

This will make is so the first coordinate given is the centre of the rectangle and not the top left hand corner.

## Order for processing.

You must set the attributes for the shape before drawing the shape for it to be applied for that shape.

Its like you are preparing the brush before you paint the shape.

# Variables

==A Variable is a box that stores a value==

A variable is a place to store ONE piece of information.

Each variable has a type and a value.

e.g. Integer, String, Float, Long, Boolean.

We also need a name for that variable so that we can refer to it later.

  

- Boolean; True or False e.g. `boolean isButtonPressed`
- Char; A single character ‘&’ e.g. `char keyPressed;`
- Byte;
- Short;
- Int; A whole number e.g. `int total;`
- Long;
- Float; Floating decimal number e.g. `float pi;`
- Double;

  

Variables must be names in camelCase

Must be an appropriate name.

## Setup and Draw

`void setup(); {}`

This is drawn once at the initialisation of the code

`void draw(); {}`

This is drawn repeatedly about 30/s, can be used to move and animate objects.

## Random

`random(maxint);`

this will call a random number below the specified integer