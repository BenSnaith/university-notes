### Hadoop and Database: OLTP

 - Relational Databases vs. MapReduce

![[Pasted image 20260203125236.png]]

 - Hadoop Underpinning OLTP (On-Line Transaction Processing)
	 - SQL statements are optimised for execution using relational algebra.
	 - Hadoop as backend for OLTP; MapReduce implementation of relational algebra operators

![[Pasted image 20260203125340.png]]

### Relational Algebra

![[Pasted image 20260203125355.png]]

### MapReduce Implementation of Selection

![[Pasted image 20260203125421.png]]

### Projection

![[Pasted image 20260203125434.png]]

### Union, Intersection, Difference

![[Pasted image 20260203125456.png]]

### Grouping & Aggregation

![[Pasted image 20260203125531.png]]

### (Natural) Join

 - (Natural) Join in RA vs. (Inner) Join in SQL
	 - Reduce-Side Join: Repartition Join.
	 - Map-Side Join: Replicated Join (A restricted type of join implementation)

![[Pasted image 20260203125649.png]]

### Reduce-Side Join

![[Pasted image 20260203125710.png]]

### Reduce-Side Join: One-to-One

![[Pasted image 20260203125726.png]]

### Reduce-Side Join: One-to-Many

![[Pasted image 20260203125751.png]]

### Reduce-Side Join: Many-to-Many

![[Pasted image 20260203125816.png]]