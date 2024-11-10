### Unit Objective

- Consider how the ADT set can be used to solve a computing problem.
- Examine implementation of the set ADT in the JCF

### Intro

- What is a set?

A set is usually an unordered collection of items of the same type and is unique, if it is not unique then it has another name, a multiset.

- How to implement a set data structure?

i.e. How to model such a data structure and its standard operations?

- What is the typical time implication of performing an operation on a set collection?

When should we use a set collection?

### Set Operations

| __Operation__ | __Purpose__                                                           |
| ------------- | --------------------------------------------------------------------- |
| add           | Adds an element to the set.                                           |
| addAll        | Adds all elements in a given set to this set.                         |
| remove        | Removes a specified element from the set.                             |
| removeRandom  | Removes a random element from the set.                                |
| union         | Performs set union between two sets.                                  |
| equals        | Checks if a given set is the same as this set.                        |
| isSubset      | Checks if this set is a subset of a given set.                        |
| contains      | Checks whether a specified element is on the set.                     |
| isEmpty       | Checks whether the set is empty.                                      |
| size          | Return the number of elements in the set.                             |
| iterator      | Returns an iterator of this set.                                      |
| retainAll     | Retains all the elements in common with a passed in set.              |
| removeAll     | Removes all the elements in common with a passed in set.              |
| isSubset      | Returns true if all of the elements in the set match a passed in set. |
| intersection  | Returns a new set where all the elements are present in both sets     |
| difference    | Returns a new set of elements that are only in the initial set.       |
| copy          | Copy this original set into a new set.                                |
### Exercise: implementing a `pickRandom` method.

- In a set, the elements are unordered.

- When we pick an element from a set, we pick it at random.

- Let's assume an array implementation of set.

- Write out an algorithm for returning a random element within a set collection.

```java
public T pickRandom() {
	// Create a random object if there is not a class one
	Random rand = new Random();
	
	// Depending on how our set in implemented this will
	// differ, however I will assume that we are just using
	// an array.
	int randomIndex = rand.nextInt(this.size);
	
	return this.underlyingArray[randomIndex];
}
```

### When should a Set be used.

One example of using set...

...to model a game of bingo.

### Case Study: Bingo

- Each player has a bingo card with numeric values associated with the letters B-I-N-G-O

- Letter / number combinations (printed on bingo balls) are picked at random, which the player marks on their card if possible.

- The first player to get five squared in a row on their bingo card wins.

### Modelling the B-I-N-G-O board.

![[Pasted image 20241108163725.png]]

We assume that each player has been given a bingo card, and would tick off the matching number on their bingo card as the number of each randomly picked bingo ball announced by the host.

- We create an object of class `BingoBall` to represent one letter / number combination.

- The main program:

	1. creates the balls.
	
	2. stores them in a set.
	 
	3. draws one ball from the set and announce its number, and 
	   
	4. repeat step 3 N - 1 times (where n is the number of balls required for each game).

### `Bingo` and `BingoBall`

UML description of the `Bingo` and `BingoBall` classes

![[Pasted image 20241108165500.png]]

### Class `BingoBall`

```java
public class BingoBall {
	private char letter;
	private int number;
	
	/**
	 * Set up this bingo ball with the specified number and
	 * appropriate letter.
	 */
	public BingoBall(int num) {
		number = num;
		
		if(num <= 15) {
			letter = 'B';
		}
		else if(num <= 30) {
			letter = 'I';	
		}
		else if(num <= 45) {
			letter = 'N';	
		}
		else if(num <= 60) {
			letter = 'G';	
		}
		else {
			letter = 'O';
		}
	}
	
	/*
	 * Returns a string representation of this Bingo ball`
	 */
	public String toString() {
		return (letter + ": " + number);
	}
}
```

### Class `Bingo`

```java
import snaith.ArraySet;

public class Bingo {
	/*
	 * Returns a string representation of this Bingo ball`
	 */
	public static void main(String[] args) {
		final int NUM_BALLS = 75;
		final int NUM_PULLS = 10;
		// a set collection for holding all bingo balls
		ArraySet<BingoBall> bingoSet = new ArraySet<BingoBall>();
		BingoBall ball;
		
		for(int num = 1; num <= NUM_BALLS; num++) {
			ball = new BingoBall(num);
			bingoSet.add(ball);
		}
		System.out.println("Size: " + bingoSet.size() + "\n");
		// Pick 10 bingo balls from the set one by one.
		for(int num = 1; num <= NUM_PULLS; num++) {
			// Remove a random bingo ball and print the val 
			ball = bingoSet.removeRandom();
			System.out.println(ball);	
		}
	}
}
```

### When else to use a set?

- Names in a hat.

- Finding duplicated.

### Set ADTs in JCF

The Java Collections Framework (JCF) includes various interfaces and classes for modelling a set collection:

- `java.util.Set` - Models a typical set collection
  Elements in the set may or may not be ordered.

- `java.util.SortedSet` - A set whose elements are sorted.

- `java.set.NavigableSet` - A `SortedSet` extended with navigation methods reporting closest matches for given search targets.

### Some Set Implementation in JCF

- `java.util.AbstractSet` - Skeletal `Set` implementation.

- `java.util.HashSet` - Hash table implementation of interface `Set`

- `java.util.TreeSet` - Elements in `TreeSet` are sorted.

- `java.util.LinkedHashSet` - Linked list and hash table implementation of interface `Set`
	
	- An insertion-sorted `Set` implementation that runs nearly as fast as `HashSet`.
	
	- Iteration over a `LinkedHashSet` is likely to be faster than a `HashSet`:
		
		- Iteration over a `LinkedHashSet` required time proportional to the size of the set, regardless of its capacity.
		
		- Iteration over a `HashSet` required time proportional to its capacity

### `LinkedHashSet`: an illustration

![[Pasted image 20241108171831.png]]

### `java.util.Set` Methods

- `add`: Adds the given element to this set if it is not already present.

- `addAll`: Performs set union and keeps the result in this set.

- `contains`: Checks if the given element is in this set.

- `containsAll`: Checks if this set contains all of this element in the given collection.

- `remove`: Removes the specified element from this set if it is present.

- `removeAll`: Removes from this set all of its elements that contained in the specified collection, i.e. set difference.

- `retainAll`: Perform set intersection and keeps the result in this set.

- `clear`: Removes all of the elements from this set.

- `equals`: Compares the specified object with this set for equality

- `isEmpty`: Checks if this set contains no elements.

- `size`: Returns the number of elements in this set.

- `iteration`: Returns an iterator over the elements in this set.

- NO `isSubset`, `removeRandom`, `pickRandom`, `...`

### Using `java.util.Set`

- Lab 3 used three different implementations of `java.util.Set` to model a `MagicalBag`:

	- `java.util.HashSet`.
	
	- `java.util.LinkedHashSet` and
	
	- `java.util.TreeSet`.

- The use of each of these implementation in Lab 3 is pretty similar.

### Using `java.util.TreeSet`

- Constructing a `MagicalBag6` object:

```java
public MagicalBag6() {
	contents = new TreeSet<>();
}
```

- Adding an item to the bag:

```java
public void add(T item) {
	contents.add(item);
}
```

- `TreeSet` stores elements in a self-balancing binary search tree, which supports O(log n) data retrieval.

- None of the implementation of set in the JCF provide a "remove random" facility.

### Removing a Random Element from a `TreeSet`

```java
	public T remove() {
		if(contents.isEmpty()) {
			throw new EmptyMagicalBagException();
		}
		T item = null;
		
		int index = randomiser.nextInt(size());
		
		int count = 0;
		for(T element : contents) {
			if(count == index) {
				item = element;
				break;
			}
			count++;
		}
		
		if(item != null) {
			contents.remove(item);
		}
		return item;
	}
```

### Using `HashSet` and `LinkedHashSet`

- Hash Tables are very time efficient => executes in O(1) time.

- A hash table that is full reduces its efficiency significantly and will need dynamic resizing to restore its efficiency.

	- Try to avoid the need for dynamic resizing by specifying a sufficiently large initial capacity.
	
	- Constructing a `MagicalBag4` object:
	
```java
public MagicalBag4() {
	contents = new HashSet<>(WordPicker.MAX_BAG_CAPACITY * 1.5);	
}
```

- Constructing a MagicalBag5 object:

```java
public MagicalBag5() {
	contents = new LinkedHashSet<>(WordPicker.MAX_BAG_CAPACITY * 1.5);
}
```

