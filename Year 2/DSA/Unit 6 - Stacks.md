## Unit Objectives

- Learn about two-dimensional arrays
- Consider some uses of the ADT Stack.
- Consider implementations of stack as provided by the JavaSDK.

## What do we know so far?

- We can implement the ADT stack using an array, e.g. `ArrayStack`
- A time efficient unbounded stack can be implemented using linear linked nodes.
- Regardless of the implementation choice, operations in a bounded stack run in constant time, i.e. O(1)
- Stack is a linear, LIFO data structure, with opening at one end only.

## Using Stacks - run-time activation record

- A classic use of stacks is in the run-time environment of a programming language such as Java:
    - As method calls occur, the run-time system pushes an activation record onto the run-time stack.
    - When each method completes its execution, its activation record is popped off the stack.
    - The program control uses information in this record to return to the method that called.

## Using Stacks - run-time activation record: Illustration

```Java
public T draw() {
	if(!contents.isEmpty()) {
		Random randomiser = new Random();
		int which = randomiser.nextInt(contents.size());
		return contents.remove(which);
	}
	return null;
}
```

## Using Stacks

- One common application of a stack is to implement a multiple undo facility in an application:
    - When an operation is performed, a record of it is pushed onto a stack.
    - When the undo function is invoked, the most recent operation can be popped off the stack for undoing.
- Another suitable use of a stack is for keeping track of alternative in maze traversal or in other trial and error algorithms.

## Using Stacks: an example application

- A stack is for keeping track of alternative in maze traversal or in other trial and error algorithm.
- Questions to consider:
    - How to represent a maze
    - How to make a move within the maze
    - How to keep track of alternative paths

## Representing a Maze using a 2D Array

- A maze can be represented by a grid of 1’s and 0’s
    - 0: Wall
    - 1: Path
- The grid can be represented as a 2D array of int values in Java, i.e. `[]`
- A successful traversal of the maze means that a continuous path of 1’s is found from the start to the finish.

```Java
{{1, 1, 1, 0, 1, 1, 0, 0, 0, 1, 1, 1, 1},
 {1, 0, 0, 1, 1, 0, 1, 1, 1, 1, 0, 0, 1},
 {1, 0, 0, 1, 1, 0, 1, 1, 1, 1, 0, 0, 1}
 {1, 0, 0, 1, 1, 0, 1, 1, 1, 1, 0, 0, 1}
 {1, 0, 0, 1, 1, 0, 1, 1, 1, 1, 0, 0, 1}
 {1, 0, 0, 1, 1, 0, 1, 1, 1, 1, 0, 0, 1}
 {1, 0, 0, 1, 1, 0, 1, 1, 1, 1, 0, 0, 1}
 {1, 0, 0, 1, 1, 0, 1, 1, 1, 1, 0, 0, 1}}
```

## 2D Arrays

We can declare arrays of any type including array types, e.g. a 2D array (as an array of arrays):

```Java
int[][] b;
b = new int[3][4];

// creates an array with 10 rows and 10 columns
double[][] d = new double[10][10];
```

For 2D arrays, element access involves a little more address arithmetic, but can still be done in constant time.

## Visual Representation of a 2D Array

```Java
int[][] b;
b = new int[3][4]; // 3 rows and 4 columns
```

- A 2D array can be depicted as a block of memory with n rows and m colums:

![[image 35.png|image 35.png]]

- The individual elements of the array are accessed using the notation `b[i][j]` , where `i` specifies the row and `j` the column of the element.
- We can assign a value to an array cell using separate declarations and assignments, e.g.

```Java
int[][] c = new int[2][4];
c[0][0] = 5;
c[0][1] = 2;
c[0][2] = 1;
c[0][3] = 4;
c[1][0] = 6;
c[1][1] = 0;
c[1][2] = 3;
c[1][3] = 2;
```

- However, it is much neater to declare a 2D array and initialise its elements using 2D aggregate, e.g.

```Java
int[][] c = {{5, 2, 1, 4},
						 {6, 0, 3, 2}};
```

## Number of Rows and Columns

- The number of rows in a 2D array `b` can be accessed using the `final` field `length` of the array, e.g. `b.length` where `b` is a 2D array.
- This works because a 2D array is actually an array of arrays (or rows). Thus `b.length` is the number of rows
- To find the number of columns in an array we get the length of one of the array elements `b[0].length`

## 2D Array Processing

```Java
int[][] b = {{5, 2, 1, 4}, {6, 0, 3, 2}, {4, 2, 9, 7}};
```

- Use nested `for` loops to process all the elements of a 2D array:

```Java
for(int i = 0; i < b.length; i++) {
	for(int j = 0; j < b[i].length; j++) {
		b[i][j] *= 2;
	}
}
```

- We can, of course, use enhanced `for` loops:

```Java
for(int[] row : b) {
	for(int element : row) {
		element++;
	}
}
```

## Time Complexity of Array Operations

- Processing a whole 2D array with m rows and n columns will involve a nested loop, e.g.

```Java
Tree[][] forest = new Tree[5][6];

for(Tree[] row : forest) {
	for(Tree tree : row) {
		tree.makeVisible();
	}
}
```

Assuming the time complexity of processing one element is O(1), the time complexity of the whole process will be O(m x n).

- If rows ~ columns ~ n
    
    The time complexity of processing a 2D array is O(n^2).
    

## Traversing a Maze using a Stack

- We can traverse a maze using a trial-and-error approach, and use a stack to keep track of moves that have not yet been tried.
- We need to avoid trying paths that have already been followed.
    
    … to avoid going in circle within the maze!
    

Can you spot the circular path in the maze below?

![[image 1 10.png|image 1 10.png]]

- As we visit each valid location, we can change the 1 stored there to a 3 to mark it as visited.

![[image 2 9.png|image 2 9.png]]

- At each point of traversal, we can find ≤ 4 potential moves.
- Not all 4 possible moves need to be valid, e.g.
    - When we are at an edge of the grid.
    - When we are at the corner of the grid.
    - If some of the neighbouring positions are walls.
    - Or are positions that have already been visited.
- We keep track of the valid moves by pushing the end position of each valid move onto the stack.
- When we want to make a move, we pop one position from the stack and move to this position.
- This maze search enables the target location to be found, but the path is not recorded by the algorithm.

## Maze Traversal Application: A UML class diagram.

- The Java solution consists of 3 tailor-written classes plus an implementation of the interface `StackADT` namely `ArrayStack`.
- The class `LinkedStack` could be used instead.

![[image 3 9.png|image 3 9.png]]

## `Maze.java`

```Java
public class Maze {
	private final int TRIED = 3;
	private Position start = new Position(0, 0);
	private Position finish = new Position(8, 12);
	
	private int[][] grid =
	{{1, 1, 1, 0, 1, 1, 0, 0, 0, 1, 1, 1, 1},
	 {1, 0, 0, 1, 1, 0, 1, 1, 1, 1, 0, 0, 1},
	 {1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 0, 0},
	 {0, 0, 0, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1},
	 {1, 1, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1},
	 {1, 0, 1, 0, 0, 0, 0, 1, 1, 1, 0, 0, 1},
	 {1, 0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1},
	 {1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
	 {1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1}};
	 
	 StackADT<Position> stack = new ArrayStack<>(200);
}
```

## Methods `push_new_pos` and `valid`

```Java
private void push_new_pos(int x, int y) {
	if(valid(x, y)) {
		stack.push(new Position(x, y));
	}
}

private boolean valid(int row, int column) {
	boolean result = false;
	if(row >= 0 && row < grid.length
	&& column >= 0 && column < grid[row].length)
		if(grid[row][column] == 1)
			result = true;
	return result;
}
```

## Method `traverse`

```Java
public boolean traverse() {
	boolean done = false;
	Position pos;
	stack.push(start);
	while(!done) {
		pos = stack.pop();
		grid[pos.getX()][pos.getY()] = TRIED;
		if(pos.getX() == finish.getX() && pos.getY() == finish.getY()) {
			done = true;
		}
		else {
		 push_new_pos(pos.getX(), pos.getY()-1);
		 push_new_pos(pos.getX(), pos.getY()+1);
		 push_new_pos(pos.getX()-1, pos.getY());
		 push_new_pos(pos.getX()+1, pos.getY());
		}
	}
	return done;
}
```

## Class `MazeSearch`

```Java
public class MazeSearch {
	public static void main(String[] args) {
		Maze labyrinth = new Maze();
		
		System.out.println(labyrinth);
		
		if(labyrinth.traverse()) {
			System.out.println("The maze was successfully traversed!");
		}
		else {
			System.out.println("There is no possible path.");
		}
		System.out.println(labyrinth);
	}
}
```

## Class `java.util.Stack`

- J2SDK defines a Stack class with operations similar to `StackADT` .
- `java.util.Stack` extends `java.util.Vector` and hence has features that are inappropriate for a pure stack.

## Using Class `java.util.Stack` as a Pure Stack.

- One way to reuse `java.util.Stack` as a pure stack is by means of a wrapper class.
- e.g. a wrapper class named `PureStack` may have a single field contents of type `java.util.Stack` .
- Class `PureStack` can define methods that belong to a pure stack, e.g. `pop`, `push`, `peek` and `isEmpty`.
    - Each of these methods simply calls the respective in `java.util.Stack` to do the job.

## Stack in the Java Collections Framework (JCF)

- Class `java.util.Stack` is not part of the JCF.
- New facilities for stack were added to JCF since v1.6:
    - `java.util.Deque`: “double-ended queue” which supports element insertion and removal at both ends.
    - `java.util.ArrayDeque`: array implementation of an unbounded `Deque`
    - `java.util.LinkedBlockingQueue`: Linked nodes implementation of bounded `Deque`
    - `java.util.LinkedList`: Linked nodes implementation of unbounded `Deque`

## `java.util.Deque`

- Designed to be a multi-purpose collection. It is expected to be used as a stack or a queue.
- Stack methods are precisely equivalent to `Deque` methods as follows:

![[image 4 9.png|image 4 9.png]]

## Various Implementation of `java.util.Deque`

- `ArrayDeque` is likely to be faster than `Stack` when used as a stack.
- Classes `ArrayDeque`, `LinkedBlockingDeque` and `LinkedList` can be used as a stack because they implement the `Deque` interface.
    - The application programmer, however must stick to the stack-only methods, i.e. `addFirst`, `removeFirst` and `peekFirst`.
- `addFirst`, `removeFirst` and `peekFirst` in all implementations run in approximately constant time.
- The performance of `addFirst` in `ArrayDeque` is dependent on whether there is the need for capacity expansion.
- The performance of `addFirst` is `LinkedBlockingDeque` is subject to the time spent on blocking.