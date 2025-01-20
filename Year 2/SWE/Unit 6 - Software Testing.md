### Unit Objectives

- Importance.
- Black-box vs White-box testing.
- Testing Techniques.
- Levels of Testing.
- Testing documentation and planning.
- JUnit examples.
- Test-Driven Development.

### What is Software Testing

- A process to validate a software application.
- Observing, recording and comparing the behaviour (output) of the software with the intended behaviour and output.
- Main purpose of testing is to try __find errors__.
	- Is it always done?

### When to do testing?

- Testing should be done __early__ and __often__.
- No need to wait until all operations of a software component are fully implemented.
- Even a smallest change on a piece of code may __invalidate__ the entire system!
	- Testing should be done __whenever changes have been made__

### Test Data

- __Test data__ should test the software at its limits and test business rules.
- Test data should include:
	- Extreme Values:
			(e.g., Out-of-Bounds)
	- Borderline Values:
			(e.g., -1, 0.9999)
	- Invalid Combinations of Values:
			(e.g., age=3, marital_status=true)
	- Nonsensical Values:
			(e.g., negative order line quantities)
	- Heavy Loads
			(e.g., are performance requirements met?)

### Who should perform testing?

- Ideally, test scripts should be built and executed by __specialist test teams__ who have access to software.
- Testing should also be done by business and systems analysts.
- In eXtreme Programming (XP), programmers are expected to write __test harnesses:__ a software framework that imitates missing infrastructure allowing automated testing.
- Intended users of the system should test against requirements, aka __user acceptance testing__.

### What kind of testing?

- __Black Box Testing__ seeks to establish whether the end-product does what it's meant to.
   
Checking FR, and is usually done by Systems Analysts.

- __White Box Testing__ seeks to establish whether the end-product delivers a good solution, not just a solution to the problem.
  
Checking RF/NFR, and is usually done by the developers.

### Various types of Testing

- __Unit Testing:__ ensures that individual classes work correctly.
- __Interface Testing:__ validates the function exposed by components.
- __Integration Testing:__ establishes whether all components in the system work correctly together.
- __Subsystem Testing:__ checks if each subsystem works correctly and delivers the required functionality.
- __System Testing:__ check if the WHOLE system works seamlessly.
- __Robustness Testing:__ establish the ability of the software application in handling anomalies (being __trustworthy__).
- __Mutation Testing:__ introduce statement/value/decision "mutations" on purpose, to see how the system reacts.
- __Performance Testing:__ check if the system is fast enough and it uses an acceptance amount of memory (like a stress test).

### Different Levels of Testing

- __Level 1:__ Testing components (i.e. classes), then program (i.e. use cases), then suites (i.e. application).
- __Level 2 (Alpha Testing or Verification):__ Execute programs in a simulated environment and test inputs and outputs.
- __Level 3 (Beta Testing or Validation):__ test in a live use environment and test for response times, performance under load and recovery from failure, etc.

### Summary of Testing Activities

![[Pasted image 20241211163923.png]]

### Regression Testing

- __Regressing Testing__ is a process in which the software is __retested__ so as to ensure that its behaviour has not been compromised by the addition of new, or change to existing code.
- It facilitates faster development:
	- It reduces risk of changes
	- Unexpected effect can be found quickly.
	- Ability to run thousands of tests in one click.

### When is Regression Testing needed?

- __Regression Testing__ is important but van be very time and cost consuming.
	- Requires capturing of data, analysis, reporting, etc.
- Consider the following scenario.

__Question:__
![[Pasted image 20241211164229.png]]

__Answer:__
![[Pasted image 20241211164323.png]]

### Test Documents (Plans/Cases/Results)

- __Test Plans__
	- Written before the tests are carried out!
	- Written, in fact, before the code is written.
	- Contains test cases.
- __Test Cases__ are specified with the following formation:
	1. Test data.
	2. Expected Outcomes.
	3. Description of the Test.
	4. Test Environment and Configuration.
- __Test Results__
	- Used for analysis, recorded in a spreadsheet, database or a specialist package (e.g. Jira).
	- Record when tests are failed or passed.
	- Include statistics, e.g. percentage of passed/failed.
	- Ideally should be linked to requirements (traceability!).
	- Error results should be recorded in a fault reporting package, with enough details for development to __reproduce__ them with a view to fixing the bugs.

### Test Planning - Steps

1. Define what is meant by a `Testing Unit`.
2. Determine the types of testing to be performed.
3. Determine the extent of testing (i.e. prioritise the tests).
4. Determine how to document the testing procedure.
5. Determine __input sources__.
6. Decide who will performed which tests.
7. Estimate __resources__.
8. Identify __metrics__ to be collected.

### Determine the Extent of Testing

- Software should be thoroughly tested before __release__, but when should testing stop?
- There is no "one size fits all" scheme, in software testing.
- The testing team should establish a set of stopping criteria:
	- A tested is unable to find another defect in __n__ minutes of testing (where __n__ may be any +ve integer, e.g. 5, 10, 30, 100).
	- When all __nominal__, __boundary__ and __out-of-bounds__ test data show no defect.
	- When a given __checklist__ of test types has been completed.
	- When testing runs out of its scheduled times (DANGEROUS).

### Unit Testing

- __Unit Testing__ is performed to test parts (classes and their methods) of an application __in isolation__.
- Black Box Unit Testing:
	- __Equivalence Partitioning:__ divide inputs values into equivalent groups.
	- __Boundary Values Analysis:__ test as boundary conditions.
- White Box Unit Testing:
	- __Code Coverage:__ test cases cause every line of code (__statement__), all conditions (__branch__) and all possible flows (__path__), from entry to exit, to be executed.

### Unit Testing - Path Coverage Example

- Performing __path coverage__ on the following methods:

```cpp
class Example
{
private:
	static void showResult(int guessed, int toGuess)
	{
		if(guessed == toGuess)
		{
			std::cout << "Well Done! You've Guessed It!" << std::endl;
		}
		if(guessed > toGuess)
		{
			std::cout << "Sorry! Your Guess Is Too High!" << std::endl;
		}
		else
		{
			std::cout << "Sorry! Your Guess Is Too Low!" << std::endl;
		}

		std::endl << "The Number I Have In Mind Is: %d\n", toGuess);
	}
}
```

- A test case for each __distinct path__ path:
	- `showResult(8, 8) : 2 -> 3 -> 11`
	- `showResult(9, 8) : 2 -> 5 -> 6 -> 11`
	- `showResult(7, 8) : 2 -> 5 -> 8 -> 9 -> 11`

### Using Assertions

- __Assertions__ are statements in Java which ensure the correctness of assumptions.
- Allow us to enforce business rules and catch any mistakes.
- Allow us to check for parameter and return values.

```cpp
public:
	void checkCanDrive(int age)
	{
		assert age >= 17 : "Cannot Drive";
		std::cout << "Can Drive At: %d\n", age);
	}
```

### Unit Testing with JUnit

- __JUnit__ is a framework for unit testing which facilitates the writing of repeatable tests.
- To use JUnit 5, typically one imports:
	- `org.junit.jupiter.api.Assertions`
	- `org.junit.jupiter.api.Test`
- Annotates a test method with a @Test
- Uses assert methods, i.e. `assertFalse`, `assertTrue`, `assertEquals`, `assertThrows`, `etc`.

```java
// Switch to Java for this
@Test
public void testAddingStaff() {
	StaffManager sm = new StaffManager();
	sm.addStaff("Lucy", "Bastin");
	Assertions.assertFalse(sm.getAllStaff().isEmpty());
	Assertions.assertEquals(1, sm.getAllStaff().size());
}
```

### JUnit Test Life Cycle - Fixtures

- __Fixtures__ allow you to set up a testing environment: prepare the baseline of your tests.
- Usually fixtures have the following life cycle

```java
@BeforeAll
@BeforeEach
@Test
@AfterEach
@AfterAll
```

- You may want to use the "Before" annotations for the preparation of test data, and the "After" annotations for housekeeping

### Test-Driven Development

- A different approach to writing software.
- The development of the application is thus driven by the test cases solely.
- Writing test cases __before__ writing any source code.
- Code that does not address the issues in the test cases will not be written.
- A testing framework such as JUnit can be used to facilitate TDD.

### Test-Driven Development Process

![[Pasted image 20241211171930.png]]

### Advantages of TDD

- Test cases __ensure a good statement coverage__.
- Only code required to address the requirements is written; __no redundancy__.
- __Rapid feedback__ on the written code.
- Test suite availability for further testing purposes, e.g., __regression testing__





