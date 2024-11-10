## Unit Objectives

- Learn how to implement a QueueADT using a ‘circular’ array.
- Learn about priority queues.
- Learn how to implement a priority queue using:
    - A linked list
    - An array of FIFO queues
- Describe the time implication of performing queue operations using the Big-O notation.
- Consider implementations of queue in the JCF.

## An Array Implementation of QueueADT

- An array-based implementation of the bounded QueueADT with the front of the queue fixed at index 0 has a drawback:
    - The time complexity of `dequeue` method was O(n)

![[image 36.png|image 36.png]]

## Another Array Implementation of QueueADT

- Is there a way to use an array to implement a QueueADT without having to perform shifting?
    - YES!
- If we do not fix one end of the queue at index 0, we will not have to shift the elements…

![[image 1 11.png|image 1 11.png]]

- A circular queue (or circular buffer) utilises an array that conceptually wraps around on itself:
- The last index is thought to be followed by index 0.

## Class `CircularArrayQueue`

![[image 2 10.png|image 2 10.png]]

- We keep track of two integers for indicating the front and rear of the queue at any given time.
- To distinguish between empty and full queues where front and rear are equal, we may record to size of the queue in count.

## Circular Queues

![[image 3 10.png|image 3 10.png]]

## Class `CircularArrayQueue`

![[image 4 10.png|image 4 10.png]]

```Java
public class CircularArrayQueue<T> implements QueueADT<T> {
	private final int DEFAULT_SIZE = 100;
}
```

## Circular Queue: `enqueue`

- When an element is enqueued, it is stored at index rear.
    
    rear is then incremented
    
- But we must allow for looping back to 0:

```Java
rear = (rear + 1) % queue.length;
```

- Also the array can reach its full capacity and may need enlarging

```Java
public void enqueue(T element) {
	if(size() == queue.length)
		expandCapacity();
		
	queue[rear] = element;
	rear = (rear + 1) % queue.length;
	
	count++;
}
```

## Unbounded Circular Queues: expand capacity

![[image 5 8.png|image 5 8.png]]

## Circular Queue: `expandCapacity`

```Java
private void expandCapacity() {
	T[] larger = (T[]) (new Object[queue.length * 2]);
	
	for(int scan = 0; scan < count; scan++) {
		larger[scan] = queue[front];
		front = (front + 1) % queue.length;
	}
	front = 0;
	rear = count;
	queue = larger;
}
```

- When existing elements are copied to the enlarged array, they are copied to the start of the enlarged array so that the front is again at index 0.

## Circular Queue: `dequeue`

- When an element is dequeued, it is retrieved from index `front` . `front` is them incremented.
    - We will also need to take care of ‘looping back’, i.e.
        
        `front = (front + 1) % queue.length;`
        

```Java
public T dequeue() 
{
	if(isEmpty())
		throw new IllegalStateException("Queue Empty");
		
	T result = queue[front];
	queue[front] = null;
	front = (front + 1) % queue.length;
	count--;
	return result;
}
```

## Some Uses of Queues: multi-threaded software applications

- Queues are often used in multi-threaded software application.
    
    Data items for processing are produced by ‘producer’ threads and deposited in a queue from where they are retrieved later by ‘consumer’ threads and processed.
    
    - The execution of the producer and consumer threads is largely decoupled.
- If at a certain time the producers are producing data faster than it can be consumed, the producers do not have to wait, they simply add their data items to the queue.
- When the consumers start to consume data faster than it can be produced, they will not be delayed as they can retrieve data items from the backlog in the queue.

## Some Uses of Queues: Ticket counter simulation

- Queues are often used in simulations to model real-life queues.
- A typical use of a queue is to simulate a waiting line.
    - Consider a waiting line at a ticket booth.
    - The goal is to determine how many cashiers are needed to keep the wait time < 7 minutes.
    - We will assume:
        - Customers arrive on average every 15 seconds.
        - Processing a request takes 2 minutes once a customer reaches a cashier.

## Ticket Counter Simulation: a UML description

![[image 6 6.png|image 6 6.png]]

## Ticket Counter Simulation: Algorithm

Simulate the ticket counter scenario using various numbers of cashiers@

1. Create the customer waiting queue
    
    - Each customer keeps track of their arrival and departure times.
    
    Assumption: Customers arrive on average every 15 seconds.
    
2. Each cashier needs to record the time they finished serving the last customer.
    
    - Modelled by an array of type `int[]` named `cashiers`
    - At the start of the simulation, each cashier is available at time 0 seconds.
    
    Assumption: Each cashier takes 2 minutes to serve one customer.
    

`final static int PROCESS = 120;`

1. Process all customers in the queue:
    1. Each cashier takes turn to serve a customer in the waiting queue.
        - If a customer arrives at a time when the cashier is busy, they will need to wait:
            
            customer dept time = cashier last service completion time + process time
            
        - If a customer arrives at a time when the cashier is free, no waiting is requires:
            
            customer dept time = customer arrival time + process time
            
    2. Update the cashier’s time accordingly.
    3. Accumulate the time that each customer actually spent at the ticket centre:
        
        customer time spend at the ticket booth = customer dept time - customer arrival time.
        
2. Output the average time that each customer spent at the ticket centre.

## Ticket Counter Simulation: Java Code

```Java
public static void main(String[] args) {
	LinkedQueue<Customer> customerQueue = new LinkedQueue<Customer>();
	int[] cashierTime = new int[MAX_CASHIERS];
	int totalTime, averageTime, departs;
	
	for(int cashiers = 0; cashiers < MAX_CASHIERS; cashiers++) {
		for(int count = 0; count < cashiers; count++) {
			cashierTime[count] = 0;
		}
		
		for(int count = 1; count < NUM_CUSTOMERS; count++) {
			customerQueue.enqueue(new Customer(count * 15));
		}
		
		totalTime = 0;
		
		
		// OMITTED
		
		
	}
}
```

## Priority Queues

- Most queues are first-in, first-out (FIFO) data structures, but sometimes it is useful for high priority data to ‘jump’ the queue and join a queue ahead of lower priority data.
- Data items of the same priority are still processed in a FIFO manner.
- The priority of data items is represented by a range of non-negative integer values.
    - 0 us the lowest priority up to a maximum priority value M.
- A priority queue can be implemented using a linked list or and array.
    - Elements are ordered by priority level of the data items involved.
- To enqueue an items means to insert it into a position in the list/array ahead of all lower priority items, but behind data items of higher or equal priority.

## Priority Queue: an Array Implementation

![[image 7 6.png|image 7 6.png]]

## Priority Queue: a Linked Structure Implementation

![[image 8 5.png|image 8 5.png]]

## Priority Queue Implementation

- Items can only be added to a priority queue if they have a priority level.

Can we simply define `LinkedPriorityQueue` as follows?

```Java
public class LinkedPriorityQueue<T> implements QueueADT<T>
```

- We ensure that items can only be added to a priority queue if they have an associated priority level by demanding that the data type T must implement an interface `Prioritised` , e.g.

```Java
public interface Prioritised {
	int getPriority();
	void setPriority(int level);
}
```

- To ensure that `LinkedPriorityQueue` is instantiated only with a type of T which implements Prioritised, the type variable in the class header must be qualified as:
    
    `<T extends Prioritised>`
    
    - This enables us to call `getPriority` from the body of methods of the generic class `LinkedPriorityQueue`.

## `LinkedPriorityQueue.java`

```Java
public class LinkedPriorityQueue<T extends Prioritised> implements QueueADT<T> {
	private LinearNode<T> front;
	
	private int count;
	
	public void enqueue(T elem) {
		LinearNode<T> tmp = new LinearNode<T>(elem);
		
		LinearNode<T> previous = null;
		LinearNode<T> current = front;
		while(current != null && current.getElement().getPriority() >= elem.getPriority) {
			previous = current;
			current = current.getNext();
		}
		
		if(previous == null) {
			tmp.setNext(front);
			front = tmp;
		}
		else {
			tmp.setNext(previous.getNext());
			previous.setNext(tmp);
		}
		count++;
	}
	
	public T dequeue() {
		if(isEmpty()) {
			throw new IllegalStateException("Queue Empty");
		}
		T item = front.getElement();
		
		front = front.getNext();
		count--;
		return item;
	}
}
```

## How to implement an efficient priority queue?

- A simple array-based implementation of priority queue is inefficient.

![[image 9 5.png|image 9 5.png]]

- A linked list based implementation of priority queue is slightly better, but not by much.

![[image 10 5.png|image 10 5.png]]

- There is a simple technique which is appropriate if the number of priority levels is not too large.

## A Multi-Queue Implementation

- Suppose the priority levels are integers and range from 0 (lowest) to M (highest).
    
    We implement the priority queue as an array `queueList` of size M + 1 of ordinary FIFO queues.
    
    - An item is `enqueued` in the normal way on the FIFO queue corresponding to its priority level.
    - The method `dequeue` works by calling the dequeue method of the non-empty queue with the highest priority

## Priority Queue: a Multi-Queue Implementation

![[image 11 5.png|image 11 5.png]]

## `PriorityQueue.java`

```Java
public class PriorityQueue<T extends Prioritised> implements QueueADT<T> {
	private QueueADT<T>[] queueList;
	
	private final int maxPriority;
	private int count;
	
	public PriorityQueue(int maxPriority) {
		this.maxPriority = maxPriority;
		queueList = (QueueADT<T>[]) Array.newInstance(QueueADT.class, maxPriority+1);
		for(int i = 0; i <= maxPriority; i++) {
			queueList[i] = new LinkedQueue<T>();
		}
		count = 0;
	}
	
	public void clear() {
		for(int i = 0; i <= maxPriority; i++) {
			queueList[i].clear();
		}
		count = 0;
	}
	
	public void enqueue(T element) {
		int index = element.getPriority();
		count++;
		queueList[index].enqueue(element);
	}
	
	public T dequeue() {
		if(count == 0) {
			throw new IllegalStateException("Queue empty");
		}
		int index = findQueue();
		count--;
		return queueList[index].dequeue();
	}
	
	private int findQueue() {
		for(int i = maxPriority; i >= 0; i--) {
			if(!queueList[i].isEmpty()) {
				return i;
			}
		}
		return -1;
	}
}
```

## Time Complexity of multi-FIFO Priority Queue Operations

- For the multi-FIFO queue implementation `PriorityQueue`, all queue operations are considered to execute in constant time.
    - As the number of priority levels is assumed small (30 or so), the loops in `clear` and `findQueue` execute in almost constant time.
- If the number of priority levels M because large, `clear` and `findQueue` (and `first` and `dequeue` which call `findQueue` ) would have time complexity O(M).

## Queues in JCF

- The interface `java.util.Queue<E>` specified five methods:
    - `element`
    - `offer`
    - `peek`
    - `poll`
    - `remove`
- Concrete implementation for `Queue<E>` includes:
    - `java.util.LinkedList<E>`
    - `java.util.ArrayDeque<E>`
    - `java.util.concurrent.LinkedBlockingQueue<E>`
    - `java.util.concurrent.ArrayBlockingDeque<E>`
    - `java.util.PriorityQueue`
    - etc

## Some queue-related classes and interfaces in JCF

![[image 12 4.png|image 12 4.png]]

## Double-ended Queue in JCF

- `java.util.Deque` in JCF models a “double-ended queue” which supports elements insertion and remove at both ends
- `Deque` can be used as a queue

![[image 13 4.png|image 13 4.png]]

- Concrete implementations include `ArrayDeque`, `LinkedBlockingDeque` and `LinkedList`, all in `java.util`
- `ArrayDeque` is likely to be faster than `LinkedList` when used as a queue.

## Class `PriorityQueue` in JCF

- JCF includes an implementation of priority queue named `java.util.PriorityQueue`, which is different from `dsaj.PriorityQueue` ,
    - Elements in `java.util.PriorityQueue` do not need to implement the `Priority` interface. They are ordered by their natural order
        - e.g. numerical for numbers, alphabetical for strings, or the order defined by `compareTo`
    - Elements with the same priority (i.e. they are ‘identical’ elements) in `java.util.PriorityQueue` are returned arbitrarily during dequeue or peek.

## Interface `BlockingQueue` in JCF

- `java.util.concurrent.BlockingQueue` models:
    
    “a queue that additionally supports operations that waits for the queue to become non-empty when retrieving an element, and wait for space to become available in the queue when storing an element.”
    
- Concrete implementation for `BlockingQueue<E>` includes:
    - `ArrayBlockingQueue<E>`: a bounded blocking queue back by an array
    - `LinkedBlockingQueue<E>`: an optionally bounded blocking queue based on linked nodes
    - `DelayQueue<E>`: an unbounded blocking queue of `java.util.concurrent.Delayed` elements, in which an element can only be taken when its delay has expired
- `BlockingQueue` implementations are designed to be used primarily for producer-consumer queues.

## Interface `TransferQueue` in JCF

- `java.util.concurrent.TransferQueue` is a specialised version of `java.util.concurrent.BlockingQueue` in which:
    
    “producers may wait for consumers to receive elements. A `TransferQueue` may be useful for example in message passing application in which producers sometimes (using method `transfer(E)`) wait receipt of elements by consumers invoking take or poll, while at other times enqueue elements (via method `put`) without waiting for receipt.”
    
- Class `java.util.concurrent.LinkedTransferQueue` is a concrete implementation of `TransferQueue`, which is an unbounded implementation of `TransferQueue` based on linked nodes.