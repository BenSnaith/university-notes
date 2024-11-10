## Where does `String` come from?

- `String` is a class, just like the classes of our own.
- Whenever we want a character sequence, we use the `String` class.
- The `String` class comes from the Java classes we get for “free” when we write a Java program. Processing gets those too because it is built on top of Java
- There is documentation for the String class. The Processing reference has some information [here](http://processing.org/reference/String.html)

## What is a `String`?

- The Java documentation says that Strings are constant; their values cannot be changed after they are created
- It also says that

```Java
String str = "abc";
```

is equivalent to

```Java
char data[] = {'a', 'b', 'c'};
String str = new String(data);
```

- `String` data is really a convenience class to avoid us having to do all of that work with the `chars`.
- You can think of a string as really an array of `char` but all packaged up into a class that has functions for all the commons ways you want to process text.

## What can i do with a `String`?

- Two common functions are “get the character at a specific index” for which we use `charAt(i)`, and “how long is the `String`” for which we use `length()`

```Java
String message = "a_bunch_of_text_in_a_String";
char c = message.charAt(3);
println(c);
int length = message.length();
println(length);
```

- The code above produces the outputs:

`u`

`27`

- Note that using `String` is so common, we don’t bother with a constructor.

```Java
String message = new String("a_bunch_of_text_in_a_String");
```

## A `String` is immutable

- Remember we said earlier that once a String has been constructed, it cannot be changed.
- ==The technical term for that is that is it immutable. An immutable object is one whose data can never be changed.==
- This means that `String` functions that change a string have to return a new copy of the string, so it makes a new one and then assigns it to the original behind the scenes.

```Java
String message = "a bunch of text is a String";
String upper = message.toUpperCase();
println(upper);
```

## Comparing strings

- What would you expect this code to output

```Java
String s = "hello";
String s2 = "hello";
String s3 = new String("hello");
print("s is "); println(s);
print("s2 is "); println(s2);
print("s3 is "); println(s3);
print("s == s2 is ");
println(s == s2);
print("s == s3 is ");
println(s == s3);
```

## Unexpected output

- The answer to the question on the previous slide is not what you expect

```Java
"""
s is hello
s2 is hello
s3 is hello
s == s2 is true
s == s3 is false
"""
```

- Both `s` and `s3` contain the same text, `hello`
- BUT the expression s == s3 returns false.
- WHY?

## First: Why doesn’t == work on `String`?

- Technically, the == operator compares the two values on each side of the operator
- This is fine if we have something like this:

```Java
int n1 = 7;
int n2 = 5 + 2;
```

the expression `(n1 == n2)` compares the values (both 7) so the expression evaluates to `true`

- However, if we have something like this

```Java
char[] a1 = {'h', 'e', 'l', 'l', 'o'};
char[] a2 = {'h', 'e', 'l', 'l', 'o'};
```

the expression `(a1 == a2)` returns `false`

- The values held in a1 and a2 are actually references, which refer to two DIFFERENT addresses where the arrays are stored
- ==This is where REFERENCE DATA TYPES come from==

## Comparing `String` variables

- Remember, we said that the String class is really just class a class whose data is an array of characters
- Java tries to be efficient with the storage of the character arrays that are `String` data
- If Java can be sure two String variables, say s1 and s2 contains identical sequences of characters, it reuses the SAME array and therefore points to the same memory address, this is why s1 == s2 returns true, because it is the same memory address.
- The problem is Java is not always smart enough to do that, so sometimes two identical character arrays are stored in different memory locations. In this case s1 == s2 returns false.
- Therefore we cannot use == with String values

## Primitive types vs Objects

- In general we can only use == to compare primitive types
- ==Primitive types:  
    int  
    float  
    double  
    char  
    byte  
    short  
    long  
    Boolean  
    ==
- Object types (everything else) need to be compared using `equals` function.
- Object types: any values that has been constructed from a class
- When comparing object types, we need to write an equals method for the class to specify how to compare the objects for equality. The `String` class comes with an `equals` method

## Comparing arrays of `char`

- Before we look at comparing `String` values, lets look at how we might compare arrays of `char`.
- Here are two `char` arrays being compared in two different ways:

```Java
char[] a1 = {'h', 'e', 'l', 'l', 'o'};
char[] a2 = {'h', 'e', 'l', 'l', 'o'};

void setup() {
	print("a1 == a2 is ");
	println(a1 == a2);
	print("equals(a1, a2) returns");
	println(equals(a1, a2));
}
```

- This program outputs:
    
    a1 == a2 is false
    
    equals(a1, a2) returns true.
    
- What does the `equals` function do?

## An `equals` function for arrays of `char`

- To compare arrays of `char`, we must compare each character one by one:

```Java
boolean equals(char[] s1, char[] s2) {
	if (s1 == s2) {
		return true; // physically same memory location
	} else {
		int index = 0;
		// are the arrays the same length
		boolean sameSoFar = (s1.length == s2.length);
		while(index < s1.length && sameSoFar == true) {
			// compare the two charcters at the same index
			sameSoFar = (s1[index] == s2[index]);
			index += 1;
		}
		return sameSoFar;
	}
}
```

## `String` is more convenient than `char` array

- Fortunately, the String class contains a function called equals, which returns true when the characters contained within each String are identical and returns false otherwise.

```Java
String s1 = "hello";
String s2 = new String("hello");

void setup() {
	print("s1 == s2 is ");
	println(s1 == s2);
	print("s1.equals(s2) returns ");
	print(s1.equals(s2));
}
```

- This code outputs:
    
    s1 == s2 false
    
    s1.equals(s2) returns true
    

## Comparing Strings

- The rule is, when comparing String values ALWAYS use the equals function:

```Java
String s1 = ... ;
String s2 = ... ;

if (s1.equals(s2) {
	// the string values are identical
} else {
	// the string values are different
}
```

## Special character in text

- If we want to have a new line in a `String` we use the `\n` character, so `print(”first line\nsecond line”)` outputs:
    
    first line
    
    second line
    
- If we want a tab inside a String, we use the \t character, so print(”first word\tsecond word”) outputs:
    
    first word second word
    
- Other useful special character for use inside string are \” (double quote), \’ (single quote), and \\ (backwards slash)
- Using the backslash character inside a String is known as escaping characters. Java interprets the first backslash as meaning “the next character is a special character”

## Drawing text in sketches

- We have already seen that we can use the text function to draw text on the canvas
- The `textSize` function allows us to set the size of the text.
- The `textWidth` function returns the width of some text in pixels
- Chapter 17 of the “Learning Processing” books looks at drawing text.

## Reading data from a file

- A common requirement in programming is to read data from a file
- All data is read in as text and so we need text processing
- Processing has it’s own way of reading from a file but we are not using that, we will use the more general java way.
- We will use a Java class called Scanner which comes in Java’s `java.util` library

## Constructing a `Scanner`

- Java comes with library classes that you can use. All library classes come with documentation.
- In order to use a Scanner, you need to first import the class using an import statement.
- Constructing a Scanner object to read from a file requires us to handle exceptions
- Exceptions are covered in a later module. Therefore I have provided a Java class called `InputReader` for you to use to get a Scanner object to read from a file.
- To use the scanner we first need to learn about the import statement.

## An example of the scanner

- Here is a complete example that uses my class to construct a scanner and read a file line by line.

```Java
import java.until.scanner;

Scanner in; // Declare an Object called in of type Scanner.

void setup() {
	in = InputReader.getScanner("traffic.cvs");
	while (in.hasNext()) {
		String line = in.nextLine();
		println(line);
	}
	println("done");
}
```

- Lets look at the parts of this program

## Using a library class

- To use a library class, we need an import statement

```Java
import java.util.Scannner;
```

- Then we declare a variable, construct the object and use its methods just like any other class

```Java
Scanner in;
```

- The `InputReader.getScanner` function constructs the Scanner object for us and connects it to the file

```Java
in = InputReader.getScanner("traffic.cvs");
```

- Let’s look in more detail at the `hasNext` and `nextLine` functions.

## Reading line by line

- When reading from a file, we always need to check whether there is anything to read before we can safely read the data

```Java
while (in.hasNext()) {
	String line = in.nextLine();
	println(line);
}
```

- The `hasNext` function will return true when there is something to read and will return false when we get to the end of the file.
- The `nextLine` function will read the next line of input and return it as a String.
- You will get an error if you try and read past the end of the file (Exception)

## File formats

- We don’t often just read a file line by line and treat the while line as a string.
- Data files come in all kinds of formats
- The CSV format is a spreadsheet format. Each line has several data values separated by commas.
- There are many other file formats, each with predictable layout to make it easier to read the file.

## A file of data values.

- Lets assume out data file has one value per line:
- Each data item represents the count of the number of cars and taxis travelling down a road every hour, from 07.00 until 18.00
- We want to read each value as an integer and not as text
- The `Scanner` has functions to use with integers, `hasNextInt` to check if these is anything to read and `nextInt` to read the value.

## Read a file of integer values

- Here is our program modified to read a file integer values:

```Java
import java.util.Scanner;

Scanner in;

void setup() {
	in = InputReader.getScanner("carData.txt");
	while (in.hasNextInt())
		int n = in.nextInt();
		println(n);
	}
	println("done");
}
```

- This program prints each integer as it reads it.
- Normally we would do some processing of the data.

## Storing the data values

- In this example there are exactly 12 data values, one for each hour from 07.00 to 18.00.
- This means we could store the values into an array:

```Java
void setup() {
	values = new int[12]
	in = InputReader.getScanner("carData.txt");
	int i = 0;
	while (i < 12) {
		values[i] = in.nextInt();
		println(values[i]);
		i++;
	}
	println("done");
}
```

- We already know how to process values in an array to find the maximum, average, etc.

## Getting the number of values from the file

- Here is a modified data file. The first number, 12, dictates the actual number of data values to read:

```Java
12 687 858 504 432 517 572 598 593 530 844 764 611

void setup() {
	in = InputReader.getScanner("carData2.txt");
	if (in.hasNextInt()) {
		int size = in.nextInt();
		values = new int[size];
		int i = 0;
		while (i < size) {
			values[i] = in.nextInt();
			println(values[i]);
			i++;
		}
	}
	println("done");
}
```

## Another strategy

- If we didn’t want to have to count the entries, we could use a “sentinal” value.
- The sentinal value does not occur in the data. Therefore we can use it as an indicator that we have read all the data.
- In this file of traffic counts, all the data values are either 0 or positive. Therefore we can use -1 as the sentinal value.
- In this format, the first value read is the sentinal value. When we see a second occurence of the sentinal value, we know all the values have been read.

## Using a sentinal value

- If we use the file format containing a sentinal value, we cannot use arrays
- The reason is, we don’t know how many values there are in the data set.
- If we want to store an unknown number of data values, we need another data structure, like an array but one that is not limited by size.

## Using an `ArrayList`

- We could implement a variable sized container by writing a class that used an array. Every time the array gets full, we could create a bigger array, copy everything from the original array to the new one and then continue with the larger array.
- Fortunately, such a class already exists and it is called an `ArrayList`
- An `ArrayList` implements a dynamic list that will grow as large and necessary to store values
- The `ArrayList` class has a function called add which takes a new value as a parameter and adds it to the list.
- We don’t need to worry whether there is space to add more items because that is all taken care of in the implementation.

## Declaring an `ArrayList`

- The `ArrayList` class comes from the `java.util` library. This library comes free with Java.
- We need to import the ArrayList class into our program using an import statement:

```Java
import java.util.ArrayList;
```

- We then need to declare a variable of type `ArrayList`

```Java
ArrayList<Integer> values;
```

- Note 1: we need to declare the type of item that we are going to store.
- Note 2: we didn’t se the int type, an Array list only works with Object and Reference data types.

## Construction an `ArrayList`

- The declaration of the type of items to be put into the list is known as “generics”. The `ArrayList` is a generic class that can store any object, but it needs to be told the specific type of object.
- The <type> declaration is used both when we declare the variable and again when we construct the `ArrayList` object:

```Java
ArrayList<Integer> values;
...
values = new ArrayList<Integer>();
```

- Now we have an empty list ready to have integer values stored in it.

## Reading in data using a sentinal

- Here is the data file modified to use the sentinal value -1.

-1 687 858 504 432 517 572 598 530 844 764 611 -1

- We read the next data value in two places. First before we start the while statement and again at the end of the while statement.
- This plan even handles a empty data file: -1 -1
- Here is the Java code to read this file:

```Java
in = InputReader.getScanner("carData3.txt");
if (in.hasNextInt()) {
	int sentinal = in.nextInt();
	int v = in.nextInt();
	while (v != sentinal) {
		values.add(v);
		println(v);
		v = int.nextInt();
	}
}
```

## `ArrayList` functions

- The add function adds the integer value into our list

```Java
values.add(v);
```

- We can find out how many items were added to the list by using the size function:

```Java
int numValues = values.size();
println("You read " + numValues " " integers");
```

- The list uses index values (like an array) for when we want to refer to a specific item in the list. The get function is used to get a value from a specific index.
- As an example of the get function, lets look at how to sum all the integers in the list

## Summing the values in the list

- We need to use the get function to get each integer from the list:

```Java
int index = 0;
int total = 0;
while (index < values.size()) {
	total = total + values.get(index);
	index = index + 1;
}
```

We maintain in integer variable called index and then pass the index as a parameter to the get function to get each value from the list.

## Keeping other types in a list

- We are not limited to list of integers
- The generics <type> declaration allows us to specify any type as the contents of the list.
- What if we wanted to read in a list of music track titles from a text file:  
    Plenty  
    So Far to Go  
    Astronaut  
    Runnin’  
    Grown Man Sport  
    Montego Slay  
    Dang!  
    Sunshine  
    
- This requires a list of <String> values

## A list of `String` values

- Here is a program to read a list of music tracks from a file:

```Java
import java.util.Scanner;

Scanner in;
ArrayList<String> tracks;

void setup() {
	tracks = new ArrayList<String();
	in = InputReader.getScanner("TrackList.txt");
	while (in.hasNext()) {
		String title = in.nextLine();
		tracks.add(title);
		println(title);
	}
	int numTitles = tracks.size();
	println("You read " + numTitles + " track titles");
}
```

## Reading a CSV file

- Lets return to the idea of reading a file that has structured data.
- The CSV file format has data values separated by commas on each line. Lets expand the list of track titles to include the artist and the length
- We can read such as a file line by line as before, but we need to split out the three separate data values. The commas are the point at which we need to split the text.

## The `split` function

- The solution to our first problem, “How do we split the String at each comma?” is already solved .
- This a common problem and the String class already has a split function.
- The split function requires a parameter being the text to use as the point at which to split the string.
- In out case the parameter should be a String containing a comma: “,”.
- The split function returns a String[]. Each separate data value is inserted at a different index in the array.

## An example of `split`

- Here is an example of using the split function:

```Java
String csv = "Plenty, Guru's Jazzmatazz, 4:39";
String[] data = csv.split(",");
println("There are " + data.length + " values");
println("The data items are:");
for (int i = 0; i < data.length; i++) {
	println(data[i]);
}
```

- This program will output:

```Java
"""
There are 3 values
The data items are:
Plenty
Guru's Jazzmatazz
4:39
"""
```

## What to do with each string array?

- When we read this file containing lines of csv we have two options for storing each line in the list.

1. Use a list where each entry in the list is an array of String

```Java
ArrayList<String[]> tracks;
```

1. If we recognise that the three data items are related, we can use OOP to create a class called Track that represents a track. The track class would have variables for title, artist, and length. It could also have useful functions for working with music tracks. With this plan we could have a list of track items.

```Java
ArrayList<Track> tracks;
```

- The OOP solution is the best way to go.

## A Java class to represent a music track

```Java
class Track {
	private String title;
	private String artist;
	private String len;

	public Track(String t, String a, String l) {
		this.title = t;
		this.artist = a;
		this.len = l;
	}

	public String getTitle() {
		return title;
	}

	public String getArtist() {
		return artist;
	}

  public String getLength() {
		return len;
	}
```

## Reading and storing a list of `Track`

```Java
import java.util.Scanner;
import java.util.ArrayList;

Scanner in;
ArrayList<Track> tracks;

void setup() {
	tracks = new ArrayList<Track>();
	in = InputReader.getScanner("DailyMix.csv");
	String header = in.nextLine(); // ignore header
	while (in.hasNext()) {
		String csv = in.nextLine();
		String[] data = csv.split(",");
		Track track = new Track(data[0], data[1], data[2]);
		tracks.add(track);
	}
	int numTitles = tracks.size();
	println("You read " + numTitles + " Tracks:\n");
```

## Printing a list of `Track`

- It is reasonable that we would want to print a list of Track objects:

```Java
for (int i = 0; i < tracks.size(); i++) {
	println(tracks.get(i));
}
```

- If we print an object, we get a cryptic but of text made up of the object type and memory location

## A toString function

- Write a method called toString