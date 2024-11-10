## Unit Objectives.

- Learn about how to analyse an algorithm.
- Learn the purpose of the Big-O notation.
- Learn about how the time implication of an algorithm as described by the Big-O notation

## Motivation

![[image 17.png|image 17.png]]

## The Need for Algorithm Analysis

- An aspect of software quality is the _efficient use of resources_, including the CPU.
- Algorithm analysis gives us a basis to compare the efficiency of algorithms. Examples:
    - Which data structure requires the shorter data retrieval time?
    - Which sorting algorithm is more efficient?
- To analyse an algorithm means to determine the _amount of resources_ (e.g. time and storage) that is necessary to execute it.
- Usually stated as a mathematical function relating to size of input to:
    - The number of steps _or_
    - The number of storage location requires to execute the algorithm.

## How to approach analysing an algorithm?

- Analysis is defined in general terms, based on:
    - The problem size
    - A key operation
- A growth function T(n) shows the relationship between the size of the problem (n) and the time it takes to solve the problem, e.g.
    
    $T(n) = n^2 + 3n + 100$﻿
    

The problem size is typically expressed in terms of the amount of data needed to be processed.

## Growth Function: An Example

- Consider a careless person washing the dishes
- Every time a dish is washed, all other previously washed and dried dishes are made wet again.
- A complete washing cycle for each dish by this careless person is:
    - The time for washing and drying it, plus
    - The time for drying all previously washed dished.

How much time does washing n dishes require?

- Let T(n) denote the time required for washing n dishes:
    
    ![[image 1 6.png|image 1 6.png]]
    
- Hence, the growth function for this dish-washing algorithm is:
    
    $T(n) = 15n^2 + 55n$﻿
    
- Consider another dish washing algorithm:
- Wash each dish and put it to the side.
- After washing 10 dishes, put the dishes in a rack to dry.
- Put away _all_ dishes once they have been washed and dried
- Assumptions:
    - To wash one dish takes 40 seconds.
    - To put 10 dishes on the rack for drying takes 5 seconds.
    - To put away all dished 50 seconds.

What is the _growth function_ for the second dish-washing algorithm?

![[image 2 6.png|image 2 6.png]]

- We can note the rate of increase in the execution time of an algorithm when the size of the problem (n) increases to determine the efficiency of the algorithm.

## Growth Functions

- It is usually not necessary to determine the exact growth function.
- The key issues to observe is the asymptotic complexity of the growth function, i.e.
    
    How would the result of the function grow as n increases?
    
- We determine the asymptotic complexity of a growth function by its dominant term.
    
    e.g. $15n^2$﻿ in our first dish-washing algorithm, i.e. $15n^2 + 55n$﻿
    
- The asymptotic complexity is referred to as the **order** (i.e. type) of the algorithm.
- We specify the order in **Big-O notation**:
    
    $O(1) < O(logn) < O(n) < O(nlogn) < O(n^2) < O(n^3) < O(2^n) < O(n!)$﻿
    

## Growth Functions & Asymptotic Complexity

Some growth functions and their asymptotic complexity.

|Growth Function|Order (in Big-O Notation)|
|---|---|
|$T(n) = 37$|O(1)|
|$T(n) = 24 * log(n) + 11$|O(logn)|
|$T(n) = 200 + 3n$|O(n)|
|$T(n) = 7n * log(n) + 4n + 1000$|O(nlogn)|
|$T(n) = 2n^2 + 5 + 49n$|O(n^2)|
|$T(n) = 3n + 6n^3 + 41$|O(n^3)|

To determine the order of a growth function, note its dominant term.

## Exercise: Identify dominant term in a growth function

In each growth function, which term will lead to a faster increase in the result when $n → inf$﻿

- $T(n) = 17$﻿
- $T(n) = 2n - 4$﻿
- $T(n) = 3n^2 + 5n - 2$﻿
- $T(n) = 4^n + 18n^2 + 3n$﻿

## Some common order of function

|Notation|Name|Example|
|---|---|---|
|O(1)|constant|Determining if a number is even or odd|
|O(logn)|logarithmic|Finding an item in a sorted list using binary search|
|O(n)|linear|Finding an item in an unsorted list|
|O(nlogn)|log-linear|Sorting a list with quick sort or heap sort|
|O(n^2)|quadratic|Sorting a list with insertion sort or selection sort|
|O(n^3)|cubic|Finding the best sum of subsequence over a sequence of numbers using brute force algorithm|
|O(2^n)|exponential|Solving the Tower of Hanoi problem; Guessing a password of length n bits|

## Asymptotic Complexity

- Asymptotic estimates are used because different (’reasonable’) implementations of the same algorithm may differ in efficiency, but only by a constant multiplicative factor.
- Such difference is regarded as relatively unimportant.
    
    e.g. a careless implementation of a binary search might take twice as long to execute as an efficient one. However both implementation have order O(log2n), whereas any implementation of a linear search will have order O(n)
    
- To distinguish between the relative efficiency of two algorithm in the same O class, use the tilde notation.

## The tilde notation

- We retain the constant multiplier in the dominant term. e.g. for the dish-washing example, we could write the time complexity as:
    
    $T(n) ~ 15n^2$﻿
    
- However, if we found a dishwasher who could dry a dish in 2- seconds, the time complexity would be:
    
    $T(n) ~10n^2$﻿
    
- Consider three naive sorting algorithms:
    - Selection
    - Straight Insertion
    - Bubble
- All have the time complexity O(n^2):

![[image 3 6.png|image 3 6.png]]

## Determining the time efficiency of source code

Which implementation is the most efficient?

```Java
public static int sum1(int n) {
	int result = 0;
	while (n > 0) {
		result += n;
		n--;
	}
	return result;
}

public static in sum2(int n) {
	int result;
	if(n == 1)
		result = 1;
	else
		result = n + sum2(n - 1);
	return result;
}

public static int sum3(int n) {
	return n * (1 + n) / 2;
}
```

## Determining the order of an algorithm

- Given a piece of source code, we can determine the order of the underlying algorithm, e.g.
    - O(1) typically corresponds to:
        - an assignment statement
        - a conditional statement
        - a return statement
    - O(n) typically corresponds to:
        - a simple loop
    - O(n^2) typically corresponds to:
        - a nested loop

## Analysing the order of an algorithm: Exercise

What is the asymptotic complexity of the following method?

```Java
public static int sum(int n) {
	 return n * (1 + n) / 2;
}
```

A: Constant Time.

## Analysing Loop Execution

- A loop executes a certain number of times (say n)
- The complexity of a loop is n times the complexity of the body on the loop.
- Example: the following loop executes n times and the body of the loop runs in _constant time_ (i.e. O(1))

```Java
for(int i = 0; i < n; i++) {
	x += 1;
}
```

- Hence, the asymptotic complexity is O(n).
- When loops are nested, the body of the outer loop includes the complexity of the inner loop.

## Analysing Loop Execution: Exercise

What is the asymptotic complexity of the following nested for-loop?

```Java
for(int i = 0; i < n; i++) {
	x = x + 1;
	for(int j = 0; j < n; j++) {
		y = y - 1;
	}
}
```

A: O(n^2)

What is the asymptotic complexity of the following method?

```Java
public static int maxSubsequenceSum(int[] a) {
  int maxSum = 0;
  int seqStart = 0;
  int seqEnd = 0;
  for(int i = 0; i < a.length; i++) {
	  for(int j = 0; j < a.length; j++) {
		  int thisSum = 0;
		  for(int k = i; k <= j; k++) {
			  this.sum += a[k];
		  }
		  if(thisSum > maxSum) {
			  maxSum = thisSum;
			  seqStart = i;
			  seqEnd = j;
		  }
	  }
  }
}
```

## Software Engineering and Data Structures

- As our software grows more complex, we need efficient algorithms to meet users’ needs.
- In some cases, using an efficient algorithm is more important than having a fast computer processor.
- As the volume of input increases, the time efficiency of an algorithm becomes more important
- Knowing the characteristics of different data structures, we can make appropriate engineering choice.

## Problem Size vs. Processor Speed

Increase in the amount of data being processed in each algorithm with a tenfold increase in processor speed.

![[image 4 6.png|image 4 6.png]]

With algorithms belonging to a higher O class, increase in processor speed has little effect on its processing speed.

## Average Case vs. Worst Case.

- Sometimes an algorithm may perform well on average, but for a few special input data sets (worst cases) it performs noticeably badly.
- e.g. The original quick sort algorithm has average time complexity O(nlogn), but a worst case time complexity of O(n^2).
    - The worst cases occur when the data is already sorted, or sorted in reverse order.
    - The algorithm also performs badly if only a few data items are our of order.
    - Although the chances that a random data set is already sorted (or almost sorted) is very small, the chances of such an occurrence in practice is quite high.