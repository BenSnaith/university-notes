### Unit Objects

- Learn about when to use map

- Explore some concrete implementations of map in the JCF.

### The Map ADT

Each key is mapped to one value, sometimes referred to as a dictionary, associative array and lookup table.

- Typical operations include

	- add: Associate a new key with a new value.
	  
	- reassign: Associate an existing key in the map with a new value.
	  
	- remove: Remove a key with its associated value from the key set in the map.
	  
	- lookup: Find the value (if any) that is associated with key.

### When would maps be useful?

- to model the contents of a dictionary.

- to model the contents of a phone book.

- to provide various indexing for a table of database records.

### Modelling dictionary contents using Map

Consider the data in a dictionary entry, e.g.

| Word (Key) | Definition (Value)                          |
| ---------- | ------------------------------------------- |
| Duck       | A bird that lives by water, has webbed feet |
### Modelling contents of a phone book

Consider the following data in a phone book entry, e.g.:

Aston University

The Aston Triangle, B4 7ET

Tel: 0121 503 8563

Website

### Indexing database records

Consider the following Supplier table:

| S#  | SNAME | STATUS | CITY   |
| --- | ----- | ------ | ------ |
| S1  | Smith | 20     | London |
| S2  | Jones | 10     | Paris  |
| S3  | Blake | 30     | Paris  |
| S4  | Clark | 20     | London |
| S5  | Adams | 30     | Athens |

What fields should class `Supplier` have?

```java
public class Supplier {
	private String id;
	private String name;
	private int status;
	private String city;
	
	// other details omitted
}
```

With the following supplier table:

| S#  | SNAME | STATUS | CITY   |
| --- | ----- | ------ | ------ |
| S1  | Smith | 20     | London |
| S2  | Jones | 10     | Paris  |
| S3  | Blake | 30     | Paris  |
| S4  | Clark | 20     | London |
| S5  | Adams | 30     | Athens |

How to model the records in a supplier table such as the below to facilitate efficient search over the supplier's:

1. name (SNAME), or

2. location (CITY)

=> A means to facilitate search is by indexing data.

### Indexing database records

We will need two maps...

- What would be the key and value?

- How to model the required indexing in Java?

### Potential Implementations of `Map`

- What sort of structure does each element in a map have?

- Which implementation of map is more efficient?

	- array
	  
	- linked list, i.e. a linear linked structure
	  
	- tree, i.e. hierarchical linked structure
	  
	- hash table

### The `Map` interface in JCF

- The `java.util` package includes the interface `Map<K, V>`

- A map is a mapping from a finite set of keys to values.

- Each key is mapped to a single value.

- Given a key, one cam look up the corresponding value from a map

- New key-value pairs can be added to a map.

- Existing key-value pairs can be removed from the map.

### Some Methods in the `Map` interface in JCF

The main methods defined in the `Map` interface are:

- `V get(Object key)`
	- Returns the value to which the specified key is mapped.

- `V put(K key, V value)`
	- Associates the specified value with the specified key (reassign)
	- If the key is not yet in the map, add a new key-value mapping

- `V remove(Object key)`
	- Removes the mapping for a key. (remove)

### Concrete Implementation of `Map` in JCF 

- The main implementations of `Map<K, V>` are:

	- `HashMap<K, V>` - hash table implementation of map.
		- Used when the order of the data in the map is irrelevant, e.g. for storing data in an electronic dictionary.

	- `ConcurrentHashMap<K, V>` - a thread-safe, hash table implementation of map that supports concurrent operations

	 - `TreeMap<K, V>` - an ordered map, ordered by the natural order of key.
		 - Used when the data in the map need to be ordered, e.g. for storing data in a dictionary for printing a paper dictionary

```java
private TreeMap<String, LexicalUnit> dictionary;
```

### How to Iterate over `Map`?

- `java.util.Map<K, V>` does not extend the interface `Iterable`
	- Hence, an enhanced-for statement cannot be used to iterate over the contents of a `Map` object.

- `Map<K, V>` provides convenient methods for obtaining the contents of the map:

	- `Set<K> keySet():`
	  Returns a set of the keys contained in this map.

	 - `Set<Map.Entry<K, V>> entrySet():`
	   Returns a set of key-to-value mappings contained in this map.

	- `Collection<V> values():`
	  Returns a collection of the values contained in this map.
	  => The collection can contain the same object more than once. Why?

An enhanced-for statement can be used to iterate through the returned data: `Set` and `Collection`.

### Iterating over `Map`: An Example

```java
public void results() {
	System.out.println(raffle.title() + "\nThe Winners are...");
	
	Map<Prize, Ticket> winners = raffle.luckDraw();
	
	for(Map.Entry<Prize, Ticket> map : winners.entrySet()) {
		Prize prize = map.getKey();
		Ticket winner = map.getValue();
		
		System.out.println(prize.toString() + " goes to " + winner.buyer());
	}
	System.out.println("Many Congratulations!!");
}
```