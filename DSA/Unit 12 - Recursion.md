### Unit Objectives

- Learn about fundamental ideas of recursion.
- Lean how to use recursion.
- Learn when to use recursion.

### Recursive Thinking

- __Recursion is a programming technique in which a method__
	1. _breaks down_ a problem into one or more _simpler_ problems of the same nature, and then.
	2. _calls itself_ to solve the simpler problem(s).	
- A definition of a concept is _recursive_ if it involves _references to the concept_ itself.
- A recursive definition defined objects in terms of _'previously defined' simpler_ objects of the class.

### An Example of a Recursive Definition

- A persons parents are:
	- _their parents_,
	- _their parents, parents_,
	- _their parents, parents, parents_,
	- _everyone_ else you get successively continuing this process until...
	- we reach _the ancestor with no parents_.
- We can therefore define a person's ancestors as:
	- _a person's parents_ (__non-recursive / base__ case), plus.
	- The parents of _any_ of _their parents_ (__recursive__ case).

### Recursive Thinking: an Exercise

- A list of numbers looks like this:
	24, 88, 40, 37
- Define a __list__ of numbers using _recursion_
	- What is the _base case_?
	(i.e., the basic, fundamental component of the list of numbers.)
	- What is the _recursive step_?
		(i.e., a definition which uses that concept that is being defined.)
- A __LIST__ can contain a number
	- What is the _recursive step_?
		- (i.e., a definition which uses the concept that is being defined.)
- A __LIST__ can also contain _a number comma __LIST___

### Tracing the recursive definition of a list

![[Pasted image 20241212220436.png]]

- __Base Case:__ A __LIST__ can contain _a number_.
- __Recursive Step:__ A __LIST__ can also contain _a number comma __LIST___ 

### Recursive Programming

- A method in Java can invoke _itself_.
- A _recursive method_ is a method that calls itself.
	- ...it _must_ handle _both_ the __base case__ and __recursive case__.
- Each call sets up a new _execution environment_, with new parameters and new local variables.
- In a recursive method, when a recursive method call _finishes_ its execution, the control returns to _the method that invoked it_.
	- _i.e., another earlier instance of itself..._

### Recursive Programming: Summing 1 to n

Consider the problem of computing the _sum_ of all the numbers between 1 and n...

- When `n = 1: 1`
- When `n = 2: 2 + 1`
- When `n = 3: 3 + 2 + 1`
- When `n = 4: 4 + 3 + 2 + 1`
	...
- With `n - 1: (n - 1) + (n - 2) + (n - 3) + ... + 4 + 3 + 2 + 1`
- With `n: n + (n - 1) + (n - 2) + (n - 3) + ... + 4 + 3 + 2 + 1`

The _sum_ of 1 to N is N plus the _sum_ of 1 to N - 1

### Recursive Programming: an Example

- Write down the __base case__ and the __recursive step__ for
	
- _Base Case:_
	- When N = 1, the sum is 1.
- __Recursive Step:__
	- Otherwise, the sum is N plus the sum of (N - 1).

```cpp
class Example
{
public:
	int sum(int n)
	{
		if(n == 1)
			return 1;
		else
			return sum(n - 1) + n;
	}
}
```

### Recursive calls to the `sum` method

![[Pasted image 20241212221920.png]]

### Recursive Programming: Exercise

N! (where N > 0) is defined as:
	1! = 1
	N! = N x (N - 1)!

Write the method `factorial` for computing the factorial N, given N, The header of this method should be:

```cpp
static long factorial(int n)
```

```cpp
class Example
{
public:
	static long factorial(int n)
	{
		if(n <= 0)
			return STATUS_ERROR; // or throw an exception
		if(n == 1)
			return 1;
		else 
			return n * factorial(n - 1);
	}
}
```

### Recursive Method

- A _recursive method_ is a method that calls itself.
	- ...it _must_ handle _both_ the __base case__ and the __recursive case__

		_What would happen otherwise?_

__The method will enter an infinite recursion and eventually lead to a stack overflow__

### Infinite Recursion

```cpp
class Example
{
public:
	static void printOnes()
	{
		std::cout << "1" << std::endl;
		printOnes();
	}
}
```

- This will result in an unending output of 1's until stack overflow and the program terminates.

```cpp
class Example
{
public:
	static void printOnes()
	{
		printOnes();
		std::cout << "1" << std::endl;
	}
}
```

- No output - stack overflow terminates the program, the calls can never be resolved.

### Avoiding Infinite Recursion

- A recursive definition _without_ a non-recursive part causes _infinite recursion_.

	..._similar to an __Infinite Loop___

- All recursive definitions must have a _non-recursive part_ to _terminate_ the recursion.
- A non-recursive part is known as a _base case_, or sometimes a _terminating condition_.

### Processing Linear Linked Structures using Recursion

- Recursive thinking can be applied in viewing a linear linked structure

- A __linear linked structure__ comprises:

The _base case_:

![[Pasted image 20241212230739.png]]

The _recursive step_:

![[Pasted image 20241212230929.png]]

- Methods `size`, `toString` & `copy` can be implemented using _recursion_:
	- _Base Case:_
	When the linked structure contains _only one node_.

	- _Recursive Step:_
		When the linked structure is made up of _one node_ followed by _another linked structure._

### Implementing `size` in `LinearNode` using Recursion

- Class __LinearNode__ models a linear linked structure.
	- One __LinearNode__ _object is linked with another_ __LinearNode__ _object which is linked with another and so on._
- Method `size` counts the number of nodes that are linked together:
	- _Base Case:_
	`size` of a __LinearNode__ object that is linked to `null` is 1.
	- __Recursive Step:__
		`size` of a __LinearNode__ object this is linked to another __LinearNode__ object (say, `tail`) is 1+(`size` of the __LinearNode__ object `tail`)

```cpp
template <typename T>
class LinearNode<T>
{
public:
	int size()
	{
		if(next == NULL)
		{
			return 1;
		}
		else 
		{
			return 1 + next.size();
		}
	}

	std::string toString()
	{
		if(next == NULL)
		{
			return element.toString();
		}
		else 
		{
			return element.toString() + ", " + next.toString();
		}
	}

	LinearNode<T> copy()
	{
		LinearNode<T> *current = new LinearNode<T>(elements);

		if(next != NULL)
		{
			current.next = next.copy();
		}
		return current;
	}
}
```

### Analysing Recursive Algorithms

Consider:

```cpp
class Example
{
public:
	static int sum(int n)
	{
		int result;
		if(n == 1)
			result = 1;
		else
			result = n + sum(n - 1);
		return result;
	}
}
```



