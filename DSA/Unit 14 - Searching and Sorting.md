### Unit Objectives

- Learn about how various sorting and searching algorithms work.
- Analyse the efficiency of each algorithm.
- Compare the efficiency of different algorithms.

### The `Comparable` Interface (Recap)

- When conducting sort or search, we may need to perform comparison on our data.
- We may need to define the natural ordering of our data by making the underlying class implement the `Comparable` interface allows its objects to be sorted.
- Interface `Comparable` has one method `compareTo` which returns:
	- `< 0`: if this object should _precede_ the given object `obj`.
	- `= 0`: if this object is ordered the same as the given object `obj`.
	- `< 0`: if this object should _come after_ the given object `obj`.

### The `Comparable` Interface in Action

```java
public class Employee implements Comparable<Employee> {
	private String name;
	private int years;

	public int compareTo(Employee another) {
		int result;

		if(this.years == another.getYears()) {
			// If they are of the same age, compare the names.
			result = this.name.compareTo(another.getName());
		}
		else {
			result = this.years - another.getYears();
		}

		return result;
	}

	// Other method definitions omitted...

}
```

### Class `SortingAndSearching`

- We define a class `SortingAndSearching` to hold the implementations of our sorting and searching algorithms.
- All sorting algorithms and some search algorithms work on `Comparable` objects only.

```java
public class SortingAndSearching<T extends Comparable<T>> {

	// Fields and details omitted...

}
```

### Search

- __Search__ is the process of finding a target element among a group of items (the _search pool_), or determining that it is not there.
- This requires repetitively _comparing_ the target to candidates in the search pool
- An _efficient_ sort performs as few comparisons as possible.
- The _size_ of the search pool defines the size of the problem.

### Linear Search

- A __Linear Search__ sequentially examines each item in the __Search Pool__.

![[Pasted image 20241215110958.png]]

- If the search pool is _sorted_, this process _finished_ when either:
	- The target is found, or
	- An item is found that is larger than the target (all later items will also be target and so the target is no present)
- If the search pool is _unsorted_, the search continues until:
	- The target is found, or
	- The end of the search pool was reached.

### The method `LinearSearch`

```java
public int linearSearch(T[] data, int min, int max, T target) {
	int index = min;
	int comp; // the result of the comparison

	while(index <= max) {
		comp = target.compareTo(data[index]);
		if(comp == 0)
			return index;
		else if (comp < 0)
			return -(index - 1);
		else
			index++;
	}
	return -index-1;
}
```

### Binary Search

- With a _sorted_ search pool, we begin with the comparisons in the _middle_
	- If we are __very__ lucky, the middle items is what we need.
	- If not, we at least know that it is in one half or the other; the size of the search pool has been _halved_ in one comparison.
- We can then _jump_ to the middle of that half, and continue similarly.

![[Pasted image 20241215111838.png]]

For this method to work _efficiently_, the data needs to be sorted in an array, so that we can access the 'middle' elements in __O(1)__ time.

### Binary Search: Example

- Find the number `29` in the following _sorted_ list of numbers:

					8, 15, 22, 29, 36, 54, 55, 61, 70, 73, 88

- Compare the target to the middle value `54`
- We now know that if 29 is in the list, it is in the _front half_ of the list.
- With one comparison, we have eliminated _half_ of the data.
- Then compare to `22`, eliminating another _quarter_ of the data.
- What is left is `29` and `36` and there is no element between them. We simply try one and then the other, depending on the implementation of our search.

### The method `binarySearch`

```java
public int binarySearch(T[] data, int min, int max, T target) {
	int midpoint = (min + max) / 2;
	int comp = target.compareTo(data[midpoint]);

	if(comp == 0) 
		return midpoint;
	else if(comp < 0) {
		if(min <= midpoint - 1)
			return binarySearch(data, min, midpoint - 1, target);
		else
			return -1;
	}
	else {
		if(midpoint + 1 <= max)
			return binarySearch(data, midpoint + 1, max, target);
		else
			return -1;
	}
}
```

### Analysis of Binary Search

Suppose we need to determine if a given element is _not_ in a collection which contains 50 _sorted_ elements using __binary search__.

1. Estimate the size of the search pool at _each_ step of the searching process.
2. Up to 6 comparisons are required to determine the result of the search.
3. How does this number relate to the size of the collection?

![[Pasted image 20241215112819.png]]

4. This, the time efficiency is __O(log2n)__.

### Comparing Search Algorithms

- On average, a __linear search__ would examine `n/2` elements _before_ finding the target and deciding it is not present.
	- Therefore, a linear search is __O(n)__.
- The _worst_ case for a binary search is __log2(n)__ comparisons.
- A __Binary Search__ is a _logarithmic_ algorithm and has a time complexity of __O(log2n)__.
- Thus, for large n, a __Binary Search__ is much _faster_ then a linear search.

Keep in mind that, to perform __Binary Search__, the search pool _must_ be sorted.

### Sorting

- _Sorting_ is the process of arranging a group of items into a _defined_ order.
- There exist many sorting algorithms, e.g:
	- _Sequential Sorts_ require approximately `n^2` comparisons to sort `n` elements.
	- _Logarithmic Sorts_ typically require `n * log2(n)` comparisons to sort `n` elements.
- To maximise _space efficiency_, sorting may be conducted in an _'in-place'_ manner.
	- The sorting process is conducted in the _same_ data structure as the _unsorted data_.
	- No need to create a _new_ data structure to keep the _temporary_ results.

### Straight Insertion Sort

__Insertion Sort__ orders a list of values by _repetitively inserting_ a particular value into a _sorted subset_ of the list.

![[Pasted image 20241215113624.png]]

### Binary Insertion Sort

Recall that __Insertion Sort__ orders a list of values by _repetitively inserting_ a particular value into a __sorted subset__ of the list...

- For _arrays_, __when inserting an item into the sorted subset of the list,__ use _binary search_ rather than linear search to find the correct place to insert the item.
	- Recall that _linear search_ is __O(n)__ and _binary search_ is __O(logn)__.
- Such kind of insertion sort is known as __Binary Insertion Sort__
- Due to the reduced number of comparison during item insertion. __Binary Insertion Sort__ is more efficient than __Straight Insertion Sort__

### Selection Sort

__Selection Sort__ orders a list of values by repetitively putting a particular value (e.g. the 'smallest' one) into its _final_ position.

![[Pasted image 20241215114046.png]]

### Comparing Sorts

![[Pasted image 20241215114204.png]]

### Quick Sort

- __Quick Sort__ orders a list of values by _splitting_ the list into two partitions around _one_ element, then sorting each partition.
- More specifically:
	- Choose _one_ element in the list to be the _splitting element_
		- _For simplicity, we will use the first element in the partition as the splitting element for the next stage._
	- Organise the elements so that all elements less than the splitting element are to the left and all greater are to the right.
	- Apply the quick sort algorithm (_recursively_) to _both_ partitions.

### Illustration of Quick Sort Processing

![[Pasted image 20241215114449.png]]

### Quick Sort

- We will divide the work into _two_ methods:
	- `quickSort`: performs the recursive algorithm.
	- `findPartition`: rearranges the elements into _two_ partitions.
- We can select _any_ one element as the splitting element.

### The method `quickSort`

```java
public static <T extends Comparable<T>> void quickSort(T[] data, int min, int max) {
	int indexOfPartition;

	if(max > min) {
		// Create paritions
		indexOfPartition = findPartition(data, min, max);

		// Sort the left side
		quickSort(data, min, indexOfPartition - 1);

		// Sort the right side
		quickSort(data, indexOfPartition + 1, max);
	}
}

private static <T extends Comparable<T>> int findPartition(T[] data, int min, int max) {
	int left, right;
	T temp, split;

	// Use the first element as the splitting value
	split = data[min];

	left = min;
	right = max;

	while(left < right) {
		// Search for an element that should follow split
		while(data[left].compareTo(split) <= 0 && left < right) {
			left++;
		}
		while(data[right].compareTo(split) > 0) {
			right++;
		}
		if(left < right) {
			temp = data[left];
			data[left] = data[right];
			data[right] = temp;
		}
	}
	// Swap splitting element and element with index right
	data[min] = data[right];
	data[right] = split;
	return right;
}
```

### Analysis of Quick Sort

![[Pasted image 20241215120014.png]]

When `n = 7`, we need:
- 3 layers of `findPartition` (i.e. log2(7)), and
- Each later of `findPartition` requires 7 comparisons.

- Executes in _log-linear_ time, i.e. __O(nlog2n)__.

### Efficiency of `quickSort`

- However, our version of __quick sort__ has an __O(n^2)__ _worst case_ behaviour which, unfortunately, occurs quite commonly in practice: namely when the data is already _sorted_ or _sorted in reverse order_ (or nearly so)!
	- Then at each state one of the partitions is empty and the other one has a size only one less than the previous partition.