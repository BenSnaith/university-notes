- Support Video Notes
    
    # Further revision / understanding
    
      
    
    ## What is a tuple?
    
    The best way to explain what a tuple is, is to explain how it differs to a set.
    
    This is a set;
    
    1, 5, 3, 7, 6, 9
    
    But it is also a tuple;
    
    1, 5, 3, 7, 6, 9
    
      
    
    **So how do they differ?**
    
      
    
    A set must contain unique items;
    
    1, 5, 3, 7, 6, 9, 9 ← this is wrong
    
    whereas **a tuple is permitted duplicates**
    
    1, 5, 3, 7, 6, 9, 9 ← this is okay
    
      
    
    A set can be any order and it doesn’t matter;
    
    1, 5, 3, 7, 6, 9 = 1, 7, 9, 6, 3, 5
    
    **For a tuple the order does matter**
    
    1, 5, 3, 7, 6, 9 ¬= 1, 7, 9, 6, 3, 5
    
    These would be two separate tuples
    
      
    
    **Tuples cannot be infinite**
    
      
    
    **Tuples are written with ( )**
    
    (1, 7, 9, 6, 3, 5)
    
    Where sets are written with { }
    
    {1, 7, 9, 6, 3, 5}
    
      
    
    **Cartesian Products**
    
      
    
    How do we present a cartesian product;
    
    { (x, y) | x ∈ A ^ y ∈ B }
    
    the first part determines we will identify the product of x and y.
    
    the second part spells out what x and y actually are.
    
    **X is a member of set A**
    
    **Y is a member of set B**
    
    Let A be {Birmingham, Coventry, London}
    
    Let B be {Walking, Cycling, Driving}
    
      
    
    A x B = {
    
    (Birmingham, Walking) (Birmingham, Cycling) (Birmingham, Driving)
    
    (Coventry, Walking) (Coventry, Cycling) (Coventry, Driving)
    
    (London, Walking) (London, Cycling) (London, Driving)
    
    }
    
      
    
    B x A {
    
    (Walking, Birmingham) (Cycling, Birmingham (Driving, Birmingham
    
    (Walking, Coventry) (Cycling, Coventry) (Driving, Coventry)
    
    (Walking, London) (Cycling, London) (Driving, London)
    
    }
    
    **The order matters.**
    
      
    
    Let C be {2, 3, 5, 7} C x C {
    
    (2,2), (2,3), (2,5), (2,7),
    
    (3,2), (3,3), (3,5), (3,7),
    
    (5,2), (5,3), (5,5), (5,7),
    
    (7,2), (7,3), (7,5), (7,7)
    
    }
    
    **We don’t multiply the number**
    
      
    
    Whenever you try and find the product of a set and an empty set, the result is 0
    
    C x { } = 0
    
    like
    
    5 * 0 = 0
    
      
    
    ## Relations
    
    We are gonna show this through two apps, FlyDroid and iFly.
    
    Apps could allow for; Searches, Alerts, Hotels.
    
    In this case iFly allows for Searches and suggests Hotels
    
    FlyDroid allows for Searches and Alerts
    
      
    
    We could present Apps and Features in 2 sets
    
    A = {FlyDroid, iFly}
    
    B = {Searches, Alerts, Hotels}
    
      
    
    Then we could show the cartesian products of these sets
    
    {
    
    (FlyDroid, Searches), (FlyDroid, Alerts), (FlyDroid, Hotels),
    
    (iFly, Searches), (iFly, Alerts), (iFly, Hotels)
    
    }
    
      
    
    Then a subset to show which apps contain which features
    
      
    
    Includes = {(FlyDroid, Searches), (FlyDroid, Alerts), (iFly, Searches), (iFly, Hotels)}
    
      
    
    Suppose we then approach this subset with this proposition
    
    iFly includes Searches
    
    This is true because;
    
    (iFly, Searches) ∈ Includes
    
      
    
    Properties
    
    All properties contain left or right, related to the left or right side of the products
    
    In our case the apps are on the left and the features are on the right
    
      
    
    Left Total;
    
    Every element in the let set is connected to something on the right, but they could be connected to the same thing
    
      
    
    Right Total;
    
    All of the elements on the right must appear is something on the left, be that all the same or different
    
      
    
    Right Unique;
    
    Every element on the left is linked to at the most one element on the right, cannot be two, but both left could be linked to same right
    
      
    
    Left Unique;
    
    Every element on the right is related to at most one element on the left, no more, two is bad, 0 is okay.
    
      
    
    **Plotting points on a cartesian plane.**
    
      
    

## Actual Lecture.

  

**Sets revisited.**

  

Definition by enumeration;

A = {5, 6, 7, 8, 9, 10}

Definition by set-builder notation

A = { x ∈ Z | x > 4 ^ x < 11 }

  

**Why care about sets**

  

- Database query design
- Machine learning
- OOP
- Pattern Matching
- Any programming application where you need to store an unordered collection of unique elements.

  

**What are tuples**

**Sets vs. Tuples.**

- Duplicates don’t exist vs. Duplicates are fine
- The order is unimportant vs. Order is very important
- Defined using { } vs. Defined using < >

  

**Cartesian Products**

  

A = {1, 2, 3}

B = {7, 8, 9}

**A x B** gives us the set { (x, y) | x ∈ A ^ y ∈ B }

{(1, 7), (1, 8), (1, 9), (2, 7), (2, 8), (2, 9), (3, 7), (3, 8), (3, 9)}

These are tuples inside of a set.

  

**B x A** gives us the set { (y, x) | x ∈ A ^ y ∈ B }

Same thing but the y comes first

  

A = {1, 2, 3}

A x A can also be written as A^2

{ (x, y) | x ∈ A ^ y ∈ A }

{(1, 1), (1, 2), (1, 3), (2, 1), (2, 2), (2, 3), (3, 1), (3, 2), (3, 3)}

What would this be?

{ (x, x) | x ∈ A }

{(1, 1), (2, 2), (3, 3)}

X cannot be 2 things at once!

The cartesian of a full set and an empty set is an empty set.

  

**Relations**

  

A relation can be considered a subset of a cartesian product

{(1, 7), (1, 8), (1, 9), (2, 7), (2, 8), (2, 9), (3, 7), (3, 8), (3, 9)}

here is a subset

C = {(1, 7), (2, 8), (3, 9)}

Here we have a relation, and we can make the following assertions

(1, 7) ∈ C

(2, 9) ¬∈ C

  

A = { RL, EW, NP }

B = { CS1MCP, CS1OOP, CS1CS }

Teaches = {(RL, CS1MCP), (RL, CS1OOP), (EW, CS1MCP), (NP, CS1OOP)}

Here “Teaches” is a relation.

  

**Properties of Relations**

  

![[Untitled 22.png|Untitled 22.png]]

{ (1, 8), (2, 8), (2, 9), (3, 9) }

  

**Left-total**

Each element on the left is related to at least one element on the right.

![[Untitled 1 11.png|Untitled 1 11.png]]

Left-total

  

**Right-total**

Each element on the right connects to at least one element on the left

![[Untitled 2 11.png|Untitled 2 11.png]]

Right-Total

  

**Right-unique**

Each element on the left is related to **at most** one element on the right.

![[Untitled 3 9.png|Untitled 3 9.png]]

Right-Unique

  

**Left-unique**

Each element on the right is related to **at most** one element on the left.

![[Untitled 4 8.png|Untitled 4 8.png]]

Left-unique

![[Untitled 5 8.png|Untitled 5 8.png]]

  

**Functions**

  

Some relations are also functions

A relation is a function when it is both **left total and right unique**

- $f$﻿: A → B

**If all on the left have a single arrow, it is a function.**

A is called the **domain** of $f$﻿, and B is called the **codomain**

If the function is left-unique, it is an **injective** function

If it is right-total, it is a **surjective** function

Both left-unique and right-total(everything), it is a **bijective** function

  

**Reflexivity**

  

(**∀**x ∈ A) x R(elates) x

- Each member of set A relates to itself or “All instances of x in set A are such that x relates to x
- Example for the set {1, 2, 3} : {(1, 1), (2, 2), (3, 3)} - This is reflexive
- In graphical terms each set points to itself

```Mermaid
graph TD
  setA --> setA
	setB --> setB
	setC --> setC
```

^ reflexivity example.

  

**Symmetry**

  

(∀x ∈ A)(∀y ∈ A)( x R y ←→ y R x)

- x is related to y if (and only if) y is related to x; any relation between two elements must be bi-directional
- Example for set {1, 2, 3} : {(1, 2), (2, 1), (1, 3), (3, 1)}

```Mermaid
graph TD
  setA --> setB
	setB --> setA
```

  

**Transitivity**

  

(∀x ∈ A)(∀y ∈ A)(∀z ∈ A) ((x R y ^ y R z) → x R z)

- if x relates to y and y relates to z then x relates to z
- Example for set {1, 2, 3} : {(1, 2), (2, 3), (1, 3)}

```Mermaid
graph TD
  x --> y
	y --> z
	z --> x
```