## Top 3 Java IDEs

- Eclipse
- Netbeans
- IntelliJ IDEA
- CS1410 will use Eclipse

## Deconstructing an IDE

- Every IDE has many features, including some advanced tools:
    - A way to create new projects
    - A file management of some kind to allow you to create and delete Java files in your project
    - An editor or editing Java source code (usually with syntax highlighting and easy code reformatting)
    - A way to compile and run your code
    - A way to debug your code
    - Professional IDEs also contain many other tools (auto-generate code, rename classes/variables, reorganise a project, analyse your code. develop Java Web Apps, version control, etc)

## Doing without an IDE: Editing source code

- We don’t need an IDE, we just need to download the individual tools necessary to write java programs
- We need a text editor, preferably one that understands Java code and does the syntax highlighting
    - DO NOT use a word processor! Java files are plain text files with no formatting
    - Notepad: if you are a windows user, the is a text editor that is included with windows. Drawbacks are that it doesn’t know about programming languages
    - Notepad++; free and easy to learn, Windows Only

## The Java Developers Kit (JDK)

- You need the JDK to make program Java code
- Java source code needs to be compiled before it can be run
- The compile command is called `javac`.
- The run command is `java`.
- Commands have to be run from the command line.

## Command-line commands

- Open a command window on your computer
- Just typing `javac` or `java` will not work.

## Running the Java compiler (`javac`)

- You can run the javac commands by typing the full path in the command window, if you extracted the JDK archive directly into the c: drive, you could type:

c:\jdk-13.0.1\bin\javac

- You will see loads of outputs in your command window

prompt> c:\jdk-13.0.1\bin\javac

Usage: `javac` <options> <source files>

where possible options include:

… loads more output

## What was all that output?

- If we try to run the `javac` commands without telling it the name of the Java source-code file to compile, it prints a “help” message telling us how to use the command
- The way we will use the compiler is to add the name of a source file after the command. For example:

c:\jdk-13.0.1\bin\javac MyClass.java

- Terminology: directory means folder. DO NOT include spaces in your file and folder names.
- The above command works only if the current directory of your command window contains the file MyClass.java
- Learn the command-line commands to navigate around the file system inside a command window

## Navigating the file-system (Windows)

- List the contents of the current directory: `dir`  
    This will be followed by some output listing the files and sub-directories of the current directory.  
    
- Move up to the parent directory: `cd ..`
- Move down to a sub directory: `cd Documents`
- Make a new sub-directory: `mkdir newDirectory`

## The `PATH` environment variable

- You don’t want to type the full path to the `javac` command every time we use it.
- We can update the environment variables that your computer uses
- One such environment variable is called `PATH`. It contains a long list of all the directories that contain commands
- You need to add the full name of the bin sub-directory of your JDK to your path

## Update your path (Windows)

- See [here](https://www.architectryan.com/2018/08/31/how-to-change-environment-variables-on-windows-10/)
- Click on the search icon, type in “env”, and choose “Edit the system environment variables”
- Click the “Environment Variables…” button
- Select the Path variable and then click “Edit…”
- Click “New” then click “Browse” and then navigate to your JDK bin directory, when you find the bin directory, click “OK” through all the windows that opened and that directory will be added to your path
- Now open a new command window and type `javac`. You should see the same output as before.

## Summary so far

- We have installed a text editor that recognises program code (Notepad++)
- We have downloaded and installed a JDK
- We have updated our path to include the jdk/bin folder
- We are now ready to write and run Java programs

## Java Programs: The `main` method

- Any new Java application should be contained in its own directory
- All Java files contain a class
- The name of any Java file is the same name as the class it contains with .java added to the end
- We need to write a special method called main which is the first method to be called when we run the program. Everything else gets called from inside main
- We don’t need the a main in Processing because it takes care of running the code in the setup/draw tab.
- In nearly every other IDE we need to write the main method

## How to write the `main` method

- Here is a class called `ExampleMain` which contains a very basic `main` method:

```Java
public class ExampleMain {
	public static void main(String[] args) {
		System.out.println("Hi from Java!");
	}
}
```

- We have seen everything except the keyword `static` before
- The keyword static allows the method to be called directly in the class without first constructing a new object.
- We will explain the purpose of `String[] args` later.

## Compiling our new class.

- We need to create a new directory and then use our editor to open a file called `ExampleMain.java` and inside it we write the `ExampleMain` class.
- In the command window, navigate to the new directory and type `dir` to see the contents of the folder
- Now type: `javac ExampleMain.java`
- You will not see any output this time (unless there is an error)

## What did `javac` do?

- We didn’t see any output from running

javac ExampleMain.java

- However, if you type dir you will now see two files:

ExampleMain.class

ExampleMain.java

- The class file is what will be run when we run the program. It contains virtual machine code.

## Running a Java program

- Every time you edit your Java source code, you need to run the javac command to compile the source code
- Once the source code is compiled, weuse the java command to run the program and we add the name of the class containing the main method. in this case ExampleMain.
- Here is the output from compiling and the running my ExampleMain class (the > is the prompt in my command window)

p> javac ExampleMain..java

p> java ExampleMain

Hi from Java!

- Note that the javac command needs the .java file type to be included.

## What are the `String[] args`?

- Command line parameters are passes in inside the `String[] args`
- Inside our main method we need to check to see if there are any parameters.
- If there are parameters, we access them in the same way we access any data in a `String` array

```Java
public class ExampleMain {
	public static void main(String[] args) {
		if (args.length == 0) {
			System.out.println("No Arguments Received");
			} else {
				for (int i = 0; i < args.length; i++) {
					String arg = args[i];
					System.out.println("args["+ i +"] is " + arg);
				}
			}
		}
	}
}
```

## Passing arguments from the command line

- Here are the commands to compile and run out update ExampleMain:

p> javac ExampleMain.java

p> java ExampleMain

No Arguments received

p> java ExampleMain one “hello there” Tony

args[0] is one

args[1] is hello there

args[2] is Tony

## A bigger problem

- We can think of the class containing the main method as the equivalent of the setup/draw tab in processing. The main can be used in the same way as the setup
- Here is a program from week 7 lecture. We use the InputReader class to get the Scanner and then use the Scanner to read a file
- We can pass the filename as a command line parameter to the main

## Update reading a file from lecture 7

```Java
import java.util.Scanner;
public class ScannerExample {
	public static void main(String[] args) {
		if (args.length == 1) {
			String file = args[0];
			Scanner in = InputReader.getScanner(file);
			while (in.hasNext()) {
				String line = in.nextLine();
				System.out.println(line);
			}
			System.out.println("done");
		} else {
			System.out.println("No file name");
		}
	}
}
```

## Running the program

- We need to copy [InputReader.java](http://InputReader.java) into the same directory in the same way we need it in the processing project.
- When we compile [ScannerExample.java](http://ScannerExample.java), the compiler will also compile and other classes that are mentioned in that class, so [InputReader.java](http://InputReader.java) will also get compiled
- Then when we run the program, we give it an argument which is the file to be used by the scanner

p> javac ScannerExample.java

p> java ScannerExample ScannerExample.java

p> [output not shown]

We have passed the Java source file as the input filename so the program reads and print that file

## Another Example: Eliza

```Java
import java.util.Scanner;
public class Eliza {
	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		Responder eliza = new Responder();
		System.out.println("Welcome to Eliza");
		boolean finished = false;
		while (!finished) {
			String input = in.nextLine();
			if (input.toLowerCase().trim().equals("quit")) {
				finished = true;
			} else {
				String response = eliza.generateResponse(input);
				System.out.println("Eliza said: " + response);
			}
		}
		System.out.println("Goodbye!");
	}
}
```

## A closer look at Eliza

- We need [Response.java](http://Response.java) class we wrote for Lecture 8

```Java
Responder eliza = new Responder();
```

- Input from the keyboard comes from System.in
- We can construct a Scanner which will read from the keyboard

```Java
Scanner in = new Scanner(System.in);
```

- When we use this scanner, it reads what we type on the keyboard

```Java
String input = in.nextLine();
```

- Then we can get a response from Eliza

```Java
String response = eliza.generateResponse(input);
System.out.println("Eliza said: " + response);
```

## Running the Eliza program

- We need [Responder.java](http://Responder.java) in the same directory as Eliza.java
- Here is the program being compiled and run…

p> javac Eliza.java

p> java Eliza

Welcome to Eliza

hello

Eliza said: Hi. What seems to be your problem?

i am depressed

Eliza said: Have you tried counselling?

no, i have been to busy with my computer

Eliza said: What do you think computers have to do with your problem?

it keeps breaking

Eliza said: Are such questions much on your mind?

quit

Goodbye!

## Writing utility programs

- You may want to write a utility program that you can run on your computer
- Here is a slightly contrived example, but lets say you want to easily compute the area of a circle and the area of a rectangle
- You would write a class to represent a Circle and a class to represent a rectangle
- The class for a Circle would have a variable holding the radius, a constructor to assign a value to radius, and a method called `getArea` which would return the result of the calculation pi * r$^2$﻿
- The class of the Rectangle would have variables representing the width and height, a constructor which would assign values to the variables, and also a getArea method that would return the result of the calculation width * height

## Designing a `main` method

- What we need from our main method is to be able to pass in when we run the program
- This utility does not need a UI and a way of reading input from the user
- We want to be able to get the area of a circle by running the program with one parameter:

java ShapesExample 14.5

Circle area is 660.519855417254

- And be able to get the area of a rectangle by running the program with two parameters:

java ShapesExample 10.2 9.15

Rectangle area is 93.33

## Alternatives based `args.length`

```Java
public static void main(String[] args) {
	if (args.length == 1) {
		double radius = //"read args[0] as a double
		Circle c = new Circle(radius);
		System.out.print("Circle area is ");
		System.out.println(c.getArea());
	} else if (args.length == 2) {
		double width = //read args[0] as a double
		double height = //read args[1] as a double
		Rectangle rect = new Rectangle(width, height);
		System.out.print("Rectangle area is ");
		System.out.println(rect.getArea());
	} else {
		System.out.println("Incorrect number of args");
	}
}
```

## Turning `String` into `double`

- The arguments arrive in our program as a String (containing digits and a decimal)
- Java provides utility classes for turning String values containing only digits and decimal points into number types
- Here is how to turn a String type into a double type (you get an error if the string contains anything other than digits and a decimal point):

```Java
double radius = Double.parseDouble(args[0]);
```

- Here is how to turn a String type into a float or an int:

```Java
String fText = "7.5";
float fValue = Float.parseFloat(fText);
String iText = "96";
int iValue = Integer.parseInt(fText);
```

## Final version of our main method

see above cba do tomorrow

## Processing without the Processing IDE

- See [here](https://happycoding.io/tutorials/java/processing-in-java) for a guide
- When we run this Processing program

```Java
void setup() {
	size(500, 500);
}

void draw() {
	background(64);
	ellipse(mouseX, mouseY, 20, 20);
}
```

- The program gets rewritten so that a main method is added and some other changes are made. see next slide…

## The Java version

```Java
import processing.core.PApplet;

public class MySketch extends PApplet {
	public void settings() {
		size(500, 500);
	}

	public void draw() {
		background(64);
		ellipse(mouseX, mouseY, 20, 20);
	}

	public static void main(String[] passedArgs) {
		String[] appletArgs = new String[] { "MySketch" };
		PApplet.main(appletArgs);
	}
}
```

## The differences

- Now we see what the setup/draw tab looks like written in Java, we could write that ourselves. However there are some new/different things to explain first
- The setup method is now called settings
- Both the settings and draw methods are marked as public
- We don’t have access to the color type. Use int instead

## A sketch class is a PApplet

- What is that extends bit?

```Java
public class MySketch extends PApplet {
```

- The full explanation of extends will be left until your next Java module.
- The short explanation is that it means MySketch is an extension of an already existing class called PApplet
- By extending a class we get everything that is declared in that class PLUS anything new we want to add
- The PApplet class is where width, height, fill, ellipse and all the other Processing specific stuff is defined so by extending PApplet we get all of that in MySketch too.

## Importing PApplet

- Where do we get PApplet from?

```Java
import processing.core.PApplet;
```

- The processing.core library comes with Processing and not the JDK. To compile this code, we need to tell Java where to find the processing.core. This requires something called a classpath

## What is a classpath?

- In an earlier slide we described how we can set a PATH that the command window uses to look for commands (i.e. to find javac and java)
- We can do the same thing with Java. To avoid putting absolutely all the classes we need in our project, we can provide a list of places where the Java system can find classes.
- These can be folder or jar files. The JAR format is the same as the ZIP format. It is an archive containing some compiled Java classes
- In an IDE we can simply add a list of folders and jar files to the project
- Using the command line we have to provide that list to the javac and java commands

## Adding Processing to the classpath

- First, you need to find where Processing was installed. On my computer it is in /home/beaumoaj/processing
- Inside that directory is another directory called core/library
- Inside that directory is the processing library core.jar
- The full path name is: /home/beaumoaj/processing/core/library/core.jar
- That path should be included in out classpath, and we also need to add “the current directory”. In a command window, the current directory is referred to as . (dot)
- We separate items on the classpath with a semi-colon ; (Windows)
- The classpath we need is:  
    /home/beaumoaj/processing/core/library/core.jar  
    

## Compiling and Running

- This is the command to compile [MySketch.java](http://MySketch.java) note you need to change the path to the location of YOUR core.jar and the command is all on one line

java -cp /home/beaumoaj/processing/core/library/core.jar MySketch.java

- This is the command to run the program

java -cp /home/beaumoaj/processing/core/library/core.jar MySketch

- There is no “stop” button, instead type CTRL+C in the command window to interrupt
- On windows the classpath separator is ; and not :

## Converting a PDE class

- In week 5 we had a bouncing ball example that used a class called Ball
- The Ball class uses width, height, fill, circle, etc that belong to Processing but not the Java
- We can fix that. The solution is to pass the main PApplet class as a parameter to the ball class

```Java
public class MySketch extends PApplet {
	Ball b;

	public void settings() {
		size{500, 500);
		b = new Ball(this);
	}
}
```

## Fixing the Ball class

```Java
import processing.core.PApplet;

class Ball {
	private float ballX; // X coordinate
	private float ballY; // Y coordinate
	private float ballWidth; // diameter
	private float speedX; // speed in X direction
	private float speedY; // speed in Y direction
	private PApplet pde;

	public Ball(PApple p) {
		pde = p;
		ballX = 10;
		ballY = pde.height/2;
		ballWidth = 60;
		initializeSpeed();
	}

	public void initializeSpeed() {
		speedX = pde.random(5, 10);
		speedY = pde.random(5, 10);
	}

	public void display() {
		pde.fill(pde.color(255, 0, 0-));
		pde.circle(ballX, ballY, ballWidth);
	}

	public void move() {
		ballX = ballX + speedX;
		ballX = pde.contrain(ballX, ballWidth/2, pde.width-(ballWidth/2));
		ballY = ballY + speedY;
		ballX = pde.contrain(ballY, ballWidth/2, pde.height-(ballWidth/2));
	}

	public void bounce() {
		if (ballX >= (pde.width-ballWidth/2) || ballX <= (0 + ballWidth/2)) {
			speedX = -speedX;
		}
		if (ballY >= (pde.height-ballWidth/2) || ballX <= (0 + ballWidth/2)) {
			speedY = -speedY;
		}
	}
}
```