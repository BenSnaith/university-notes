## Goals for this lecture

- Understand the concepts of unit testing and test-driven development
- Set up and Eclipse project for automated unit testing with JUnit
- Understand the basic structure of JUnit test cases
- Import existing projects from Blackboard to Eclipse
- Use the AutoFeedback platform to test your code before submission

## How do you check your code works?

From toy programs to real programs

- For a toy program, you can just run it and see if it works
- Real programs have many options, features, and corner cases: you can’t be trying them all every time you make a change.

Real programs need to be tested at multiple levels

1. Individual functions and classes (unit testing)
2. Multiple classes together (integration testing)
3. Whole system at once (system testing)

You gain confidence in your building blocks, which allows you to then test how you put them together and isolate your program

## The testing triangle

INSERT TESTING TRIANGLE

- We have a foundation of many small, fast and cheap unit tests
- Then a smaller number of integration tests in the middle
- Then a few tests for the whole system, which are the slowest

## What is unit testing?

Basic idea

- You test a single unit in your system
- In Java, this is typically a single function or a single class
- You test it in isolation of everything else
- You normally use a unit testing library to help you

What do you test?

- When I give it valid inputs, does it produce a valid result
- When I give invalid inputs, does it fail as expected

## How do I do unit testing in Java?

```Java
public class Sum
{
	public int sum(int a, int b) { return a + b; }
}

public class SumTest
{
	@Test
	public void testZero()
	{
		Sum c = new Sum();                      // Arrange
		int result = c.sum(0, 5);               // Act
		assertEquals("0 + 5 = 5", 5, result);   // Assert
	}
}
```

- Add a unit testing library to your project (e.g. JUnit for Java)
- Write @Test functions in a test class: each one is like a small main method, with three parts:
    - Arrange: set up your test data
    - Act: call your function under test
    - Assert: check results with JUnit’s `assertX` functions
- Write your function and run your test against it.

## What is TDD?

“Traditional” order

1. You write your code
2. You write whatever tests you can think of
3. Your tests pass: hopefully you didn’t forget anything

Test-driven development flips them around

1. You write the tests about what your code doesn’t do yet
2. You write just enough code to pass that
3. If you need more features, go to step 1

How can TDD be useful?

- Forces you to think how the function should look first
- You are confident your tests are useful and thorough
- Your function does not have more code than needed

## What are we going to do now?

1. Setup and Eclipse project for JUnit from scratch, and use TDD to write an RPG-style attack damage calculator
2. Import an existing calendar booking project, use TDD to complete it, and use an external tool to validate our code before submission

## Requirements for the damage calculator

|   |
|---|
|DamageCalculator|
|FIRE : int = 0 {read-only}  <br>GRASS : int = FIRE+1 {read-only}  <br>WATER : int = GRASS+1 {read-only}|
|+ calculateDamage(int baseDamage, int attackType, int defendType): int|

The method calculateDamage should multiply baseDamage by 0.5 or 2 depending on the attack and defend types and return the result…

|   |   |   |   |
|---|---|---|---|
||Fire|Grass|Water|
|Fire|half|double|half|
|Grass|half|half|double|
|Water|double|half|half|

## New project setup (I): name and location

- Go to “File → New Java Project”
- Enter project name as usual
- Watch how Eclipse creates the project in your workspace folder by default
- Press Finish: we will use the Project Properties to set up the project (more powerful)

## New project setup (II): no module-info.java

- Remember that for any Java9+ project, Eclipse will ask you if you want a `[module-info.java](http://module-info.java)` file
- This is only needed for JavaFX (later in the module), and it otherwise complicates the project for no reason — click on “Don’t Create”

## New project setup (III): project properties

- We need to create a test-specific source folder and add the JUnit library to our project
- The options in the New Project dialog are not enough: we need the full “Project Properties” window
- Right-click on the project and select Properties (usually, it’s the last item)

## New project setup (IV): test source folder

1. Select “Java Build Path” on the left, select “Source” tab
2. Use “Add Folder…” to add a src-test folder
3. Double-click on “Contains test sources”
4. Check “Allow output folders for source folders”
5. Double click on “Output folder”, select “Specific o. folder”
6. Enter bin-test, click on OK

## New project setup (V): JUnit library

1. Select “Libraries” tab, select “Classpath”, then “Add Library”
2. Select “JUnit”, “Next”, and then “JUnit 5”
3. Expand “JUnit 5” and double click on “Visible only for test sources”: this ensures we can only use it from src-test
4. Click on “Finish”

## New project setup (VI): checking things

Your project should now look like this

- The project should be a Java project
- src: normal source folder
- src-test: test source folder
- Java Runtime Environment System Library should use a JavaSE-11 or newer execution environment
- JUnit 5 library should be listed and be only available in test code

## Creating out JUnit test class

- Right-click on `src-test`
- Select “New → Class”
- Create a class called `DamageCalculatorTest`
- Convention: class `X` is tested in class `XTest`

## Writing a test case

- A Test class is just like a normal Java class that you are used to writing.
- Test are methods in that class that are annotated with @Test
- The code we are testing (e.g. `calculate()` ) should have an expected result
- We compare the expected result with an observed result
- We use one of the JUNIT methods, e.g. assertequals, to compare the expected result with the observed result. If they are different, the test will fail. If they are the same, the test passes.

Often the full requirements are complex (we have NINE different possible cases). Focus on ONE case and test that first. We will write a test for the “Fire” (attack) vs “Fire” (Defend) case.

```Java
package uk.ac.aston.oop.damage;

import org.junit.jupiter.api.Test;

public class DamageCalculatorTest
{
	@Test
	public void testFireVsFire()
	{
		// Arrange
		DamageCalculator calc = new DamageCalculator();
		// Act
		int damage = calc.calculate(30, DamageCalculator.FIRE, DamageCalculator.FIRE);
		// Assert
		assertEquals("Fire vs Fire does half damage", 15, damage);
	}
}
```

- In TDD fashion, we write the test before the normal code: we can play around with how it should feel before we write.

## Writing out first test case: importing assertEquals

ADD THE PHOTO ABOUT THE STATIC

- We can solve the missing import file for the JUnit `assertEquals` by using one of Eclipse’s “Quick Fixes”
- To activate it, you have two options:
    - Click on the lightbulb with red cross to the left of the line number
    - Put text cursor on `assertEquals` and press CTRL+1
- Select the “Add static import for Assert.assertEquals”
    - Assert has many other useful assertions
    - Assertions would also work (new in JUnit 5)
- Save in order to trigger recompilation: squigglie dissapears

## Writing our first test: creating missing class

ADD THE PHOTO ABOUT CREATING THE MISSING CLASS

- We can create DamageCalculator manually, or we can use a Quick Fix
- In this case, we’ll activate the Quick Fixes as usual and pick “Create class”

## Writing our first test: creating missing class (II)

PHOTO WITH THE CLASS INTERFACE PHOTO

- Eclipse has already filled in the name (DamageCalculator)
- It’s a normal class. not a test class: we change the source folder to src
- Click on Finish, and our basic class structure is ready

## Double checking our class structure

INSERT THE CLASS PHOTO

- DamageCalculator class in uk.ac.aston.oop.damage package, in src source folder
- DamageCalculatorTest class in uk.ac.aston.oop.damage package, in src-test test source folder
- This separation allows us to only package normal code when we distribute our program (making the download smaller)
- Note: .java files should have filled-in “J”s, meaning they are in a source folder and will be compiled

## Writing our first test: creating the FIRE constant

```Java
package uk.ac.aston.oop.damage;

public class DamageCalculator
{
	public static final int FIRE = 0;
}
```

- The next error to fix is the missing DamageCalculator.FIRE
- `final`: cannot be charged after it is set
- `static`: we have only one copy for the whole class (rather than one per object): that’s how we can just type  
    ClassName.staticVarName  
    
- Static final variables are typically NAMED_LIKE_THIS
- We will eventually have a constant for each attack type

## Writing our stub implementation

```Java
package uk.ac.aston.oop.damage;

public class DamageControl
{
	public static final int FIRE = 0;

	public int calculate(int baseDamage, int attackType, int defendType)
	{
		return 0;
	}
}
```

- In test-driven fashion, we write just enough of the calculate code so it compiles
- We have our base damage and attacking/defending types
- We just return 0 for now: we want to make sure our test says this is not OK (otherwise it is a useless test!)

## First run of out test case: launching

To run all JUnit tests in your project, right-click on the project, right-click on the project and select “Run As - JUnit Test”

## First run of our test case: results

INSERT TEST RESULT PHOTO

- The JUnit view will pop up, and you will see a large red bar: testFireVsFire failed (blue X means assertion failure)
- The “Failure Trace” says we wanted 15 but got 0
- The test is working as it should: let’s fix the function

## Write code to pass the “fire vs fire” test

```Java
package uk.ac.aston.oop.damage;

public class DamageControl
{
	public static final int FIRE = 0;

	public int calculate(int baseDamage, int attackType, int defendType)
	{
		return baseDamage/2;
	}
}
```

- We write just enough code to pass this test
- The idea is that any extra code should be motivated by more tests: by the time we’re done, we’ll have good code and good tests.

## Rerun and pass test

INSERT THE PASSED TEST THING

- Bar is green: all tests passed!
- Obviously, we’re not done yet
- We need to repeat this “add tests, fail tests, fix code, pass tests” cycle a few times

## Writing the “fire vs grass” test

```Java
	@Test
		public void testFireVsGrass()
		{
			DamageCalculator calc = new DamageCalculator();
			int damage = calc.calculate(15, DamageCalculator.FIRE, DamageCalculator.GRASS);
			assertEquals("Fire vs Grass does double damage", 30, damage);
		}
```

- We add a test for fire attacking grass (should do 2x damage)
- We add the GRASS constant to DamageCalculator (Equal to FIRE+1)

## Failing the “fire vs grass” test

INSERT THE FAIL PIC

- We rerun the tests: we pass the old one and fail the new one
- We confirm we need to handle fire vs grass in our code.

## Complete the fire element implementation

```Java
package uk.ac.aston.oop.damage;

public class DamageControl
{
	public static final int FIRE = 0;
	public static final int GRASS = FIRE + 1;

	public int calculate(int baseDamage, int attackType, int defendType)
	{
		if (defendType == GRASS)
		{
			return baseDamage * 2;
		}
		else
		{
			return baseDamage / 2;
		}
	}
}
```

## Reducing repetition in Arrange with @BeforeEach

### @BeforeEach functions are called before each test.

```Java
private DamageCalculator calc;

@BeforeEach
	public void setUp()
	{
		this.calc = new DamageCalculator();
	}

	// This will apply to all of the tests and reduces the repetiton of creating the calc obj.
```

## Add the rest of the tests: fire and grass

```Java
//@Test
public void testFireVsWater()
{
	int damage = calc.calculate(30, DamageCalculator.FIRE, DamageCalculator.WATER);
	assertsEquals("Fire vs Water does half damage", 15, damage);
}
//@Test
public void testGrassVsFire()
{
	int damage = calc.calculate(15, DamageCalculator.GRASS, DamageCalculator.FIRE);
	assertsEquals("Grass vs Fire does half damage", 7, damage);
}
//@Test
public void testGrassVsGrass()
{
	int damage = calc.calculate(15, DamageCalculator.GRASS, DamageCalculator.GRASS);
	assertsEquals("Grass vs Grass does half damage", 7, damage);
}
//@Test
public void testGrassVsWater()
{
	int damage = calc.calculate(15, DamageCalculator.GRASS, DamageCalculator.WATER);
	assertsEquals("Grass vs Water does double damage", 30, damage);
}
//@Test
public void testWaterVsFire()
{
	int damage = calc.calculate(15, DamageCalculator.WATER, DamageCalculator.FIRE);
	assertsEquals("Water vs Fire does half damage", 30, damage);
}
//@Test
public void testWaterVsGrass()
{
	int damage = calc.calculate(15, DamageCalculator.WATER, DamageCalculator.GRASS);
	assertsEquals("Water vs Grass does half damage", 7, damage);
}
//@Test
public void testWaterVsWater()
{
	int damage = calc.calculate(15, DamageCalculator.WATER, DamageCalculator.WATER);
	assertsEquals("Water vs Water does half damage", 7, damage);
}
```

- More of the same!
- We now run the tests, and see a few of them fail, time to complete the code.

## Complete the implementation

INSERT THE MF IMPLEMENTATION AND I CANT BE ARSED TO WRITE IT ALL OUT ITS 23:45

## All tests pass: are we done?

- All 9 tests are now passing: bar is green
- We’re mostly done, but that code had a lot of repetition let’s fix that.

## Refactor our code

```Java
package uk.ac.aston.oop.damage;

public class DamageCalculator
{
	public static final int FIRE = 0;
	public static final int GRASS = FIRE + 1;
	public static final int WATER = GRASS + 1;

	public int calculate(int baseDamage, int attackType, int defendType)
	{
		if(isStrongAgainst(attackType, defendType))
		{
			return baseDamage * 2;
		}
		else
		{
			return baseDamage / 2;
		}
	}
	
	private boolean isStrongAgainst(int attackType, int defendType)
	{
		return attackType == FIRE && defendType == GRASS
		|| attackType == GRASS && defendType == WATER
		|| attackType == WATER && defendType == FIRE;
	}
}
```

## Run tests for all elements (after refactorize)

- Everything still works
- This is the main benefit of automated unit testing: our tests stay with us, and we can rerun then at the click of a button
- The tests are a safety net that allows us to be more confident about improving our code without breaking anything
- Real software can have hundreds/thousands of these!

## Working from existing code

You will rarely start from scratch

- In most jobs, there will be existing code you have to work on
- Being able to read code is even more important than writing it!

Most labs in TP2 have starting code

- Usually, you will download ZIP from Blackboard
- You will import it into Eclipse and perform some tasks
- Then you will export it into a ZIP and upload it to Blackboard

## Importing an existing project in Eclipse (i)

- Download the ZIP from Blackboard
- In Eclipse, go to “File → Import… → General → Existing Projects into Workspace”

## Importing an existing project in Eclipse (ii)

- Click on “Next”, pick “Select archive file”
- Browse to the downloaded ZIP file and click on “Finish”

## Checking your setup

- You’ll notice a small “M” over the project: we are using Maven
- Maven reads the pom.xml file for instructions: you won’t need to change it in CS1OOP
- Maven downloads JUnit from Maven Central and sets up the project
- We have src and src-test source folders as usual, with files that have filled-in “J”s
- We’ll talk about .launch later.

## Problem to solve: Calendar project

Existing code:

- This is part of a calendar application
- We have Appointments to fit in a Day
- Appointments have a description and a duration in hours
- We have to write the Day::makeAppointment function (C++?)

Day::makeAppointment

- There are certain hours available for making appointments (from START_OF_DAY to FINAL_APPOINTMENT_TIME)
- Appointments should not overlap
- makeAppointment should return true if the appointment worked, and false if it did not.