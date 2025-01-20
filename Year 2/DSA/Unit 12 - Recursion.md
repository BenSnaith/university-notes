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

To analyse _recursive_ algorithms (similar to iterative algorithms...)

1. Work out the time efficiency (i.e. _order_) of the _method body_ excluding the _recursive call:_ O(1).
2. Multiply the result by the _order_ of the _recursion_ (the number of times the method calls itself): n x O(1)
3. Overall time complexity: O(n)

### The Towers of Hanoi

- The Towers of Hanoi is a puzzle made up of _three_ vertical pegs and several disks that slide onto the _pegs_.
- The disks are of _varying_ example, initially placed on one peg with the largest disk on the bottom and increasingly smaller disks on top.
- The goal is to move all of the disks from one peg to another following these rules.
	- Only _one_ disk can be moved at a time.
	- A disk cannot be placed on top of smaller disk.
	- All disks must be on a peg (unless in transport).

### The Towers of Hanoi Solution

- A solution to the Towers of Hanoi puzzle involving _three_ disks is shown below:

![[Pasted image 20241213114247.png]]

### The Towers of Hanoi Algorithm

- To move a stack of N disks from the original peg to the destination peg.

	1. Move the topmost N - 1 disk from the original peg to the extra peg. _recursive step_.
	2. Move the largest disk from the original peg to the destination peg.
	3. Move the N - 1 disks from the extra peg to the destination peg. _recursive step_.

- The _base case_ in the recursion occurs when a _'stack'_ contains only one disk.

### Java Code for Tower of Hanoi

```java
private void moveTower(int numDisks, int state, int end, int temp) {
	 if(numDisks == 1) {
		 moveOneDisk(start, end);
	 }
	else {
		moveTower(numDisks - 1, start, temp, end);
		moveOneDisk(start, end);
		moveTower(numDisks - 1, temp, end, start);
	}
}

private void moveOneDisk(int start, int end) {
	System.out.println("Move one disk from the start to the start to the end");
}
```

`numDisks = n` defines the `size` of the problem.

__Each `moveTower` call leads to _two_ more `moveTower` calls plus a move to `moveOneDisk`___

### Analysing Towers of Hanoi

How many `moveOneDisk(int, int)` calls are there for a 3-disk tower.

What is the worst case time complexity of `solve()`

__O(2^n)__

### Fibonacci Numbers

- The Tower of Hanoi is said to be doubly recursive as at each stage `MoveTower` calls itself _twice_.
- The Fibonacci sequence is this sequence of integers...
			1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144

- In which each number (except the first two) is the sum of two previous numbers in the sequence.
- A _doubly_ recursive definition of the nth Fibonacci number F(n):
			F(0) = 1
			F(1) = 1
			F(N) = F(N - 1) + F(N - 2) ... 1

### A Recursive Method for Fibonacci Numbers

- A doubly recursive method to calculate the nth Fibonacci number.

```java
public static int fib(int n) {
	if(n == 0 || n == 1) {
		return 1;
	} 
	else {
		return fib(n - 1) + fib(n - 2); // recursive case
	}
}
```

- All very elegant!
- But unfortunately very _inefficient_

e.g., To find out the 4th Fibonacci number, 9 steps are required (2^n-1 + 1 steps)

### An Iterative Method for Fibonacci Numbers

- An iterative solution has time complexity `O(n)` and is far superior

```java
public static int fib(int n) {
	if(n == 1 || n == 1)
		return 1;

	int f0 = 1; int f1 = 1; int result;
	for(int i = 2; i <= n; i++) {
		result = f0 + f1;
		f0 = f1;
		f1 = result;
	}
	return result;
}
```

- We should be careful about when to recursive methods.

### Recursion vs. Iteration 

- Every recursive solution has a corresponding _iterative_ solution.
	- An iteration may be more suitable than a recursion, e.g., when summing 1 to N or calculating factorials.
- Recursion has the _overhead_ of multiple methods invocations.

Each recursive call sets up a new __execution environment__, with new __parameters__ and new __local variables__.

...more storage space required.

- For some problems, however, recursive solutions are often _simpler_ and _more elegant_ than iterative solutions.
	- It is important to know _when_ recursion should be used.
	

