## Unit Objectives

- Learn about the fundamental concept behind linked data structures.
- Learn how to model different kinds of linked data structures.
- Learn how to implement various ADTs using linear linked data structures (aka linked lists)
- describe the time implications of processing linear linked data structures using Big-O notation.

## Linked Structures

How do linked structures work?

- What are the fundamental building blocks of a linked structure?
- How to implement and manipulate such building blocks in Java?

## Linking Objects and Object References

- A linked structure uses object reference variables to link one object to another.
- An object reference can be seen as a _pointer_ to an object.

![[image 20.png|image 20.png]]

## Self-referential Objects: an Example

- An object can hold a reference to another object, even one of the same class. e.g.

```Java
public class Person {
	private Person mother;
	private String name;
	private boolean childBearing;
	private String address;
	// Constructor and methods omitted.
}
```

## Self-referential Objects: an Illustration

We can represent a partial family tree which only shows the mother’s side of the ancestry information.

![[image 1 9.png|image 1 9.png]]

## Linked Structures

- The fundamental building blocks of a linked structure are self-referential objects:

![[image 2 8.png|image 2 8.png]]

- One object references another, which refers to another and so on and so forth.

![[image 3 8.png|image 3 8.png]]

- Each object in the linked structure is often known as a node.
- A linked structure is dynamic because its size may grow or shrink as needed. unlike an array where the size is fixed.
- A linked structure can be linear or non-linear:
    - A linked list is a linear structure
        - Typically, each node only makes reference to ≤ 1 other node.
            
            (Except for double linked lists sometimes called deques).
            
    - Trees and graphs are both non-linear structures.
        - Each node may make reference to > 1 other node.

## Non-linear Linked Structures: Trees & Graphs

![[image 4 8.png|image 4 8.png]]

## Linear Linked Structures

![[image 5 7.png|image 5 7.png]]

- The references in a linked structure must be carefully managed to maintain the integrity of the structure.
- The entry point front into the list must be maintained properly.
- The order in which certain steps are taken is often very important.

## Inserting a node at the front of a linked structure

![[image 6 5.png|image 6 5.png]]

## Inserting a node in the middle of a linked structure

![[image 7 5.png|image 7 5.png]]

## Deleting the first node in a linked structure

![[image 8 4.png|image 8 4.png]]

## Deleting an interior node from a linked structure

![[image 9 4.png|image 9 4.png]]

While traversing a linked structure, always keep a record of the previous and the current.

1. Look for the node `previous` that makes a reference to the node we want to delete `current`
2. Find the node `next` that current is making a reference to.
3. Make the `previous` node reference the `next` node cutting the current out of the equation.

## Elements without inbuilt links

- Objects of classes such as `Person` naturally have links to objects of the same class and can easily be built into linked structures.
- What if we want to build up a linked structure of object of some class T, say, which does not have such inbuilt links?
    - The solution is to wrap the objects of type `T` in a `Node` class the references other `Node` objects of the linked structure.

![[image 10 4.png|image 10 4.png]]

Class `Node` is a generic class which uses the type variable `T`

## Elements without Inbuilt Links

![[image 11 4.png|image 11 4.png]]

- A generic linear collection can store any one kind of object.

## `LinearNode.java`

```Java
public class LinearNode<T> {
	private T element;
	private LinearNode<T> next;
	
	public LinearNode() {
		next = null;
		element = null;
	}
	
	public LinearNode(T elem) {
		next = null;
		element = elem;
	}
	
	public LinearNode<T> getNext() {
		return next;
	}
	
	public void setNext(LinearNode<T> node) {
		next = node;
	}
	
	public T getElement() {
		return element;
	}
	
	public void setElement(T elem) {
		element = elem;
	}
}
```

## Illustration: Tracing the node trail.

- Consider the class `LinearNode<T>`
- The following method created a linked list of n nodes.

```Java
LinearNode<Integer> linkedList = null;

for(int i = 0; i <= n; i++) {
	LinearNode<Integer> node = new LinearNode<>(i);
	node.setNext(linkedList);
	linkedList = node;
}
```

- Let’s assume `n = 4`
    
    Using an object diagram, sketch the underlying linked list at each iteration of the above for-loop.
    

## A Linked List Implementation of Stack

![[image 12 3.png|image 12 3.png]]

![[image 13 3.png|image 13 3.png]]

## The ADT Stack: a recap

- A stack is a linear collection whose elements are added and removed from one end.
- A stack is a LIFO collection.
    
    The last element to be put on the stack is the first element to be removed.
    
    ![[image 14 3.png|image 14 3.png]]
    

```Java
public interface StackADT<T> {
	public void push(T element);
	
	public T pop();
	
	public T peek();
	
	public boolean isEmpty();
	
	public int size();
}
```

## The `LinkedStack` Class.

- A stack ADT can also be implemented using linked list.
- The `LinkedStack` class models a stack using a linked list.
- A linked list is made up of a linear sequence of node objects.
    - We simply use the `LinearNode` class.
- We keep a reference to the top of the stack and an integer count of the number of nodes in the stack.

![[image 15 2.png|image 15 2.png]]

## `LinkedStack` method: `push()`

Pushing an element into the stack means adding an element at the font of the linked list.

![[image 16 2.png|image 16 2.png]]

```Java
public void push(T element) {
	LinearNode<T> temp = new LinearNode<T>(element);
	
	temp.setNext(top);
	top = temp;
	count++;
}
```

## `LinkedStack` method: `pop()`

Popping an element from the stack means removing the first element in the linked list.

![[image 17 2.png|image 17 2.png]]

```Java
public T pop() {
	if(isEmpty()) 
		throw new IllegalStateException("Stack Empty in pop()");
		
	T result = top.getElement();
	top = top.getNext();
	count--;
	
	return result;
}
```

## `LinkedStack` method: `peek()`

The method peek simply returns the object reference to the element that is get in the first node of the linked structure

```Java
public T peek() {
	if(isEmpty())
		throw new IllegalStateException("Stack Empty in peek()");
		
	T result = top.getElement();
	return result;
}
```

## Summary: Analysis of `LinkedStack` Operations

- `LinkedStack` is an unbounded collection.
    - No need for expanding capacity
- Stack operations are generally efficient.
- None of the `LinkedStack` operations require an looping.
    - Hence, all of these stack operation can be performed in constant time O(1)

Aside:

If a bounded stack is to be implemented, which implementation is preferable, an array or linear linked structure

Answer:

Array would be easier to bound, but the time efficiency of moving all of the elements in the array to keep it memory contiguous would make it less efficient.

## A Linked List Implementation of a Queue

![[image 18 2.png|image 18 2.png]]

![[image 19 2.png|image 19 2.png]]

## The ADT Queue: a recap

- A queue is a linear collection whose elements are added at one end (i.e. the rear) and removed from another end (i.e. the front).
- A queue is FIFO

![[image 20 2.png|image 20 2.png]]

- Queue operations occur at both ends.

```Java
public interface QueueADT<T> {
	public void enqueue(T element);
	
	public T dequeue();
	
	public T first();
	
	public boolean isEmpty();
	
	public int size();
}
```

## `LinkedQueue`

- Using a linked list, no need for element shifting.
- The last node in the queue has its `next` link set equal to `null`.
- We need to keep track of the `front` and the `rear` of the queue. Also useful to keep track of its size in the field `count`.

![[image 21.png]]

## Advantages of `LinkedQueue`

- A linked list implementation is more flexible than an array because the size of the queue can grow and shrink as required at run-time.
- No storage space wasted creating initial storage for the cells in an array.
- There is no need to check in enqueue if the queue is already full.

However, in a linked queue, every node contains 2 references compared to an array element which only contains 1.

There are extra storage overhead for a queue of a given size.

![[image 22.png]]

## Class `LinkedQueue`: Constructor

```Java
public LinkedQueue() {
	front = null;
	back = null;
	count = 0;
}
```

## `LinkedQueue` method: `enqueue()`

To enqueue means to add an element to the rear of the linear linked structure.

![[image 23.png]]

```Java
public void enqueue(T elem) {
	LinkedNode<T> node = new LinkedNode<>(elem);
	if(isEmpty()) {
		// Creating a new queue with this element as the only node;
		front = node;
		back = node;
	}
	else {
		back.setNext(node);
		back = node;
	}
	count++;
}
```

## `LinkedQueue` method: `dequeue()`

To dequeue means to remove the first element from the linear linked structure.

![[image 24.png]]

```Java
public T dequeue() {
	if(isEmpty())
		throw new IllegalStateException("Queue Empty");
	
	T result = front.getElement();
	front = front.getNext();
	count--;
	
	if(isEmpty()) // implementation
	
	return result;
}
```

## `LinkedQueue.java`

```Java
public class LinkedQueue<T> implements QueueADT<T> {
	private LinearNode<T> front;
	private LinearNode<T> back;
	
	public LinkedQueue() {
		count = 0;
		front = null;
		rear = null;
	}
	
	public boolean isEmpty() {
		return front == null;
	}
	
	public int size() {
		return count;
	}
	
	public void clear() {
		front = null;
		rear = null;
		count = 0;
	}
}
```

## A LinkedList Implementation of Set

![[image 25.png]]

![[image 26.png]]

## The ADT Set

- A set is a collection of distinct elements of a particular type, e.g. the set of vowels
    
    { a, e, i, o, u }
    
- A set is logically an unordered collection, where each element can appear at most once.

```Java
public interface SetADT<T> extends Iterable<T> {
	boolean add(I element);
	boolean contains(T element);
	boolean isEmpty();
	int size();
	
	boolean addAll(SetADT<T> A);
	boolean removeAll(SetADT<T> A);
	boolean retainAll(SetADT<T> A);
	
	SetADT<T> union(SetADT<T> A);
	SetADT<T> intersection(SetADT<T> A);
	SetADT<T> difference(SetADT<T> A);
	
	boolean isSubset(SetADT<T> A);
	boolean equals(SetADT<T> A);
}
```

## `LinkedSet`

![[image 27.png]]

Using a linked list, we will implement a set class named `LinkedSet`

- We may need to remove elements from the middle of the linked list.
- New elements will always be added at the start of the list.

![[image 28.png]]

As with `ArraySet`, this class will extend `AbstractSet` where some methods of `setADT` (e.g. `addAll` and `removeAll` ) are implemented in terms of add and remove.

![[image 29.png]]

## `LinkedSet.java`

```Java
public class LinkedSet<T> extends AbstractSet<T> {
	private int count;
	private LinearNode<T> contents;
	
	public LinkedSet() {
		count = 0;
		contents = null;
	}
	
	public boolean isEmpty() {
		return contents == null;
	}
	
	public int size() {
		return count;
	}
	
	public void clear() {
		contents = null;
		count = 0;
	}
}
```

## `LinkedSet` method: `contains()`

```Java
public boolean contains(T elem) {
	LinearNode<T> current = contents;
	while(current != null) {
		if(elem.equals(current.getElement()) {
			return true;
		}
		else {
			current = current.getNext();
		}
	}
	return false;
}
```

## `LinkedSet` method: `add()`

```Java
public boolean add(T element) {
	if(!contains(element)) {
		LinearNode<T> node = new LinearNode<T>(element);
		
		node.setNext(contents);
		
		count++;
		return true;
	}
	return false;
}
```

## `LinkedSet` method: `remove()`

To remove a specified element from a `LinkedSet` means one of the following:

- Remove the first node in the linked list.

![[image 30.png]]

- Remove an interior node from the linked list.

![[image 31.png]]

```Java
public boolean remove(T element) {
	if(contents == null) {
		return false;
	}
	else { // Special case where the element if the first in the list
		if(element.equals(contents.getElement()) {
			contents = contents.getNext();
			count--;
			return true;
		}
	}
	LinearNode<T> previous = contents;
	LinearNode<T> current = contents.getNext();
	while(current != null) {
		if(element.equals(current.getElement())) {
			previous.setNext(current.getNext());
			count--;
			return true;
		}
		else {
			previous = current;
			current = current.getNext();
		}
	}
	return false;
}
```

## `LinkedSet` method: `copy()`

```Java
public LinkedSet<T> copy() {
	LinkedSet<T> result = new LinkedSet<>();
	LinearNode<T> current = contents;
	LinearNode<T> newNode;
	
	while(current != null) {
		newNode = new LinearNode<>(current.getElement());
		newNode.setNext(result.contents);
		result.contents = newNode;
		current = current.getNext();
	}
	result.count = this.count;
	return result;
}
```

## `LinkedSet` method: `union()`

```Java
public SetADT<T> union(SetADT<T> A) {
	LinkedSet<T> result = this.copy();
	
	result.addAll(A);
	
	return result;
}
```

## `LinkedSet` method: `iterator()`

To compete the implementation of `LinkedSet`, we need to define an `iterator()` method as the class implements the `Iterable` interface:

```Java
public Iterator<T> iterator() {
	return new LinkedIterator<T>(contents);
}
```

Method `iterator()` creates a new type of `Iterator` object to handle iteration over this `LinkedSet` object.

A `LinkedIterator` object specialises in iterating over a linear linked structure.

## `LinkedIterator` Illustration

A conceptual view of the contents of a set…

![[image 32.png]]

The actual representation of the contents in the set…

![[image 33.png]]

To iterate over the contents of a `LinkedSet` means to iterate over the elements within the underlying linear linked structure.

## `LinkedIterator`

![[image 34.png]]

A `LinkedIterator` object uses a `LinearNode` variable (cursor) to keep track of the node in the linked list that is to be returned whenever method `next()` in invoked.

## `LinkedIterator.java`

```Java
import java.util.Iterator;
public class LinkedIterator<T> implements Iterator<T> {
	private LinearNode<T> cursor;
	
	public LinkedIterator(LinearNode<T> contents) {
		cursor = contents
	}
	
	public boolean hasNext() {
		return (cursor != null);
	}
	
	public T next() {
		if(!hasNext()) {
			throw new IllegalStateException("no next element");
		}
			T result = cursor.getElement();
			cursor = cursor.getNext();
		  return result;
		}
	}
}
```