## Unit Objectives

- Learn what is meant by an Abstract Data Type (ADT)
- Learn about some common examples of collection ADTs

## Abstract Data Types (ADTs)

- An ADT is a mathematical specification of:
    - A set of data, and…
    - The set of operations that can be performed on that data.
- Such a data type is abstract as the focus on defining the properties of the set of data and the behaviour of the operations that act on it.
    - The same ADT can be implemented in various ways.
    - Users/Clients are not informed about how the data type is actually implemented
- Typical examples of ADTs are fraction, string, list, stack, queue, map, etc.
- For each ADT, we specify two pieces of information:
    - The abstract structure of the data, and…
    - The typical operations that can be performed on the data.
- Example: ADT Fraction

|   |   |
|---|---|
|Abstract Structure|Typical Operation(s)|
|Numerator / Denominator|add, subtract, multiply, divide, etc.|

- Another Example: ADT String

|   |   |
|---|---|
|Abstract Structure|Typical Operation(s)|
|A sequence of characters|concatenate, contain, equals, length, substring, etc.|

## Collections

- A collection is an object that represents a group of objects of some fixed type, e.g.
    - A collection of books, cars, tickets, films, treasure, employees, etc.
    - Each object within a collection is known as an element of the collection.
- Many types of fundamental collections have been defined, e.g. stack, queue, list, tree, graph, set.
- e.g. In Java.

```Java
ArrayList<Book> bookShelf = new ArrayList<>();

HashSet<Treasure> myTreasure = new HashSet<>();

HashMap<String, ID> phoneBook = new HashMap<>();
```

Collections can be broadly categorised as:

- Unordered
- Linear
- Non-linear

The elements within a collection are usually organised based on:

- The order in which they were added to a collection, or
- Some inherent relationship among the elements themselves, e.g.
    - Numeric Order: {12, 25, 33, 42, 49, 57, 73, 81}
    - Alphabetical Order: {”Amy”, “Ben”, “Cat”, “Dan”, “Phe”, “Seb”}
    - Chronological Order: {1878, 1912, 1914, 1939, 1945}
- Example of collection types: stack, queue, set, map, list, tree

## Bounded and Unbounded Collections

Collections can also be categorised as:

- Bounded - the collection had a maximum size or capacity.
- Unbounded - there is no limit on the size of the collection.
- Array is an example of a bounded concrete data structure in Java

## Exception

- Exception in Java is a means to handle the situation when a problem arises during a Java program’s execution.
- e.g. Consider attempting to remove something from an empty `Box` . What should an empty `Box` return.
    - Null
    - Return Nothing and terminate program
    - ???

## Using Exception

- To avoid returning null, the program can throw an exception:

```Java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.Random;

public class Box<T> implements Iterable<T> {
	private ArrayList<T> contents;
	
	public T draw() {
		if(contents.isEmpty()) {
			throw new IllegalStateException("Empty Box, Raffle Over!");
		}
		
		Random rand = new Random();
		int which = rand.netInt(contents.size());
		return contents.remove(which);
	}
}
```

## Working with Exception

- When receiving an exception, the caller program can:
    - Handle the exception, or…
    - Not handle the exception, simple propagate it to the program’s caller.
        
        i.e. “pass the responsibility”
        
- Question: How can the caller program find out if it has been given an exception?

## Handle Exception

`try` to execute some Java code, but bear in mind that there may be the need to `catch` an exception and deal with it:

```Java
public Map<Prize, Ticket> luckyDraw() {
	Map<Prize, Ticket> winners = new HashMap<>();
	
	try {
		for(Prize p : prizes) {
			winners.put(prize, tickets.draw());
		}
	}
	catch(IllegalStateException e) {
		return winners;
	}
	
	return winners;
}
```

## The Interface `Bounded`

```Java
public interface Bounded<T> implements Iterable {
	public int capacity;
	public T[] arr;
	public int length;
	
	// Other details omitted.
}
```

## Collections and Abstraction

- An abstraction hides certain details at certain times.
- A collection is an abstraction.
    - Why?
    - In what way?
- We want to separate the interface of the collection from the underlying details of how we choose to implement it.

## Hiding implementation details using an interface

A well-defined interface masks the implementation of the collection.

![[image 18.png|image 18.png]]

![[image 1 7.png|image 1 7.png]]

## Java Interfaces and Abstract Data Types

- A Java interface typically defines a set of abstract methods, e.g. `public abstract int size();`
- Java interfaces do not contain any data members (i.e. fields)
- Classes and Interfaces modelling collection data structures should be generic
    
    **Why?**
    

## Linear Collections

- Stack
- Queue
- List

## Stacks

- A stack is a linear collection whose elements are added and removed from one end.
- A stack is LIFO: Last in, First out.
- The last element put on the stack is the first element to be removed
- A stack is usually depicted vertically, with additions and deletions occurring at the top of the stack.

## Stack Operations

- Any collection ADT should provide the operations `isEmpty` and `size` .
- A stack ADT has three operations traditionally known as:
    - `push` - add an element to the top of the stack
    - `pop` - remove the element at the top of the stack and return it
    - `peek` - return the element at the top of the stack without removal

## StackADT.java

```Java
public interface StackADT<T> {
	public void push(T item);
	
	public T pop();
	
	public T peek();
	
	public boolean isEmpty();
	
	public int size();
}
```

By default, StackADT is unbounded, no provision for iterating over it’s elements.

## Bounded Stack

- For a BoundedStackADT, we need to extend the interface to include the two extra operations `isFull` and `capacity`:

```Java
public interface BoundedStackADT<T> extends StackADT<T> {
	public boolean isFull();
	
	public int capacity();
}
```

- An alternative is to let a class implementing a bounded stack implement both of the interfaces StackADT and Bounded

```Java
public class BoundedArrayStack<T> implements StackADT<T>, Bounded {
	// Implementation details omitted.
}
```

## Queues

- A queue is a linear collection that has opening at both ends
- A queue is processed in a FIFO fashion: First in, First out.
- Elements are removed in the some order that they are inserted.
- Any waiting line is a Queue:
    - The Queue at a supermarket
    - Cars at a traffic light
    - Operations on a printer
- Queue operations occur at both ends (front and rear)
- A queue is usually depicted horizontally
- Elements are added at the rear (or the tail) of the queue.
- Elements are removed from the front (or the head) of the queue.

## Queue Operations

- enqueue adds an element to the end of the queue.
- dequeue removes an element from the head of the queue.
- A pure queue does not allow access to the elements in the middle.

|   |   |
|---|---|
|Operation|Purpose|
|enqueue|Adds an element at the back (i.e. the rear) of the queue.|
|dequeue|Removes an element from the front of the queue|
|first|Returns the element at the front of the queue.|
|isEmpty|Checks whether the queue is empty (i.e. without any elements)|
|size|Returns the number of elements in the queue|

## QueueADT.java

```Java
public interface QueueADT<T> {
	public void enqueue(T element);
	
	public T dequeue();
	
	public T first();
	
	public boolean isEmpty();
	
	public int size();
}
```

Any class implementing an unbounded queue data structure would implement this interface.

For a bounded queue, the class would also implement interface `Bounded`

## Lists

- Also known as sequences
- List is a linear collection:
    - Lists are more flexible than stacks or queues
- Elements can be added or removed anywhere within a list.
- A list may contain duplicate values
- There are different kinds of list, each with their own specific operations

## List Operations

|Operation|Purpose|
|---|---|
|removeFirst|Removes the first element from the list.|
|removeLast|Removes the last element from the list.|
|remove|Removes a specified element from the list.|
|first|Returns the first element of the list.|
|last|Returns the last element of the list.|
|contains|Checks whether a specified element is on the list.|
|isEmpty|Checks whether the list is empty (i.e. without any element)|
|size|Returns the number of elements on the list|

## The ListADT Interface

```Java
import java.util.Iterator;

public interface ListADT<T> {
	T removeFirst();
	T removeLast();
	T first();
	T last();
	boolean isEmpty();
	int size();
	
	boolean remove(T element);
	
	boolean contains(T target);
}
```

Should a for-each statement be used on a list?

## ListADT Interface: an improved version

```Java
import java.util.Iterator;

public interface ListADT<T> extends Iterable<T> {
	T removeFirst();
	T removeLast();
	T first();
	T last();
	boolean isEmpty();
	int size();
	
	boolean remove(T element);
	
	boolean contains(T target);
}
```

Do we need to add an `iterator()` method to `ListADT`

## Non-Linear Collections

- Map
- Set
- Multiset

## Maps

- Also known as a dictionary (Python), associative array (PHP) and lookup table
- Map is an ADT that maps keys to values
- Typically, each key in a map is unique.
    
    … but different keys may be mapped to the same value.
    

## Maps: Operations

- Typical operations include:
    - Add - Add a new key-value mapping to the map.
    - Reassign - Associate an existing key in the map with a new value
    - Remove - Remove a key with its associated value from the key set in the map
    - Lookup - Find the value (if any) that is associated with a key.

## MapADT.java

```Java
public interface MapADT<T, U> {
	public void add(T key, U element);
	
	public void reassign(T key, U element);
	
	public void remove(T key);
	
	public void lookup(T key);
	
	public boolean isEmpty();
	
	public int size();
}
```

## What is a Set?

- A set is a collection of distinct elements of a particular type
- Elements in a set are unordered
- We can delimit the elements in a set by curly braces, e.g. the set of vowels
    
    Vowels = {’a’, ‘e’, ‘i’, ‘o’, ‘u’}
    
- As the order in which the elements of a set are listed is irrelevant this logically:
    
    Vowels = {’a’, ‘e’, ‘i’, ‘o’, ‘u’} = {’e’, ‘a’, ‘i’, ‘u’, ‘o’} = {’o’, ‘u’, ‘i’, ‘e’, ‘a’} = {’o’, ‘u’, ‘a’, ‘e’, ‘i’}
    

## Set Collection

- Although a set is logically an unordered collection, internally its elements may be ordered for efficiency reasons.
- An element can appear at most once in a set
- If we add an element `a` to a set that already contains `a` the set will be unchanged

## Sets: Operations

- Like most collections, the SetADT includes ways for the user to:
    - `isEmpty` - determine if the set is empty
    - `size` - determine the number of elements in the set
    - `add` - add a specified element to the set
    - `remove` - remove a specified element from the set
    - `removeAll` - remove every element except a set of specified elements
    - `contains` - determine if a element is a member of the set
    - `equals` - determine if two sets have the same members
    - `isSubset` - determine if one set if a subset of another
- There will also be some ‘classic’ set operations
    - union: u
    - intersection: n
    - difference: \

## SetADT.java

```Java
public interface SetADT<T> {
	public boolean add(T element);
	
	public boolean addAll(SetADT<T> A);
	
	public boolean remove(T element);
	
	public boolean removeAll(SetADT<T> A);
	
	public boolean retainAll(SetADT<T> A);
	
	public SetADT<T> union(SetADT<T> A);
	
	public SetADT<T> intersection(SetADT<T> A);
	
	public SetADT<T> difference(SetADT<T> A);
	
	public boolean isSubset(SetADT<T> A);
	
	public boolean contains(T element);
	
	public boolean equals(SetADT<T> A);
	
	public boolean isEmpty();
	
	public int size();
}
```

## Multi-Set Collections

- A multi-set is a generalisation of a set concept which the same element can appear more than once
- As with sets, the order in which the elements of a multi-set are listed is irrelevant

## Multi-Set Operations

- Most of the operations of a multi-set are quite similar to those of an ordinary set, differing only in that they take proper account of duplicate elements.
- For example, suppose an element x occurs n times in a multi-set A and multi-set B contains it m times. Then after the method call A.addAll(B), x will appear in A for (n + m) times.
- Similarly, after the method call A.removeAll(B), the multi-set A would contain x(n - m) times (or 0 times if m ≥ n).
- Two multi-sets (bags) are equal only if they contains exactly the same elements with duplicate elements appearing the same number of times in each.
- A.isSubbag(B) is true if every element of A occurs at least as many times in B as it does in A

The set methods union, intersection and difference in multi-sets:

- If an element occurs n times in multi-set A and m times in multi-set B, then:
    - union - it occurs max(n, m) times in A u B
    - intersection - it occurs min(n, m) times in A n B
    - difference - it occurs max(O, (n - m)) times in A \ B
- Two additional methods are useful:
    - count - returns the number of occurrences of a specified element in the multi-set

```Java
public int count(T element);
```

- sum - if an element occurs n times in multi-set A and m times in multi-set B then it occurs (n + m) times in A + B

```Java
public MultisetADT<T> sum(MultisetADT<T> A);
```