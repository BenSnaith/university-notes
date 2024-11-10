## File Input and Output

- Error recovery cannot be ignored in input/output.
    - Users can make typing mistakes
    - The external environment may cause problems: files may be corrupt or deleted; the file store may be full; a directory may not be writeable
- The `java.io` package includes many classes which support I/O in a platform-independent way.
- The checked exception class `java.io.IOException` is the base class for all the exceptions `java.io` classes may raise
- Very brief discussion here of writing to file, reading from file, and I/O exception handling

## Commonly used classes in java.io

==Character based I/O.==

- Writer and reader: base interfaces.
- FileWriter: write characters into a File
- FileReader: read characters from a File
- PrintWriter: print things into a Writer (e.g. FileWriter)
- BufferedReader: read lines from a Reader (e.g. FileReader)

Byte-based I/O.

- InputStream and OutputSteam: base interfaces
- FileOutputStream: write bytes into a binary file
- FileInputStream: read bytes from a binary file
- We will not cover byte-based I/O in this module

## AddressBook with I/O: AddressBookFileHandler

- Class which handles the I/O for an AddressBook
- Separate from AddressBook as it has distinct responsibilities
- Contains an AddressBook object to simplify most methods
- Carries out basic error recovery for file system integrity
- Propagates exceptions to client (as most server classes)
- We will focus on these methods:
    
    `exportText(file)` Exports entries into a text file
    
    `importText(file)` Imports entries from a text file
    
    `exportJSON(file)` Export entries into a JSON file
    
    `inportJSON(file)` Import entries from a JSON file
    

## Exporting entries into text: first attempt

```Java
public void exportText(File file) throws IOException {
	FileWriter fw = new FileWriter(file);
	PrintWriter pw = new PrintWriter(fw);
	for (ContactDetails entry : book.itemsProperty()) {
		pw.println(entry.getName());
		pw.println(entry.getPhone());
		pw.println(entry.getAddress());
		pw.println();
	}
	pw.close();
	fw.close();
}
```

1. This is a server class — let caller deal with exceptions.
2. create FileWriter that writes characters into destination.
3. create PrintWriter that knows how to print things.

4-9. loop and use println to print things into file.

10-11. finish writing into the file and close it.

- This is far too optimistic: if something goes wrong before line 10, we will never get to close the file
- This may prevent users from opening the file, and we may be leaking resources (we can only keep so many files open)

## Exporting entries into text: using finally

```Java
public void exportText(File file) throws IOException {
	FileWriter fw = new FileWriter(file);
	PrintWriter pw = new PrintWriter(fw);
	try {
		for (ContactDetails entry : book.itemsProperty()) {
		pw.println(entry.getName());
		pw.println(entry.getPhone());
		pw.println(entry.getAddress());
		pw.println();
		}
	}
	finally {
		if (pw != null) pw.close();
		if (fw != null) fw.close();
	}
}
```

We can use a finally block to ensure `close()` is always called

## Exporting entries to text: using try-with-resources

```Java
public void exportText(File file) throws IOException {
	try (
		FileWriter fw = new FileWriter(file);
		PrintWriter pw = new PrintWriter(fw)
	) {
		for (ContactDetails entry : book.itemsProperty()) {
		pw.println(entry.getName());
		pw.println(entry.getPhone());
		pw.println(entry.getAddress());
		pw.println();
		}
	}
}
```

- Variant of try that takes 1+ declarations of Closeable or AutoCloseable objects, separated by a “;”
- Implicit finally block that closes all created objects
- Much easier to use — always use this if possible

## Importing entities from text

```Java
public void exportText(File file) throws IOException {
	try (
		FileWriter fw = new FileWriter(file);
		BufferedReader br = new BufferedReader(fw);
	) {
		String name = br.readLine();
		while(name != null) {
			String p = br.readLine();
			String a = br.readLine();
			br.readLine(); // Discard separating blank like
			book.addDetails(new ContactDetails(name, p, a);
			name = br.readLine();
		}
	}
}
```

1. create FileReader that reads characters from a file
2. create BufferedReader that reads lines from a Reader

Remember: we get an implicit finally block that closes both readers for us.

1. br.readLine() reads the first line
2. name being null means “end of file”

12. read the next name before we loop

8-10. read the other lines for this entry

1. create and add the ContactDetails object

## Parsing text with Scanner

- `Java.util.Scanner` provides more functionality. A scanner breaks the contents of a file into tokens using a delimiter patter.
- The default separator is white space, but the `useDelimiter` method can be used to change this: pass in a String or a regular expression
- You can also use Scanner to parse other data types, such as primitive types

```Java
public class TextScanner {
	private static void main(String[] args) throws ... {
		try(Scanner s = new Scanner(new File(fn))) {
			s.useDelimiter(System.lineSeparator());
			while(s.hasNext()) parseLine(s.next());
		}
	}
	
	private static void parseLine(String line) {
		Scanner lineScanner = new Scanner(line);
		lineScanner.useDelimiter("\\s*,\\s*");
		String name = lineScanner.next();
		int age - lineScanner.nextInt();
		boolean isCertified = lineScanner.nextBoolean();
		// do something with this info
		}
	}
```

- Parsing file with lines such as “Joe, 38, True”
- Outer Scanner in readFile reads one line at a time
- Inner Scanner parses comma delimited data, discarding whitespace on either side of the comma

## ScamSum: adding up numbers in text files

```Java
public class ScanSum {
	public static void main(String[] args) throws IOException {
		try(FileReader fr = new FileReader(args[0]);
				Scanner s = new Scanner(fr)) {
			s.useLocale(Locale.US);
			double sum = 0.0;
			while(s.hasNext()) sum += s.nextDouble();
			System.out.println(sum);
		}
	}
}
```

- Scanner can also read numbers n appropriate formats: for instance, it understands thousands separators
- In a US or UK locale, Scanner corrects reads the string 32,767 as an integer value
- Specifying the locale is important for internationalisation (usually shortened to “i18n”): making your program support multiple cultures.

## Handling format errors in ScanSum

```Java
while(s.hasNext()) {
	if(s.hesNextDouble()) {
		sum += s.nextDouble();
	} else {
		s.next(); // throw away next token
	}
}
```

- ScanSum has a serious shortcoming: if the input file contains any tokens that aren’t valid double values, it throws an exception and dies
- To fix that problem, we need to add some kind of error handling, Here’s how we can rewrite the scanning loop so that it skips over any token that isn’t a double

## Some comments on directly writing/reading text

Custom file formats are hard!

- Saving as text is good because it is human readable
- Saving as text is bad because it is human readable
- Writing files is easy: parsing is hard
- Detecting and reporting bad files helpfully is even harder

Recommendation: use a standard format

- XML is a popular format for documents
- JSON is very popular on websites
- YAML/TOML are common formats for config files

## Object Serialisation

Concept

- Serialising an object is turning it into a series of bytes
- Deserialising is the opposite: from bytes back to object
- This allows for writing objects to files, or sending them over the network: we can read the object back from those bytes

Support in Java

- Java has built-in capabilities for (de)serialising objects
- However, these are rarely used nowadays: it is more common to serialise to formats like XML/JSON/YAML
- We will focus on JSON, using the Google GSON library

## Exporting Entries to JSON

```Java
public void exportJson(File file) throws IOException {
	int nItems = book.itemsProperty.size();
	ContactDetails[] aDetails = book.itemsProperty.toArray(new ContactDetails[nItems]);
	try(
		FileWriter fw = new FileWriter(tmpFile);
		BufferedWriter bw = new BufferedWriter(fw)
	) {
		Gson gson = new Gson();
		gson.toJson(aDetails, bw);
	}
}
```

2-4. prepare a ContactDetails[] to be saved to JSON

6-7. open the file for writing using a try-with-resources

1. create a Gson object which understands JSON
2. use the toJson method, providing:
    1. The value we want to save in JSON format
    2. The Writer we want to write the JSON document into

## Importing Entries from JSON

```Java
public void importJson(File tmpFile) throws ... {
	try(
		FileWriter fw = new FileWriter(tmpFile);
		BufferedWriter bw = new BufferedWriter(fw)
	) {
		Gson gson = new Gson();
		ContactDetails[] aDetails = gson.fromJson(br, ContactDetails[].class());
		for(ContactDetails details : aDetails) {
			book.addDetails(details);
		}
	}
}
```

3-4. open the file for reading with try-with-resources

1. create a Gson object that understands JSON

7-8. use the fromJson method, providing:

- the Reader to read from
- The class of the objects we want to read (syntax. Type.class)

9-10. loop over the array, adding entries to the AddressBook

## How do we know if our program works?

Donald Knuth (1974 ACM Turing Award)

- Beware of bugs in the above code; I have only proved it correct, not tried it

  

- For some programs, you can try to mathematically prove they are correct
- However, doing this is too expensive / complicated for most developers and most systems
- Even if you had proof, your program is running on top of various libraries, which run on top of the JVM, which runs on top of Windows, which runs on top of your BIOS, which runs on your CPU microcode… and any of these can have bugs
- In the end, we always have to run our programs with the intent to find bugs ← this is testing

## Importance of test design

```Java
public int sum(int a, int b) {
	return a + b;
}
```

Problem

- Take this simple method above, which adds two sums
- How many possible inputs exist for this toy method
- int has 2^32 possible values, and we have two
- 2^64 possible inputs: too many to try them all!

Solution

- We need to be smart about which inputs to try: test design

## System testing

_Run the whole program, interacting with it as a normal user:_

- We can cover large parts of our code in a single test
- Easy to consider things like animation quality, music, etc
- Hard to automate
- Hard to trigger rare cases
- Hard to pinpoint root causes of problems

## Unit Testing

Try the methods of a specific “unit”

- Can consider both the common and rare cases easily
- Less code to debug when we find a bug
- Easy to automate
- Some things are hard to test this way
- In the short term, it takes more work

## Conclusion

We need both: system testing to cover the big picture, and unit testing so we can cover the details

## AddressBook Example: Sorted Insertion

Why is it needed?

- The GUI want AddressBook to have an itemProperty() with a sorted list of its ContactDetails
- Internally, AddressBook uses a map, with phone and name keys for each ContactDetails
- AddressBook listens to the map, updating the itemsProperty() when new keys are entered
- We need to be able to quickly insert a new ContactDetails into the itemsProperty() while keeping it sorted

How does it work?

- Suppose we have a sorted list, e.g. (1, 5, 9, 13, 14)
- We want to insert 6 as quickly as possible, keeping list sorted
- We use a “binary chop” approach to pick where to insert it:
    - We start with full range of candidate positions
        - 0 included to 5 excluded: [0, 5]
    - Compare 6 with middle element (at index 5/2 = 2): 6 < 9
        - We focus on left half of [0, 5], excluding middle: [0, 2]
    - Compare 6 with middle element (at index 2/2 = 1): 6 > 5
        - We focus on right half of [0, 2], excluding middle: [2, 2]
    - [2, 2] is an empty range:
        - This means we can insert 6 at index 2
- We will end up with (1, 5, 6, 9, 13, 14), as expected

Problem?

- This is very easy to get wrong!
- To gain confidence, we are going to write test for it
- How do we come up with tests?

Approaches for test design

- Black Box: looking at the specification, we come up with various types of inputs and what the output should be
- White Box: looking at the code, we come up with inputs that will run the program in every possible way
- We will always need to combine both approaches

## Black box approach for sorted insertion

Input and outputs

- We provide an element and a sorted list
- We should get a sorted list with the new element
- What are the possible causes

Thinking about the various possibilities

- For the list: could be empty, have 1 element, or have 2+
- For the element: could end up at the beginning, in the middle, or the end
- The element could also be equal to one of the elements already in the list
- We take all these options and combine them into classes

## White box approach for sorted insertions

```Java
when you are sat in the lecture do this please 
new new new new new mew new new
```

- A white box approach looks at the code and comes up with tests that trigger every possible path through the program
- Look at the conditions and try to come up with an input that meets them, then think about the output you should get

## Other test designing approaches

Considering well-known scenarios

- What if we insert numbers 1 to 5 in order?
- What if we insert those numbers in reverse order

Property-based testing

- If we insert a list of numbers in any order, we know we should get a list with those same numbers back, in sorted order
- That means we could potentially try inserting the numbers 1 to 10 in some order, and we should always get (1, 2, …, 10)
- There are 10! = 3,628,800 possible ways to order 10 elements, but we could randomly sample 200 ways
- If one of those inputs fails, we can turn it into a test of its own to help us debug the problem without the randomness

## A refresher on JUnit and assertions

```Java
public class SortedCollectionsTest {
	@Test
	public void insertIntoEmpty() {
		List<Integer> l = new ArrayList<>();
		SortedCollections.sortedInsertion(0, 1);
		assertEquals(Arrays.asList(0), 1);
	}
	// ...
}
```

- Unit tests are written as methods annotated with @Test in a test class (usually with name ending in Test)
- JUnit provides a number of static methods for doing test assertions (e.g. assertEquals)
- Don’t confuse them with Java assertions, which are for internal optional checks in normal class:
    - assert x > 0 : “x must be positive”

## Available JUnit test assertions: equality

- For most types( [] means “optional”):
    - assertEquals(expected, obtained[, msg]
    - assertNotEquals(expected, obtained[, msg])
- For float and double, a delta is needed(1/3.0 will not be exactly equal to 0.33, but do we care?)
    - assertEquals(expected, obtained, delta[, msg])
    - assertNotEquals(expected, obtained, delta[, msg])
    - Usually delta is small value
- For arrays:
    - assertArrayEquals(expected, obtained[, msg])
    - assertArrayNotEquals(expected, obtained[, msg])

## Available JUnit test assertions: other types

- For true/false
    - assertTrue(obtained[, msg])
    - assertFalse(obtained[, msg])
- For null
    - assertNull(obtained[, msg])
    - assertNotNull(obtained[, msg])
- To check if two variables point to the same object
    - assertSame(expected, obtained[, msg])
    - assertNotSame(expected, obtained[, msg])

## Available JUnit test assertions: manual failing

```Java
assertTrue(x > 0, "x was not > 0");
// same thing
if(x <= 0) fail("x was not > 0");
```

- If we want to do the check ourself and then manually fail, we can always call the fail(String) JUnit static method
- Can be useful in some corner cases (e.g. exception handling)

## Testing the AddressBookFileHandler

Method to test

- exportEntries(File)
- importEntries(File)
- load(File)
- save(File)

Method relationships are useful for black box testing

- What save saves, load should load
- What exportEntries exports, importEntires should import
- This means we can design test cases by:
    1. Populating an AddressBook
    2. Saving it / exporting its entries
    3. Loading / importing it back
    4. Comparing with the original

## JUnit test setup / teardown results

```Java
public class AddressBookFileHandlerTest {
	private AddressBook book;
	private AddressBookFileHandler handler;
	
	@BeforeEach public void setUp() {
		book = new AddressBook();
		hander = new AddressBookFileHandler(book);
	}
	
	...
}
```

- We may need to run some code before each of our tests: e.g. creating helper objects or allocating resources
- For that, we can have a setup methods annotated with @BeforeEach (name does not matter)
- We can also have a @AfterEach teardown method to clean up after each test case (e.g. deleting temp files)

## Testing save + load

```Java
public class AddressBookFileHandlerTest {
	...
	@Test public void loadSaveEmpty() throws Exception {
		assertSaveThenLoadIsEqual();
	}
	@Test public void loadSaveOneEntry() throws Exception {
		book.addDetails(new ContactDetails("john doe", "123", "e"));
		assertSaveThenLoadIsEqual();
	}
	...
}
```

- We have two very similar tests:
    - Save + load empty book
    - Save + load book with 1 entry
- We have our own assertSaveTheLoadIsEqual assertion (DRY!)
- Note how we let Exceptions propagate to JUnit: if an exception is thrown, JUnit will fail the test (red result)

## Creating custom test assertions

```Java
private void assertSaveThenLoadIsEqual() throws ... {
	File tmpFile = File.createTempFile("test", ".abk");
	tmpFile.deleteOnExit();
	handler.save(tmpFile());
	AddressBook loaded = AddressBookFileHandler.load(tmpFile);
	
	assertEquals(book, loaded)
	assertEquals(book.itemsProperty().size()), loaded.itemsProperty().size());
}
```

- A custom test assertion is just a regular Java method, without @Test as it is not a test case to be run by JUnit
- Remember: test code should still be good code — you can use inheritance / composition / private methods as usual

## Testing for failure

```Java
@Test public void loadNull() throws Exception {
	try {
		AddressBookFileHandler.load(null);
		fail("Expected a NullPointerException");
	} catch (NullPointerException ex) {}
}

@Test public void loadMissing() throws Exception {
	assertThrows(FileNotFoundException.class, () -> {
		AddressBookFileHandler.load(new File("idonotexist.abk"));
	});
}
```

- We should test that our program fails the way we expect, too
- To do this, we have two approaches:
    - Use try + catch and the fail JUnit static method
    - Use the assertThrows JUnit test assertion

## Finding missing tests with coverage reports

Common situation

- We have written a number of test cases, and we think we did pretty well: could we have missed a test case, though?
- We need to decide if we have done “enough” testing

Approaches

- We can follow a formal requirement, e.g. “run all lines at least once” or “run all executions branches at least once”
- Having 100% coverage of something can be expensive
    - Pareto rule: 80% of the work takes 20% of the time, meaning the remaining 20% of the work takes 80% of the time
- May be better to simply check if we are missing something “important”

## Test coverage with EclEmma and JUnit: launching

- If using your own PC, you will need EclEmma
- You can install from the eclipse marketplace