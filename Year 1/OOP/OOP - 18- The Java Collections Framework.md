## Programs need to deal with groups of objects

So far you have used…

- Arrays for sequences of a known number of objects
- ArrayLists for sequences of unknown numbers of objects
- HashMap to store and look up objects by key (like a dictionary)

ArrayList and HashMap are just the surface

- Programs need to order their data all of the time
- Most modern languages include a good set of data structures as part of their standard libraries
- For Java, we have the Java Collections Framework as a base: ArrayList and HashMap are just part of it

## Structure of the Java Collections Framework

The JCF provides three kinds of things:

- Interfaces that describe the various abstract data types: the abstract idea of an ordered list of things (List), a set of things (Set), a key-value mapping (Map) and so on.
- Implementations for those interfaces, like ArrayList (implements List using Arrays) or HashMap (implements Map using a hash table)
- Algorithms for common operations, like sorting (remember `Collections.sort` and `Comparable` last term?)

![[Untitled 45.png|Untitled 45.png]]

These are the main interfaces we will look at, we will go over each of these later.

![[Untitled 1 25.png|Untitled 1 25.png]]

This is the general structure of the JCF

## What is a Collection?

- Collection is the most general interface for a simple “group” of objects that you can loop over and change
- You can `add()` and `remove()` single objects: these methods will return true if this caused a change
- You can `addAll()` or `removeAll()` the objects in another collection, or `retainAll()` the objects in your collection that also exist in the other collection
- You can `clear()` the collection to leave it empty, check if it `isEmpty()` or retrieve its `size()` in number of elements
- Finally, you can check if the collection `contains()` a certain element or not

![[Untitled 2 25.png|Untitled 2 25.png]]

## Example: basic use of Collection

```Java
// 1. ArrayList is-a collection
// 2. When declaring + setting, use <> to avoid repetiton
Collection<String> c = new ArrayList<>();

System.out.println("Size(): " + c.size()); // 0
System.out.println("isEmpty(): " + c.isEmpty()); // true
System.out.println("contains 'A': " + c.contains('A')); // false

System.out.println("Adding A, B, and C");
c.add("A");
c.add("B");
c.add("C");

System.out.println("Size(): " + c.size()); // 3
System.out.println("isEmpty(): " + c.isEmpty()); // false
System.out.println("contains 'A': " + c.contains('A')); // true

System.out.println("Clearing the collection");
c.clear();
System.out.println("isEmpty(): " + c.isEmpty()); // true
```

- `addAll()` adds all of the elements in a Collection to another Collection
- `removeAll()` removes all the elements in a Collection to another Collection
- `retainAll()` only keeps the elements in a Collection that are in another Collection

## What is a List?

![[Untitled 3 23.png|Untitled 3 23.png]]

- List is a particular kind of Collection: an ordered sequence of elements
- Elements now have an index, starting at 0
- Now you can `add()` and `remove()` elements at a specific index `(i)`
- You can also `get()` or `set()` (i.e. replace) the element at a specific index
- You can find the index at a particular object is in by using `indexOf()` : if it is not part of the list, you will get back -1

## Implementations of List

ArrayList: uses arrays

- Uses arrays internally: starts with a smaller array, and when the array is full, creates a bigger one and moves everything to it
- Very fast at accessing elements by index
- Slow at adding/removing things at the beginning/middle (requires loop)

Linked List

- Uses linked lists (imagine a string of beads, where each bead is an element)
- Slow at accessing elements by index
- Fast at adding/removing things at the beginning/middle (add/cut a bead)

## Example: using List

```Java
// Here is the only place mentioning an implementation
List<Integer> l = new LinkedList<>();

System.out.println("Adding 5 at the end and -1 at the beginning");
l.add(5);      // adds at the end (from Collection)
l.add(0, -1);  // adds at the beginning (from List)
System.out.println("Second element is " + l.get(1)); // 5

// For finding elements
System.out.println("indexOf(5) = " + l.indexOf(5)); // 1
System.out.println("indexOf(3) = " + l.indexOf(3)); // -1

// For replacing elements in place
l.set(1, 3);
System.out.println("After setting index 1 to 3: " + l); // [-1, 3]

// Removes by position
l.remove(0);
System.out.println("After removing element at index 0: " + l); // [3]
```

## What is a Set?

![[Untitled 4 21.png|Untitled 4 21.png]]

- A Set is a kind of Collection which does not keep duplicate elements (exactly like sets in maths)
- The actual methods are the same as Collection otherwise
- Set operations match as follows:
    - Union (A ∪ B): `a.addAll(b)`
    - Intersection (A ∩ B): `a.retainAll(b)`
    - Difference (A - B): `a.removeAll(b)`
    - Contains (e ∈ A): `a.contains(e)`
    - Subset (A ⊆ B): `a.containsAll(b)`

## Implementations of Set

HashSet

- Turns elements into numbers (hashes them) to quickly find them: very fast!
- Elements not stored in a predictable order (loops will seem “strange”)

TreeSet

- Orders elements according to their “natural order” (elements must implement the Comparable interface)
- Slower than HashSet (you pay for that ordering — no free lunch!)

## Example: HashSet and TreeSet

```Java
Set<String> h = new HashSet<>();
h.add("quick");
h.add("brown");
h.add("fox");

// We can quickly create any collection
// from the elements of another collection
Set<String> t = new TreeSet<>(h); // remember: tree = natural order

// Compare the order of the results!
for (String s : h) System.out.println("h: " + s); // quick, brown, fox
for (String s : t) System.out.println("h: " + s); // brown, fox, quick
```

## What is a Map?

![[Untitled 5 21.png|Untitled 5 21.png]]

- A Map is NOT a Collection!
- It maintains a key-value lookup (like a dictionary): you `put()`, `get()` and `remove()` values by a certain key
- Not that put() and remove() will return the value that was previously associated to the key, or null if there wasn’t any
- You can check if it `isEmpty()`, measure its `size()` in number of elements (keys), and `clear()` it to leave it empty
- A SortedMap is a kind of Map that keeps its keys in a predictable order (usually based on Comparable): you can do things like getting the `firstKey()` based on that order

## Implementations of Map

HashMap

- Similarly to HashSet, it turns keys into numbers to quickly find them
- Very fast at everything, but keys are not in any predictable order

TreeMap

- Like TreeSet, it orders keys according to their natural order (Comparable)
- Slower than HashSet

## Example: using HashMap

```Java
Map<String, Integer> m = new HashMap<>();

System.out.println("m.isEmpty(): " + m.isEmpty()); // true
System.out.println("m.size(): " + m.size()); // 0
System.out.println("m.get('word'): " + m.get("work")); // null

System.out.println("Putting key 'word' with value 5");
m.put("word", 5);
System.out.println("m.get('word'): " + m.get("word")); // 5
System.out.println("m.isEmpty(): " + m.isEmpty()); // false
System.out.println("m.size(): " + m.size()); // 1

System.out.println("Replacing key 'word' with value 3: old value was " 
										+ m.put("word", 3));

System.out.println("Removing key 'word'");
m.remove("word");
System.out.println("m.isEmpty(): " + m.isEmpty()); // true
System.out.println("m.size(): " + m.size()); // 0
```

## Collection views over a Map

- Maps provide three ways to view its elements as Collections:
    - `values()` gives you a Collection of all the values (e.g. dictionary definitions)
    - `keySet()` gives you a Set of all the keys (e.g. words in a dictionary)
    - `entrySet()` gives you a Set of all the entries (key-value pairs): this is the most efficient way if you need both in a loop
- These views support element removal: if you `remove()` a key from the result of `keySet()`, you will be removing the key in the Map you got it from

## Example: Collection views

```Java
Map<String, String> eng2spa = new TreeMap<>(); // tree = natural
eng2spa.put("red", "rojo");
eng2spa.put("green", "verda");
eng2spa.put("blue", "azul");

for (String s : eng2spa.keySet()) {
	System.out.println("English: " + s); // blue, green, red
}
for (String s : eng2spa.values()) {
	System.out.println("Spanish: " + s); // azul, verda, rojo
}
for (Map.entry<String, String> e : eng2spa.entrySet()) {
	System.out.println(
			"Key: " + e.getKey() + ", value: " + e.getValue()); 
}

Map<String, String> copy = new HashMap<>(eng2spa);
System.out.println("Keys in HashMap copy: " + copy.keySet()); // [red, green, blue]
```

## What is Iterable?

![[Untitled 6 17.png|Untitled 6 17.png]]

- Iterable is anything you can use in a “for each” loop (like l here):

```Java
for (Element e : l) { ... }
```

- That gets translated by Java into:

```Java
Iterator<Element> it = l.iterator();
while(it.hasNext()) {
	Element e = it.next();
	...
}
```

- An Iterator represents a specific traversal over the elements of a data structure
- We can ask if there is a next element with `hasNext()`, get it with `next()`, and remove it afterwards with `remove()`
- Every Collection is Iterable

## Working with Iterator: Parallel Traversals

```Java
List<String> 11 = new ArrayList<>();
List<Integer> 12 = new ArrayList<>();

11.add("X");
11.add("Y");
11.add("Z");

12.add(10);
12.add(20);

Iterator<String> it1 = 11.iterator();
Iterator<Integer> it2 = 12.iterator();
while(it1.hasNext() && it2.hasNext()) {
	System.out.println("11: " + it1.next());
	System.out.println("12: " + it2.next());
}

// Output: x, 10, y, 20
```

## Working with Iterator: Filtering collections (I)

- You are given some numbers, and you have to remove all the even ones without using a second list (to save memory)
- Your first attempt is with a `for (e:l)` loop:

```Java
List<Integer> 13 = new ArrayList<>();
13.add(0);
13.add(2);
13.add(3);
13.add(5);

int i = 0
for(int e : 13) {
	if(e % 2 == 0) 13.remove(i);
	i++;
}
```

Unfortunately, during a `for(e:l)` loop you cannot change `i`, so our program crashes

- Second attempt, with a `for(;;)` loop over indices:

```Java
List<Integer> 13 = new ArrayList<>();
13.add(0);
13.add(2);
13.add(3);
13.add(5);

for(int i = 0; i < 13.size(); i++) {
	if(13.get(i) % 2 == 0) 13.remove(i);
}
System.out.println(13);
```

No, this is incorrect

`[2, 3, 5]`

We should not increment `i` if we remove an element (that will shuffle everything to the left, so incrementing `i` would have use skip over the second element)

0[0] % 2 == 0, so this is removed

Now 2 is at index 0, but `i` is at 1, so 2 will never be evaluated

Lets fix this…

- Third attempt, being careful when incrementing:

```Java
List<Integer> 13 = new ArrayList<>();
13.add(0);
13.add(2);
13.add(3);
13.add(5);

for(int i = 0; i < 13.size();) {
	if(13.get(i) % 2 == 0) {
		13.remove(i);
	}
	else {
		i++;
	}
}
System.out.println(13);
```

This looks correct

`[3, 5]`

However this is needlessly complicated, the iterator is designed to solve this problem for us.

- Fourth attempt, this time with iterators:

```Java
List<Integer> 13 = new ArrayList<>();
13.add(0);
13.add(2);
13.add(3);
13.add(5);

for(Iterator<Integer> it = 13.iterator; it.hasNext();) {
	if(it.next() % 2 == 0) it.remove();
}
System.out.println(13);
```

This works and is much nicer to read and understand!

`[3, 5]`

The `remove()` method will remove what `next()` last returned, which works great for many use cases (like this one)

## Writing a function to count an object in a list

We just wrote this small program to count how many times an object appears in a list:

```Java
public static int countEquals(Object o, List<Object> l) {
	int count = 0;
	for(Object e : l) {
		if(o.equals(e)) count++;
	}
	return count;
}

public static void main(String[] args) {
	List<Object> l = new ArrayList<>();
	l.add(1);
	l.add("foo");
	l.add('c');
	System.out.println(countEquals(1, l));
}
```

It seems to work fine, let’s try it with other lists!

![[Untitled 7 16.png|Untitled 7 16.png]]

- Oops, that will not compile!
- Key detail: a `List<String>` is NOT a `List<Object>`
- You can add any Object to a `List<Object>`, and that is not true for a `List<String>`, which can only have `String`!
- If only we could tell Java our function works for `List` of type “anything” (generics lol)
- Turns out we can do that, using wildcards(”?”)
- `List<?>` really means “a List of anything”
- Note that when we loop through it, we can only get Objects from it (because all objects in Java inherit from Object)
- Wildcards and other similar features we will discuss in the rest of the lecture are generally known as Java generics: they allow you to create generic methods and classes that can work with a variety of types

```Java
public static void setAllOwned(boolean o, Iterable<Item> l) {
	for(Item e : l) e.setOwned(o);
}
public static void main(String[] args) {
	List<Item> l = new ArrayList<>();
	l.add(new CD());
	l.add(new Video());
	setAllOwned(true, l);
}
```

- We just wrote a function to mark several items as owned / not owned in one go: we even used Iterable interface for flexibility!
- However, this will not work with a `List<CD>`: while `List<CD>` is-an `Iterable<CD>` is-not-an `Iterable<Item>`
- An “Iterable of anything” (`Iterable<?>`) is not what we want: we want an “Iterable of Item or one of its subclasses”: this is an example of a bounded wildcard

```Java
public static void setAllOwned(boolean owned, Iterable<? extends Item> l) {
	for(Item e : l) e.setOwned(o);
}
```

- The right syntax would be Iterable<? extends Item>: this means “an Iterable of Item or one of its subclasses”
- This will work with `Iterable<Item>`, `Iterable<CD>` and `Iterable<Video>` just fine

## Writing a function to add a number range to a list

```Java
public static void range(int from, int to, List<Integer> l) {
	for(int i = from; i < to; i++) l.add(i);
}

public static void main(String[] args) {
	List<Integer> l = new ArrayList<>();
	range(0, 10, l);
	System.out.println(l);
}
```

- The above functions adds a range of numbers to a list
- Sadly, this only works on `List<Integer>`: it does not work on `List<Number>` or `List<Object>` (even though an `Integer` is-a `Number` and also is-an `Object`)
- If only there was a way to say “List of anything that is an Integer or one of its super classes” …

```Java
public static void range(int from, int to, List<? super Integer> l) {
	for(int i = from; i < to; i++) l.add(i);
}
```

- Turns out there is one: `List<? super Integer>`
- This means “List of anything that is an Integer or one of its super classes”
- Now the function will work with `List<Integer>`, `List<Number>` and `List<Object>`, as it should!

## Writing a function to increment a list

```Java
public static void incrementAll(List<Integer> l) {
	for(int i = 0; i < l.size(); i++) {
		l.get(i, l.get(i) + 1);
	}
}
```

- Can we generalise this one with wildcards / super / extends?
- Lets see:
    - We need the list to give us Integers, so we can increment them: that requires that the list if of Integers or its subclasses (if it had any!)
    - We need the list to accept Integers, so we can put the incremented numbers back into the list: that requires that the list is of Integers or its super classes
- The only thing that meets both requirements is plain `List<Integer>`: wildcards are not useful here!

## The get-put rule and the PECS mnemonic

- To summarise, extends / super for describing the desired type of element in a collection:
    - If you are going to get elements of type `Type` from a collection, use `? extends Type`
    - If you are going to put elements of type `Type` into a collection, use `? super Type`
    - If you are going to BOTH get AND put elements of type `Type` into a collection, just use `Type`
- The above is known as the get-put principle
- There is another similar mnemonic: PECS (Producer Extends, Consumer Super)
    - If the collection is producing elements (you are getting them from it), use `extends`
    - If the collection is consuming elements (you are putting them into it), use `super`

## Writing a function to reverse a list

```Java
public static void reverse(List<Integer> l) {
	final int lastPosition = l.size() - 1;
	for(int i = 0; i < l.size() / 2; i++) {
		// swap element at i with element at lastPosition - i
		Integer old = l.get(i);
		l.set(i, l.get(lastPosition - i));
		l.set(lastPosition - i, old);
	}
}
public static void main(String[] args) {
	List<Integer> l = new ArrayList<>();
	l.add(1);
	l.add(2);
	l.add(3);
	l.add(4);
	System.out.println(l);
	reverse(l);
	System.out.println(l);
}
```

This only works with `List<Integer>`: how do we generalise it?

We could copy and paste it every time we need a new version, but it seems wasteful (basically overloading it for every type)

- “?” won’t really help here, either: even if `l.get()` gives us an `Object, l.set()` won’t accept it
- If only there was a way to say “this function works for Lists of some type T I do not know about”

```Java
public static <T> void reverse(List<T> l) {
	final int lastPosition = l.size() - 1;
	for(int i = 0; i < l.size() / 2; i++) {
		// swap element at i with element at lastPosition - i
		T old = l.get(i);
		l.set(i, l.get(lastPosition - i));
		l.set(lastPosition - i, old);
	}
}
```

- Turns out there is one: by adding `<T>` before the return type, we tell Java that `T` is a type parameter
- You can then use `T` as a placeholder for a type in the return type, parameter types, and body of the function
- If somebody calls this function with `List<String>`, then `T` will just become a stand in for String and everything will work as if we copied and pasted the code into where `T` is
- Note: you can have multiple type parameters (separated by commas), and they can work with `extends` and `super` too

## Generic Types

We just wrote this class to hold a label / value pair that cannot change after we created it:

```Java
public class ImmutablePair {
	private final String label;
	private final Integer value;
	
	public ImmutablePair(String label, Integer value) {
		this.label = label;
		this.value = value;
	}
	
	public String getLabel() { return label; }
	public Integer getValue() { return value; }
}
```

A colleague wants something just like this, but with a Double as the value. We do not want to copy and paste all over the place: what to do?

Entire classes and interfaces can have type parameters

```Java
public class ImmutablePair<T, U> {
	private final T label;
	private final U value;
	
	public ImmutablePair(T label, U value) {
		this.label = label;
		this.value = value;
	}
	
	public T getLabel() { return label; }
	public U getValue() { return value; }
}
```

- We added the type parameters to the name of the class, and replaced String with T, and Integer with U
- Now we can just do `ImmutablePair<String, Double>`
- JCF is implemented this way: `List<T>, ArrayList<T> …`