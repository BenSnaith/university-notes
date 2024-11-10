## Choice of data structures

- A data structure does what it says in the name, it gives some structure or organisation for your data
- Many data structures maintain a collection of objects all of the same type
- The data structures that we have learned in this module are:
    - The array: a fixed size set of boxes where we can store things, We put things into specific boxes in the array and get them back by knowing their index.
    - The ArrayList: a class that gives us the concept of a list. List grow to allow us to insert as much data as we want. The ArrayList also uses the concept of an index.
    - The HashMap: associates keywords with values, The values are our data but the keys are the way we look them up. Think of a HashMap like a Dictionary

## Keeping things in an array

- First of all, arrays are a fixed size, We need the number of data items to be known in advance
- The next consideration is that each data item goes into a specific index in the array. We want an easy way to map data items onto the index
- An example of this is if we have data taken from particular hours in the day or days of the week. The mapping can than be the first hour goes to the index 0, the second hour goes to index 1, and so on
- If you don’t have a mapping, then when you want to get something back from your array, you will have the search for it.

## Keeping things in a list

- When we don’t know how much data we have, we cannot use an array.
- A list is a data structure that we can keep adding data to and it will expand to hold everything
- The ArrayList also uses the concept of an index, so we can get data back from it using the index
- The difference is that because the data size is unknown. there probably isn’t a mapping from the data to the index.
- When we want to get a specific data item back, we almost always have to search for it.

## Searching a list of items

- We have seen the code for searching
- For arrays, the number of indices we need to search is in the `length` property. This is the size the array

```Java
int theSize = myArray.length;
```

- If we need to know how many data items we have inserted into the array, we need to keep that count ourselves
- For `ArrayList` the number of indices we need to search is given by its size method. The value we get from size is the number of data items in the list

```Java
int theSize = myArrayList.size();
```

- Once we have the size of the collection we are searching. We can use a while or a for statement.

```Java
for (int i = 0; i < theSize; i++) {
	// get item at current index and process it
}
```

## Keys and Values in the `HashMap`

- The `HashMap` is designed to work with keys and values
- The `put` method associates the key with the value
- The `get` method takes a key and returns the associated value to us.
- If you choose an appropriate key, you can take advantage of the quick look-up of values. There is no searching, the key is a direct link to the value
- If you often want to search the values without using a key, then you are probably using the wrong data structure

## Thinking about searching

- We often have millions of data items (not uncommon)
- For this example, lets say 2 million data item.
- Searching takes time.
- If we don’t find what we are looking for, we look at all 2 million items
- If we find what we are looking for, the number of items we have to look at before we find it is indetermined. Worst case is we find it as the last item and we looked at all 2 million.

## Sorting

- The first thing to do if you are trying to improve the time taken to search and find an item is to sort the collection.
- The first benefit is that we can stop searching earlier if we don’t find what we are looking for. For example, if the data is in alphabetical order, and what we are looking for starts with a ‘C’, we can stop when we get to ‘D’
- Another benefit is we can use more advanced searching algorithms. For example, binary search starts searching in the middle. If the data is sorted we know in which half of the data we need to look for.

## Binary Search

- Binary search does not start at the beginning and search
- It repeatedly starts in the middle and divides the sorted data into half until the item is found.
- Here is a diagram. 75 is found in 3 steps.

![[Untitled 50.png|Untitled 50.png]]

## How do we sort our data?

- There are lots of sorting algorithms. Choose a sorting algorithm and how efficient that algorithm is (how long it takes to sort out 2 million items) is outside the scope of this module
- Other people have implemented sorting algorithms for us.
- For arrays, there is a utility class called `java.util.Arrays`. This class has a `sort` method, we can give it the array and it sorts it for us.

## How are arrays sorted?

- Lets look at arrays first, If the contents of the array are integers or floats or anything “that can be compared”, we can just call the `Arrays.sort` method:

```Java
import java.util.Arrays;

String[] names = {"John", "Mary", "Sarah", "Jack", "Arthur"};
println("Before sort: " + Arrays.toString(names));
Arrays.sort(names);
println("After sort: " + Arrays.toString(names));
```

- The above code outputs the following, the second line of output is after the array has been sorted

Before sort: [John, Mary, Sarah, Jack, Arthur]

After sort: [Arthur, Jack, John, Mary, Sarah]

## How are `ArrayList`s Sorted?

- This are very similar when it comes to sorting a `ArrayList`.
- The only difference is we are using `Collections.sort` to do the sorting.

```Java
import java.util.Arrays;
import java.util.Collections;

String names[] = {"John", "Mary", "Sarah", "Jack", "Arthur"};
// convert the array into an ArrayList
ArrayList<String> namesList = new ArrayList<String>(Arrays.asList(names));
println(namesList.toString());
Collections.sort(namesList);
println(namesList.toString());
```

Before sort: [John, Mary, Sarah, Jack, Arthur]

After sort: [Arthur, Jack, John, Mary, Sarah]

## How do we sort objects?

- In an earlier slide I said we can sort anything “that can be compared”. What does this mean?
- Classes can implement a `compateTo` method which returns an integer under the following rules:
    - A negative integer, this object is less than the other
    - Zero, this object is equal to the other
    - A positive integer, this object is greater than the other
- When we implement `compareTo` we need to declare that out class implements that method.

## A `Person` class

Here is a simple class representing a Person

```Java
class Person {
	private String name;
	private int age;

	public Person(String n, int a) {
		this.name = n;
		this.age = a;
	}

	public String getName() {
		return name;
	}

	public int getAge() {
		return age;
	}

	public String toString() {
		return name + " is " + age;
	}
}
```

## Trying to sort an array of `Person`

- If we try to sort an array of `Person[]` using `Arrays.sort` we get an error
- If we try to sort an `ArrayList<Person>` using `Collections.sort` we get an error
- These two errors are essentially Java telling us “I don’t know how to sort `Person` objects”
- However, we can fix that by following a simple standard:
    - Declare the class to be `Comparable`
    - Implement a `compareTo` method

## Making `Person` comparable by `age`

```Java
class Person implements Comparable<Person> {
	private String name;
	private int age;

	public Person(String n, int a) {
		this.name = n;
		this.age = a;
	}

	// other methods omitted -- same as before

	public int compareTo(Person other) {
		return age - other.getAge(); // compare by age
	}
}
```

- Class declaration `implements Comparable<Person>`
- The `compareTo(Person other)` method return an int value according to the rule.

## Comparing lists of `Person` by age

```Java
import java.util.Collections;
// some data
String[] names = {"John", "Mary", "Sarah", "Jack", "Arthur"};
int[] ages = {29, 32, 24, 65, 42};
// create some person objects from the data
ArrayList<Person> people = new ArrayList<Person>();
for (int i = 0; i < names.length; i++) {
	Person p = new Person(names[i], ages[i]);
	people.add(p);
}
// print then sort then print
println("Before sort: " + people.toString());
Collections.sort(people);
println("After sort: " + people.toString());
```

Before Sort: [John is 29, Mary is 32, Sarah is 24, Jack is 65, Arthur is 42]

After Sort: [Sarah is 24, John is 29, Mary is 32, Arthur is 42, Jack is 65]

## Sorting Person objects by name

- If we wanted to sort the Person objects by name in alphabetical order we can exploit the fact that the String type is already comparable
- Here is a `compareTo` which compares Person by name:

```Java
public int compareTo(Person other) {
	// use String.compareTo
	return name.compareTo(other.getName());
}
```

- The String type is comparable so we don’t need to reimplement putting strings into alphabetical order. We just call its `compareTo` and return whatever it gives us.
- Now the output of the program on the previous slide is:

After sort: [Arthur is 42, Jack is 65, John is 29, Mary is 32, Sarah is 24]

## Iterators and the enhanced `for` statement

- Java has an enhanced for statement to simply a for loop when iterating through items,.
- Here is the code from last week, rewritten to use the enhanced `for` loop.

```Java
import java.util.Iterator;

HashMap<String, Contact> contacts;
contacts = ...; // construcut and insert data

public void printAllContacts() {
	for (String email : contacts.KeySet()) {
		Contact c = contacts.get(email);
		System.out.println(c);
	}
}
```

## A template for this for statement

- This is the format to follow

```Java
for (T item : collection<T>) {
	// process the item
}
```

- On the right side of the : is a collection of objects of type T. The collection could be an array or an `ArrayList` or a `KeySet`.
- On the left of the : is a local variable of type `T`
- Each iteration, the local variable us assigned a value being the next value from the collection.
- Behind the scenes, Java rewrites this code into something like the version with the `Iterator` and the `while` statement. If you were to debug the loop you would see the `Iterator`.

## Using the enhanced for statement

- The enhanced for statement works with any collection of type, T.
- That collection could be the `KeySet()` from a `HashMap` as an earlier slide
- The collection could be an array of T. Here is an example

```Java
Person[] personArray = new Person[10];
// ... code to fill the array ommited
for (Person p : personArray) {
	// process item p
}
```

- The collection could be an `ArrayList<T>`

```Java
ArrayList<Person> personList = new ArrayList<Person>();
// ... code to fill the list not shown
for (Person p : personList) {
	// process item p
}
```

## Considering the parameter names

- Consider this code from an earlier slide:

```Java
class Person {
	private String name;
	private int age;

	public Person(String n, int a) {
		this.name = n;
		this.age = a;
	}
}
```

- We have name the parameters n and a, These are not good names, we would prefer to call them name and age but that introduces confusion

## The confusion

- When we use the names name and age for the parameters we have this confusion

```Java
class Person {
	private String name;
	private int age;

	public Person(String name, int age) {
		name = name // !!
		age = age // !!
	}
}
```

- If we try to read this we get confused. It is meaningless to assign `name = name` and `age = age`.
- If we run this code. it actually does nothing. The variables in the class do not get assigned a value

## The keyword `this`.

- We can remove this confusion by adding the keyword `this`.

```Java
class Person {
	private String name;
	private int age;

	public Person(String name, int age) {
		this.name = name // !!
		this.age = age // !!
	}
}
```

- The keyword this means “this object” and so this.age refers to the age variable defined at the top of the class.
- Without this, the variable used will be the one defined in the nearest block of code (i.e. as a local variable or a parameter)

## We can use `this` in Java classes

- Whenever we are referring to the variable defined at the top of the class, we can use the keyword `this`:

```Java
class Person {
	private String name;
	private int age;

	public Person(String name, int age) {
		this.name = name // !!
		this.age = age // !!
	}

	public String getName() {
		return this.name;
	}

	public String getAge() {
		return this.age;
	}

	public boolean isOlderThan(Person p) {
		int age = p.getAge();
		return this.age > age;
}
```

## Public vs Private

- Anything labelled `public` (instance variables, constructors, methods) are accessible to other classes.
- Anything labelled `private` is accessible only within the same class.
- Only methods that are intended for other classes should be `public`.
- Instance variables should not be `public`.
- We will see why in the following case study…

## Public instance variables: what could possibly go wrong?

- User story: As an application programmer I want to maintain a list of students taking a module. I want to be able to add a student to the module and find a student given their SUN number
- Library Programmer thinks: “I could create a class called `StudentList` and implement the list using an `ArrayList`. I’ll make is available as a library class”

## A `StudentList` class

- The class and its instance variable:

```Java
public class StudentList {
	public ArrayList<Student> students;
}
```

- These methods will ne the public interface; Method Summary

|   |   |
|---|---|
|void|addStudent(Student s)|
|Student|findStudent(String SUN)|

## If it’s public, I can use it!

- Application programmer thinks: “I will use the StudentList class in my application. Oh look she has used an ArrayList to store the list of students. The instance variable is public so I will use it”
- The programmer writes this client code to create a Student object and add it to a StudentList

```Java
void setup() {
	StudentList cs1310 = new StudentList();
	Student s1 = new Student("1234", "John Smith");
	cs1310.students.add(s1);
}
```

## `StudentList` Update design

- Library Programmer: “I could simplify my findStudent method if i use a HashMap to store the students and not an ArrayList.
- Action: Change type of the instance variable and modify the implementation of the methods that use that variable
- Improved code: Using a HashMap with the student’s ID as the key, there is no searching in findStudent. Just use the ID as the key to get the Student object.
- Action: Release the new version.

## `StudentList` v2.0

The new implementation

```Java
public class StudentList {
	public HashMap<String, String> students;
}
```

## Public instance variables: my code is broken

Application Programmer: “I got this new version of the `StudentList` but when i try and use it with my code, it won’t run, I called the woman who wrote it and she said she hasn’t changed the public interface

What’s Wrong?

## Why is the application broken

- The application programmer was using the add method of the ArrayList to add students to the list
- The new version of StudentList still has the students variable in the improved implementation but it’s type has changed to HashMap
- The HashMap does not have an add method!
- The public methods called addStudent and findStudent would work in both version because they have been written to work with the implementation

## Who is to blame? What should we do?

- In a way, both are to blame
    - The library class programmer used a public instance variables
    - The application programmer ignored the public methods and directly accessed the instanced variable
- Important: The public interface is essentially our implementation of the user story, It is fixed because that is what the user has asked for, The rest of our implementation may change whenever we find a better way to write it, so keep the rest of the implementation private
- Instance variables are not part of the public interface. We are using them internally for our own purposes
- Rule: Force everyone to use the public interface. keep instance variables private

## Private variables are not accessible

- In a Java tab, private variables are not accessible
- The situation is different for processing tabs for reasons we will not go into here
- If the students variable has been private from the start, it would not be accessible

## The correct way to use StudentList

- The StudentList developer should keep instance variables private.

```Java
private ArrayList<Student> students;
```

or;

```Java
private HashMap<String, String> students;
```

- The application programmer should use the public methods

```Java
StudentList cs1310 = new StudentList();
Student s1 = new Student("1234", "John Smith");
cs1310.addStudent(s1);
```

## Use of private for information hiding

- Data belonging to one object is hidden from other objects
- Know what an object can do, not how it does it
- Information hiding increases the level of independence
- Independence of modules is important for large systems and maintenance
- Information hiding is sometimes called encapsulation.