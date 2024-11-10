## Unit Objectives

- Revise basic array concepts.
- Look at how bounded collections ADTs can be implemented with arrays.
- Learn how abstract classes can simplify the implementation of ADTs.
- Learn how unbounded ADTs can be implemented with ‘growable’ arrays.
- Describe the time implications of the above using Big-O notation.

## Overview

- Using abstract class to simplify implementation and foster reuse.
- Working with one-dimensional (1D) arrays.
- Implementing some bounded collections: set, stack, queue.
- Implementing an Iterator for 1D arrays.
- Implementing an unbounded collection using static arrays.

## Using An Abstract Class

- Achieve improved modularisation.
- Foster reuse.

![[image 19.png|image 19.png]]

## Possible implementations of the ADT Set

![[image 1 8.png|image 1 8.png]]

## Implementing the ADT Set

![[image 2 7.png|image 2 7.png]]

## An Abstract Set Class

- Not all of the operations of `SetADT` require the knowledge of how the set is modelled, e.g. `addAll` and `isSubset`

```Java
public boolean addAdd(SetADT<T> A) {
	boolean hasBeenModified = false;
	
	for(T element : A) {
		if(this.add(element)) {
			hasBeenModified = true;
		}
	}
	
	return hasBeenModified;
}
```

## AbstractSet in JCF

The Java Collections Framework (JCF) often uses an abstract class to simplify the implementation of a collection ADT, e.g.:

![[image 3 7.png|image 3 7.png]]

## AbstractSet.java

```Java
import java.util.Iterator;

public abstract class AbstractSet<T> implements Set<T> {
	public boolean addAll(SetADT<T> A);
	
	public boolean removeAll(SetADT<T> A);
	
	public boolean retainAll(SetADT<T> A);
	
	public boolean isSubset(SetADT<T> A);
	
	public boolean equals(SetADT<T> A);
}
```

## addAll

To add _all_ elements to a given set (i.e. A) into `this` set object…

```Java
public boolean addAll(SetADT<T> A) {
	boolean hasBeenModified = false;
	for(T element : A) {
		if(this.add(element)) {
			hadBeenModified = true;
		}
	} 
	return hasBeenModified;
}
```

- We iterate through the elements of set A adding its elements one by one to the current set.
- If at least one element of A is added to the set (i.e. if not all elements of A are already present), we update the value of `hasBeenModified` to `true`

## removeAll

To remove all elements in the given set (i.e. A) from this set object…

```Java
public boolean removeAll(SetADT<T> A) {
	boolean modified = false;
	Iterator<T> iter = A.iterator();
	while(iter.hasNext()) {
		if(this.remove(iter.next()) {
			modified = true;
		}
	}
	return modified;
}
```

- We iterate though the elements of set A and attempt to remove them from the current set one by one using remove.

## retainAll

To remove all elements, except the ones in the given set (i.e. A), from this set object.

```Java
public boolean retainAll(SetADT<T> A) {
	boolean modified = false;
	for(T element : this) {
		if(A.contains(element) continue;
		if(this.remove(element) {
			modified = true;
		}
	}
	return modified;
}
```

## isSubset

```Java
public boolean isSubset(SetADT<T> A) {
	if(this.size() > A.size()) return false;
	for(T element : this) {
		if(!A.contains(element) return false;
	}
	return true;
}
```

## equals

To check whether the given set (i.e. A) contains exactly the same elements as this set object.

```Java
public boolean equals(SetADT<T> A) {
	if(this.size() != A.size()) return false;
	return isSubset(A) && A.isSubset(this);
}
```

- As a simple optimisation in equals, we first check whether the sizes of the two sets are equal.
- We know if they are the same size and they are a subset of each other (all sets are subsets of themselves) then the are equal.

## Working with arrays

Basic Java Syntax for working with static arrays:

- How to define an array?
- How to initialise and array with data?
- How to process element(s) in an array?
- Time efficiency of various array operations?

## Declaring Arrays

- Once storage for an array has been allocated, the array has a fixed capacity throughout its while lifetime.
- Array elements can be of any Java type — either primitive or a class.

```Java
int[] a;
a = new int[10];

double[] b = new double[20];

boolean[] attendance = new boolean[5];

String[] text = new String[200];

Object[] text = new Object[5];

java.util.Date[] holiday = new java.util.Date[8];
```

- Storage of an array object can be allocated and initialised using an array aggregate, e.g.

```Java
int[] c = {5, 2, 1, 4}; // array aggregate
```

- Array aggregates can only be used when an array variable is declared, they cannot be used to (re-)initialise arrays.
    
    Thus, the following will not compile
    

```Java
double d = new double[4] = {1.0, 2.0, 3.0, 4.0} // !
```

- Elements are indexed from 0 to length - 1.
    - The first index of an array is always 0.
    - The last index of an array is length-1.
- Default initialised values for different types of array:
    - `int[] : 0`
    - `boolean[] : false`
    - `java.util.Object[] : null`

## Array Processing

The number of elements in an array can be accessed using the final field length of the array, e.g.

```Java
int a[] = {1, 3, 5, 7, 9};

// add 2 to each element of array a
for(int i = 0; i < a.length; i++) {
	a[i] += 2;
}
```

However, it is often more convenient to use an enhanced for loop:

```Java
double b[] = {2.99, 11.9, 3.1415, -37.5};

double sum;
for(double elem : b) {
	sum += elem;
}
```

## Time Efficiency of Array Operations

- Access to array elements when we know the index of the element that we want is constant O(1)
- Processing a whole 1D array of size n involves a loop being executed n times.
    
    Assuming the time complexity of processing one element is O(1), the time complexity of the whole process is O(n).
    

```Java
for(int i = 0; i < salaries.length; i++) 
{
	salaries[i] += salaries[i] * 0.01;
}
```

## Implementing Various ADTs using Arrays

### Sets, Stacks and Queues

![[image 4 7.png|image 4 7.png]]

## A Bounded Set Implementation: ArraySet

![[image 5 6.png|image 5 6.png]]

## ArraySet.java

```Java
import java.util.Iterator;
public class ArraySet<T> extends AbstractSet<T> implements Bounded {
		private static final int DEFAULT_CAPACITY = 100;
		
		private T[] contents;
		private final int maxSize;
		private int currentSize;
		
		// Other implemetation details omitted.
		
		@SuppressWarnings("unchecked")
		public ArraySet (int maxSize) {
			contents = (T[])(new Object[maxSize]);
			currentSize = 0;
			this.maxSize = maxSize;
		}
		
		public ArraySet() {
			this(DEFAULT_CAPACITY);
		}
		
		public int size() { return currentSize; }
		public boolean isEmpty() { return currentSize == 0; }
		public int capacity() { return maxSize; }
		
		public boolean isFull() {
			return (currentSize == maxSize);
		}
		
		public boolean contains(T element) { // O(n)
			for(T elem : this.contents) {
				if(element.equals(elem)
					return true;
			}
			return false;
		}
		
		public boolean add(T element) { // O(1)
			if(!contains(element) {
				if(!isFull()) {
					contents[currentSize] = element;
					currentSize++;
					return true;
				}
				else {
					throw new IllegalStateException("Set is full in add()");
				}
			}
			else {
				return false;
			}
		}
		
		public boolean remove(T element) { // O(n)
			for(int i = 0; i < currentSize; i++) {
				if(element.equals(contents[i]) {
					currentSize--;
					contents[i] = contents[currentSize];
					return true;
				}
			}
			return false;
		}
		
		public SetADT<T> intersection(SetADT<T> A) { // O(n)
			ArraySet<T> res = new ArraySet<T>(maxSize);
			
			for(int i = 0; i < currentSize; i++) {
				if(A.contains(contents[i])) {
					result.add(contents[i]);
				}
			}
			return result;
		}
}
```

## Iterators

- To complete the implementation of ArraySet, we need an Iterator as the class implements the java.lang.Iterable interface.
- An iterator is an object that allows the user to acquire and use each element of a collection in turn
- Method iterator returns a `java.util.Iterator` object.
- An Iterator object has the following methods:
    - `hasNext`: return true is there are more elements in the iteration
    - `next`: returns the next element in the iteration
    - `default remove`: removes the current element of the collection.
    - `default forEachRemaining`

## API Specification: `java.util.Iterator`

![[image 6 4.png|image 6 4.png]]

## The `default remove()` in `java.util.Iterator`

![[image 7 4.png|image 7 4.png]]

NOTE: IF THE DEFAULT IMPLEMENTATION IF APPROPRIATE FOR YOU THERE IS NO NEED TO REWRITE THIS IMPLEMENTATION IN THE CONCRETE CLASSES.

## How to implement method `Iterator()`

In Unit 1, we simply invoke the method `iterator()` of an ArrayList object…

```Java
import java.util.Iterator;

public class Box<E> implements Iterable<E> {
	private ArrayList<E> contents;
	
	public Iterator<E> iterator() {
		return contents.interator();
	}
}
```

HOWEVER: Our `ArraySet` uses an array and there is not an implementation for `interator()` on array.

## ArrayIterator.java

We define a new class `ArrayIterator` and use it whenever we need it to iterator over any array-based collection

```Java
import java.util.Iterator;
public class ArrayIterator<T> implements Iterator<T> {
	private T[] contents;
	
	private int cursor;
	
	private int limit;
	
	public ArrayIterator(T[] array, int size) {
		contents = array;
		limit = size;
		cursor = 0;
	}
	
	public boolean hasNext() {
		return cursor < limit;
	}
	
	public T next() {
		if(!hasNext()) {
			throw new IllegalStateException("ArrayIterator: No next element");
		}
		return contents[cursor++]; // increment is done afterwards
	}
	
	public void remove() {
		throw new UnsuppoertedOperationException("ArrayIterator: No remove method");
	}
}
```

## `iterator()` in class `ArraySet`

```Java
public class ArraySet<T> extends AbstractSet<T> {
	
	// Previously defined field and methods are omitted
	
	public Iterator<T> iterator() {
		return new ArrayIterator<T>(this.contents, currentSize);
	}
}
```

## Implementing an Unbounded Collection using Array

- When the array reaches its capacity, we can expand it by creating a new, larger, array and copy all of the current elements from the original array and then reassign the original array to this larger array.

```Java
private T[] contents;

@SupressWarnings("unchecked")
private void expandCapacity() {
	// Create a new larger array
	T[] larger = (T[])(new Object[contents.length * 2]);
	for(int i = 0; i < contents.length; i++) {
		larger[index] = contents[index];
	}
	contents = larger;
}
```

## Implementing an Unbounded Set using Array

- When adding an element to an unbounded set, we may need to expand the capacity of the contents:

```Java
public boolean add(T elements) {
	boolean added = false;
	if(!contains(element)) {
		if(size() == contents.length {
			resize();
		}
	}
	return added;
}
```

There is now no need to throw an `IllegalStateException`.

## A Bounded Stack Implementation

- An array-based implementation leads to a bounded collection as the collection will have a maximum size.
- The stack grows upwards from the start of the array as items are pushed onto it.

## ArrayStack.java

```Java
public class ArrayStack<T> implements BoundedStackADT<T> {
	private static final int DEFAULT_CAPACITY = 100;
	
	private T[] contents;
	
	private final int maxSize;
	private int top; // currentSize
	
	public ArrayStack(int maxSize) {
		contents = (T[])(new Object[maxSize]);
		top = 0;
		this.maxSize = maxSize;
	}
	
	// Getter methods omitted (similar to ArraySet)
	
	public void push(T element) {
		if(top == maxSize) {
			throw new IllegalStateException("Stack full");
		}
		contents[top] = element;
		top++;
	}
	
	public T pop() {
		if(top == 0) {
			throw new IllegalStateException("Stack Empty");
		}
		top--;
		return contents[top];
	}
	
	public T peek() {
		if(top == 0) {
			throw new IllegalStateException("Stack Empty");
		}
		return contents[top - 1];
	}
	
	public void clear() {
		top = 0; // everything will just be overwritten
	}
}
```

- All of the methods in our array stack are constant.

## Implementing an Unbounded Stack using Array

- The only difference between an array implementation of a bounded and an unbounded stack is the push operation.

```Java
public void push(T element) { // O(n)
	if(size() == contents.length) {
		resize();
	}
	contents[top] = element;
	top++;
}
```

There is no need to throw an `IllegalStateException`

## ArrayQueue.java

We can define an `int` variable `rear` to keep an integer value that represents:

- The next available slot in the array (i.e. the cell that is not currently used for keeping an object reference)
- The number of elements currently in the queue.

```Java
public class ArrayQueue<T> implements QueueADT<T> {
	private static final int DEFAULT_CAPACITY = 100;
	private int rear;
	private T[] queue;
}
```

## Constructor

An empty queue means that no element is in the array, i.e. rear is 0

```Java
@SuppressWarnings("unchecked")
public ArrayQueue(int intialCapacity) {
	rear = 0;
	queue = (T[])(new Object[initialCapcity);
}
```

## Enqueue

- To enqueue means to assign the object reference of adding the object to the rear of the queue.
- We also need to update the value of rear.

```Java
public void enqueue(T element) {
	if(size() == queue.length)
		throw new IllegalStateException("Queue full in enqueue()");
		
	queue[rear] = element;
	rear++;
}
```

## Dequeue

- To deque means that the object reference that is kept in the array cell with the index with the index 0 is needed to be removed.
- All other elements within the queue are needed to be shifted also.

```Java
public T dequeue() {
	if(isEmpty()) {
		throw new IllegalStateException("Queue empty in dequeue");
	T result = queue[0];
	rear--;
	for(int scan = 0; scan < rear; scan++) {
		queue[scan] = queue[scan + 1];
	}
	queue[rear] = null;
	return result;
}
```