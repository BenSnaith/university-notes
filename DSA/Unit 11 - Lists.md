### Unit Objectives

- Model a doubly linked list.

- Learn how to implement an iterator for doubly linked lists.

- Learn how indexed and ordered list ADTs and how to implement them.

- Learn about when to use a list.

- Describe the time complexity of list operations using the Big-O notation.

- Consider some implementations of lists in the JCF.

### Self-referential Object

An object can reference to another object of the same type

```java
public class Person {
	private Person mother;
	private String name;
	private boolean isFemale;
	
	public Person(boolean isFemale, String name, Person mother) {
		this.isFemale = isFemale;
		this.name = name;
		this.mother = mother;
	}
	
	/* This person gives birth to another person */
	public Person givesBirth(String childName, boolean isFemale) {
		if(!this.isFemale)
			throw new UnsupportedOperationException("!!!");
		return new Person(isFemale, childName, this);
	}
	// Other methods omitted
}
```

### An Improved Class `Person`

- We enable a mother to record who her child is by using another `Person` reference:

```java
import java.util.ArrayList;

public class Person {
	private boolean isFemale;
	private String name;
	
	private Person mother;
	private Person child;
}
```

- We assume a single child policy here (lol).

### Modified Constructor & `givesBirth`

```java
	public person(boolean isFemale, String name, Person mother) {
		this.isFemale = female;
		this.name = name;
		this.mother = mother;
		this.child = null;
	}
	
	public Person givesBirth(String childName, boolean isFemale) {
		if(!this.isFemale)
			throw new UnsupportedOperationException("!!!");
			
		if(child != null)
			throw new UnsupportedOperationException("One child only!");
			
		child = new Person(isFemale, childName, this);
		return child;
	}
	// futher methods omitted.
```

The 'family line' that is build up by repeated calls to `givesBirth` is *doubly linked*. One can just as easily traverse the family line.

### Doubly-linked Objects: an Illustration

Both mother and daughter will now have knowledge of each other...

![[Pasted image 20241117161119.png]]

### Singly Linked List

- A singly linked list has one reference in each node.

![[Pasted image 20241117161212.png]]

- Each node knows its follower node.

### Doubly Linked List

- A doubly linked list has two references in each node: *previous* and *next*:

![[Pasted image 20241117161324.png]]

- Each node knows its *previous* node and its *follower* node.

### Modelling Doubly Linked Lists

A doubly linked list is made up of one or more doubly linked node(s):

```java
public class DoubleNode<T> {
	private DoubleNode<T> previous;
	private DoubleNode<T> next;
	private T element;
	
	public DoubleNode(T elem) {
		next = null;
		element = elem;
		previous = null;
	}
	
	public DoubleNode<T> getPrevious() {
	
	}
	
	public void setPrevious(DoubleNode<T> dnode) {
		previous = dnode;
	}
	
	// Other method details omitted (same as far for LinkedNode).
}
```

### Doubly Linked Lists: Advantages

- Each node of doubly linked list has a reference to both the next and previous nodes in the list.

	- We can move easily backwards and forwards.

- You can choose to traverse the linked list in reverse order.

- It is also easier to support the `remove` operation of an `Iterator` over a doubly linked list.

![[Pasted image 20241117161858.png]]

### Recap on issue with class `LinkedIterator`

- In Unit 5, `LinkedSet` utilises a *linear singly linked structure* to model its contents

- Class `LinkedIterator` in Unit 5 (which keeps track of the current node only) has no means to support method `remove`, even if class `LinkedSet` does not keep the `int` field size.

- Why?

### Doubly Linked List Disadvantages

- The downside of doubly-linked lists is that there are increased storage overheads.

	- Each node now must contain three reference fields, `element`, `next`, `prev`

- More *'book keeping'* is now required to manage the links in doubly-linked list operations, e.g.

	- Insertion and removal of nodes in the middle of a linked list both require modifications to the previous node.

### Modelling Doubly Linked Lists

To model a doubly linked list using a linear linked structure, we define:

- `DoubleNode`: to model a node within a doubly linked list.

- An *abstract* class `DoubleList`: to model a doubly linked list.

	- This will be used as the basis on which to build variously doubly linked linear structures such as an ordered set, an ordered list and an indexed list.

- An inner class `DoubleInterator`: to provide an iterator for a doubly linked list.

	- Unlike `LinkedIterator` in Unit 5, `DoubleIterator` will support the `remove` operation.

### Abstract Class `DoubleList`

![[Pasted image 20241117171835.png]]

### Abstract Class `DoubleList`

- Class `DoubleList` is `abstract`

	- Instances of `DoubleList` cannot be created.

- Unusually, all the methods of this abstract class are concrete.

	- This is to ease the burden of implementations of extension of this class.

- Most of the methods of this class are `protected`

	- They are not intended to be used by general client code, but rather are *utility methods* to be used by implementer of various collection ADTs

- We will use this class to implement some useful collection ADTs such as ordered lists and indexed lists.

- The simpler methods such as `isEmpty` and `size` are `public` and may be called by client code directly.

- Three `protected` data fields: `count`, `front` & `rear`.

### `DoubleList.java`

```java
import java.util.Iterator;

public abstract class DoubleList<T> {
	protected DoubleNode<T> front;
	protected DoubleNode<T> rear;
	protected int count;
	
	/* Constructor: Creates an empty list. */
	protected DoubleList() {
		rear = null;
		front = null;
		count = 0;
	}
}
```

### `removeLast`

```java
/* Removes and returns last element in the list. */
protected T removeLast() {
	if(isEmpty())
		throw new IllegalStateException("List Empty");
		
	T result = rear.getElement();
	rear = rear.getPrevious();
	count--;
	if(rear == null)
		front = null;
	else
		rear.setNext(null);
		
	return result;
}
```

### `removeFirst`,  `removeLast` and `remove`

```java

protected T removeFirst() {
	if(isEmpty())
		throw new IllegalStateException("Empty List");
		
	T result = front.getElement();
	front = front.getNext();
	count--;
	if(front == null)
		rear = null;
	else
		front.setPrevious(null);
		
	return result;
}

protected T removeLast() {
	if(isEmpty())
		throw new IllegalStateException("Empty List");
		
	T result = rear.getElement();
	rear = rear.getPrevious();
	count--;
	if(rear == null)
		front = null;
	else
		rear.setNext(null);
		
	return result;
}

protected void remove(DoubleNode<T> node) {
	if(node == null)
		throw new IllegalArgumentException("Null node");
	if(isEmpty())
		throw new IllegalStateException("List empty");

	if(node == front)
		this.removeFirst();
	else if(node == rear)
		this.removeLast();
	else {
		
	}
}
```

### `addFirst`, `addLast` & `addAfter`

```java
/* adds the element at the head of the list */
protected void addFirst(T element) {
	DoubleNode<T> node = new DoubleNode<T>(element);
	node.setNext(front);
	front = node;
	
	if(count == 0)
		rear = node;
	else
		front.getNext().setPrevious(node);
	count++;
}

protected void addLast(T element) {
	DoubleNode<T> node = new DoubleNode<T>(element);
	node.setPrevious(rear);
	rear = node;
	
	if(count == 0)
		head = node;
	else
		rear.getPrevious().setNext(node);
	count++;
}

protected void addAfter(DoubleNode<T> current, T element) {
	if(current == null)
		throw new IllegalArgumentException("Null node");
		
	if(current == rear) {
		addLast(element);
	}
	else {
		DoubleNode<T> node = new DoubleNode<T>(element);
		node.setNext(current.getNext());
		node.setPrevious(current);
		current.getNext().setPrevious(node);
		current.setNode(node);
		count++;
	}
}
```

### `find`

```java
// Returns first node containing the target or null if not found
protected DoubleNode<T> find(T target) {
	DoubleNode<T> cursor = front;

	while(cursor != null) {
		if(target.equals(cursor.getElement())) {
			return cursor;
		}
		else {
			cursor = cursor.getNext();
		}
	}
	return null;
}

// Returns true if the list contains the element and false
// otherwise
public boolean contains(T element) {
	return (find(element) != null);
}
```

### `iterator` and other methods

```java
public boolean isEmpty() {
	return (count == 0);
}
	
public int size() {
	return count;
}
	
public void clear() {
	front = null;
	rear = null;
	count = 0;
	// garbage collector does the rest
}
	
public Iterator<T> iterator() {
	return new DoubleIterator();
}
	
	private class DoubleIterator implements Iterator<T> {
		// next node to be returned by the iterator
		private DoubleNode<T> cursor;
		// node that will be returned at the end of the function
		private DoubleNode<T> node;
			
		public DoubleIterator() {
			cursor = front;
			node = null;
		}
			
		public boolean hasNext() {
			return (cursor != null);
		}
			
		public T next() {
			if(!hasNext())
				throw new IllegalStateException("no next element");
			node = cursor;
			T result = cursor.getElement();
			cursor = cursor.getNext();
			return result;
		}
			
		public void remove() {
			if(node == null)
				throw new IllegalStateException("no element to remove");
				
			if(node == rear) {
				rear = rear.getPrevious();
				if(rear == null) {
					front = null;
				}
				else {
					rear.setNext(null);
				}
			}
			else if(node == front) {
				front = front.getNext();
				front.setPrevious(null);
			}
			else {
				node.getNext().setPrevious(node.getPrevious());
				node.getPrevious().setNext(node.getNext());
			}
			count--;
			node = null;
		}
	}
}
```

### `DoubleIterator` vs `LinkedIterator`

```java
private class 
```

### Abstract Data Types: Lists

- Lists are linear collections

	- Lists are more flexible than stacks or queues.

- Elements can be added or removed anywhere within a list.

- Two types of list collections:
	- ordered (or sorted) list
	- indexed lists

### Ordered & Indexed Lists

- The elements in an ordered or sorted list are sorted by some inherent characteristic of the elements.

- For example:
	- names in alphabetical order.
	- scores in ascending order.
	- events in chronological order.

- In an indexed list, elements are referenced by their numerical position or index in the list.

	- There is often no inherent order relationship among then elements.

### A conceptual view of an Ordered List

Adding an element 54 to an ordered list...

![[Pasted image 20241117220454.png]]

Assume that a new element 34 is to be added to the above ordered list. Upon the completion of the operation, where in the list would the newly added element be?

### A conceptual view of an Indexed List

Elements can be added anywhere within the list...

# picture

### A conceptual view of an Unordered List

# picture

### List Operations



### The `ListADT` Interface

```java
import java.util.Iterator;

public interface ListADT<T> extends Iterable<T> {
	
	T removeFirst();
	T removeLast();
	T first();
	T last();
	boolean isEmpty();
	int size();
	
	/* Removes the element from this list */
	boolean remove(T element);
	
	/* Returns true if the list contains target element */
	boolean contains(T target);
}
```

### The `OrderedListADT` Interface

- `OrderedListADT` has one new method `add(T element)`

- To belong to an ordered list, elements must have a natural order.

- If objects in a class are expected to have an inherent order, the class must implement the standard Java interface.

	`java.lang.Comparable<T>`

- This interface specifies a single method `compareTo`:

```java
	int compareTo(T obj);
```

The meaning of the value returned to by this method is as follows:

- < 0: `this` object should precede the given object `obj`
- = 0: `this` object has the same natural order as `obj`
- > 0: `this` object should come after the given object `obj`

### `OrderedListADT.java`

To ensure that the type is used to instantiate the generic interface has an inherent order, we must qualify the genetic parameter as follows:

`<T extends Comparable<T>>`

```java
public interface OrderedListADT<T extends Comparable<T>> extends ListADT<T> {
	// Adds the element to the list at its proper location
	void add(T element);	
}
```

T must be instantiated with a type (i.e. class) that implements the `java.lang.Comparable` interface.

### A Linked Implementation of an Ordered List

```java
public class LinkedOrderedList<T extends Comparable<T>> extends ListADT<T> implements OrderedListADT<T> {
	public LinkedOrderedList() {
		super();
	}
	
	public boolean remove(T element) {
		DoubleNode<T> temp = find(element);
		if(temp == null)
			return false;
		super.remove(temp);
		return true;
	}
}
```

`remove` uses `find` to locate the node containing the element to remove, if it is present, It then uses the `remove` method of the super-class `DoubleList` to remove it.

### The method `add`

```java
public void add(T element) {
	if(front == null) {
		super.addFirst(element);
		return;
	}
	
	DoubleNode<T> cursor = front;
	while(cursor != null
	&& element.compareTo(cursor.getElement()) > 0) {
		cursor = cursor.getNext();
	}
	
	if(cursor == null)
		super.addLast(element);
	else
		super.addBefore(cursor, element);
}
```

`add` searches through the list to locate where the new node should be added. It then uses the `addBefore` method of `DoubleList` to add it.

- It must also deal with special cases where the list is empty and where the element should be added to the end of the list.

### The methods `first` & `removeLast`

```java
// return the first element of the list
public T first() {
	if(front == null)
		throw new IllegalStateException("no first element");
	return front.getElement();
}

// remove and return the last element in the list
public T removeLast() {
	return super.removeLast();
}
```

`removeLast` simply uses `removeLast` of the super-class `DoubleList` to remove it.

### Using an Ordered List

- Within an ordered list, elements are ordered by their inherent order.

	- The knowledge of ordering is defined within the element itself.

- Some objects have natural order, e.g.

	- `String`, `Integer`, `Double`, `Date`.
	
- For objects that do not have a natural order, e.g. `Employee`, `Car` and `Ticket` objects, we can introduce an order by explicitly defining it in the class definition.

Employee may be ordered by: name, id, seniority, position, etc.

- Suppose that we want to keep track of the name of the employees (of class `Employee`) of a company and their years of service.

- The `Employee` objects are kept in a list ordered by their years of service. If the years of service are equal, employees are ordered alphabetically.

- Thus, class `Employee` will need to implement interface `Comparable<T>` and provide an implementation of `compareTo`.

- To implement this method, we can simply compare the instance variable `years` in the two `Employee` objects and then compare the `name` fields if the `years` fields are the same.

- When an `Employee` object is to be added to a list, `compareTo` will be used to determine the position of this object within the list.

### Class `Employee`

Ordered by seniority and then by name alphabetically:

```java
public class Employee implements Comparable<Employee> {
	private String name;
	private int years;

	// the compare to method
	public int compareTo(Employee another) {
		int result;

		if(this.years > another.getYears())
			result = 1;
		else if(this.years < another.getYears())
			result = -1;
		else 
			result = (this.name.compareTo(another.getName()));

		return result;
	}
	// other method definitions omitted
}
```

### The `IndexedListADT` interface

```java
public interface IndexedListADT<T> extends ListADT<T> {
	// return the ith element of the list.
	public T get(int i);

	// set the ith element of the list, returning the old ith
	// element.
	public T set(int i, T element);

	// remove and return the ith element of the list.
	public T remove(int i);

	// insert the element at index i in the list
	public void add(int i, T element);

	// return the index of the first occurence of the element
	// or -1 if the element is not in the list
	public int indexOf(T element);
}
```

### ListADTs and Implementations

![[Pasted image 20241118002501.png]]

### A Linked Implementation of an Indexed List

- It is useful to define a private utility method `findNode` which returns a reference to the `ith` node of the list.

```java
public class LinkedIndexedList<T> extends DoubleList<T> implements IndexedListADT<T> {
	public LinkedIndexedList() {
		super();
	}

	private DoubleNode<T> findNode(int i) {
		if(i < 0 || i >= count) {
			throw new IllegalArgumentException("findNode index: " + i);
			DoubleNode<T> current = front;
			for(int j = 0; j < i; j++) {
				current = current.getNext();
			}
			return current;
		}
	}
}
```

### `LinkedIndexedList`: `get` and `set`

- `get` returns the element in node returned by `findNode`.

- `set` locates the `ith` node using `findNode`, changes the element stored in the node and then returns the old element.

```java
	public T get(int i) {
		return findNode(i).getElement();
	}

	public T set(int i, T element) {
		DoubleNode<T> node = findNode(i);
		T res = node.getElement();
		node.setElement(element);
		return res;
	}
```

### `LinkedIndexedList`: `remove`

- `remove` locates the `ith` node using `findNode`, then removes the node using `super.remove` and returns the element.

```java
	public T remove(int i) {
		DoubleNode<T> node = findNode(i);
		T res = node.getElement();
		super.remove(node);
		return res;
	}
```

### `LinkedIndexedList`: `add`

- `add` checks the index for the special cases of addition at he front of the end of the list and calls `addFront` or `addLast` as appropriate.

- It then uses `findNode` to located the `ith` and uses `addBefore` to add a new node before the current `ith` node.

```java
	public void add(int i, T element) {
		if(i == 0) {
			super.addFirst(element);
		}
		else if(i == count) {
			super.addLast(element);	
		}
		else {
			DoubleNode<T> next = findNode(i);
			super.addBefore(next, element);	
		}
	}
```

### `LinkedIndexedList`: `indexOf`

```java
	public int indexOf(T target) {
		DoubleNode<T> cursor = front;
		int position = 0;

		while(cursor != null) {
			if(target.equals(cursor.getElement())) {
				return position;	
			}
			else {
				position++;
				cursor = cursor.getNext();	
			}
		}
		return -1;
	}
```

### Implementing Lists with Arrays

- An array implementation of a list could follow strategies similar to those used for a queue.

- We could fix one end of the list at index 0 and shift as needed when an element is added or removed

![[Pasted image 20241118004011.png]]

- A circular array is not much help here as shifts cannot be avoided if an element is added or removed from the middle of the list.

### An Array Implementation of an Indexed List

- Due to the indexed nature, array is a natural choice for implementing an indexed list.

- Elements are kept contiguously at one end of the array.

- An integer variable (size) stores the number of elements in the list, and is also the index of the first empty cell in the array.

- In order to allow the list to grow indefinitely, we will need to perform "expand capacity".

- An integer variable (capacity) holds the current size of the underlying array used to store the elements of the list.

### `ArrayList`: an array implementation of an indexed list

```java
import java.util.Iterator;

public class ArrayList<T> implements IndexedListADT<T> {
	public static final int DEFAULT_CAPACITY = 20;
	private T[] elems;
	private int size;
	private int capacity;

	public ArrayList(int initialCapacity) {
		elems = (T[]) (new Object[initialCapacity]);
		size = 0;
		capacity = initialCapacity;	
	}

	public ArrayList() {
		this(DEFAULT_CAPACITY);	
	}

	public int size() {
		return size;	
	}

	public boolean isEmpty() {
		return (size == 0);	
	}

	public void clear() {
		size = 0;	
	}

	// returns true if the array contains the specified elem
	public boolean contains(T elem) {
		return (indexOf(elem) != -1);	
	}
}
```

### `ArrayList`: `extendArray`

- When the array is extended, the elements of the old array are copied to the new array leaving a gap at position gap.

	- The new element can be added without any further element shifting

```java
	private void extendArray(int gap) {
		capacity *= 2;

		T[] newElems = (T[]) (new Object[capacity]);

		for(int i = 0; i < gap; i++) {
			newElems[i] = elems[i];	
		}
		for(int i = gap; i < size; i++) {
			newElems[i + 1] = elems[i];	
		}
		elems = newElems;
	}
```

- On average, this saves n / 2 assignments whenever the underlying array is extended (where n is the size of the list).

### `ArrayList`: `add`

Adds the specified element to the list at index i (i <= size) and shifts the existing elements within indices >= i up by 1 to make room:

```java
	public void add(int i, T elem) {
		if(i > size || i < 0) {
			throw new IndexOutOfBoundsException("ArrayList.add: index " + i);	
		}

		if(size == capacity) {
			extendArray(i);
		}
		else {
			for(int j = size; j > i; j--) {
				elems[j] = elems[j - 1];
			}
		}
		elems[i] = elem;
		size++;
	}
```

### `ArrayList`: `indexOf`

```java
	// returns the index of the first occurence
	// (if any) of elem in the array returns -1
	// if the element is not present
	public int indexOf(T elem) {
		for(int i = 0; i < size; i++) {
			if(elem.equals(elems[i])) {
				return i;
			}
		}
		return -1;
	}
```

### `ArrayList`: `get`, `set`

```java
	// returns the element at position i
	public T get(int i) {
		if(i < size && i >= 0) {
			return elems[i];
		}
		else {
			throw new
				IndexOutOfBoundsException("ArrayList.get: index" + i);
		}
	}

	// sets the element at index i to elem
	// returns the previous value of the element stored there
	public T set(int i, T element) {
		T res;
		if(i < size && i >= 0) {
			res = elems[i];
			elems[i] = element;
			return res;
		}
		else {
			throw new
				IndexOutOfBoundsException("ArrayList.set: index " + i);
		}
	}
```

### `ArrayList`: `remove`

Remove the element at index i from the list and shifts existing elements with indices > i down by 1 to fill the gap.

```java
	public T remove(int i) {
		if(i >= size || i < 0) {
			throw new
				IndexOutOfBoundsException("ArrayList.remove: index " + i);
		}

		T elem = elems[i];

		// shift the elements with index > i down by one
		for(int j = i + 1; j < size; j++) {
			elems[j - 1] = elems[j];
		}

		size--;
		return elem;
	}
```

O(n)

### `ArrayList`: `iterator`

- The iterator is implemented using an inner class and now supports the `remove` operation.

- This new version of `ArrayIterator`:

	- May access the private fields of `ArrayList`.

	- Does not require any parameters.

	- Supports the `remove` operation.

```java
	public Iterator<T> iterator() {
		return new ArrayIterator();
	}
```

### The `ArrayIterator` inner class

```java
private class ArrayIterator implements Iterator<T> {
	private int cursor;

	private int current;

	public ArrayIterator() {
		cursor = 0;
		current = -1;
	}

	public boolean hasNext() {
		return (cursor < size);
	}

	// other method implementations omitted
}
```

### The `ArrayIterator` inner class: `next`

```java
	public T next() {
		if(!hasNext())
			throw new IllegalStateException();

		current = cursor;

		T result = elems[cursor];
		cursor++;
		return result;
	}
```

### The `ArrayIterator` inner class: `remove`

```java
	public void remove() {
		if(current == -1) {
			throw new
				IllegalStateException("No current element to remove");
		}

		for(int i = current; i < size; i++) {
			elems[i] = elems[i + 1];
		}
		size--;
		cursor--;
		current = -1;
	}
```

### An Array Implementation of an Ordered List

- It is convenient to base the implementation of `OrderedArrayList` on that of `ArrayList`.

	- `ArrayList` is practically an indexed list.

	- If we simply extend the class `ArrayList`; we will inherit too may methods

	- Inheriting method such as add element at index and set element at index in class `ArrayList` would be very likely to violate the inherent ordering of the ordered list.

- We could define an abstract class implementing the common operations of indexed and ordered lists and then extend this.

	- This will lead to more complex class hierarchy.

- A better way would be to reuse an existing class, but restrict the available operations that can be performed.

- We hide an instance of the existing class as a private field of the new class.

- Provide `wrapper` methods to call only those methods of the hidden class which is safe for clients to use.

	- This is the same approach used in class `PureStack`

### Analysis of `IndexedList` Operations

- `get`

- `set`

- `removeFirst`

- `removeLast`

- `addFirst`

- `addLast`

- `remove`

- `add`

### Lists in JCF

![[Pasted image 20241118223223.png]]

