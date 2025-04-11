### Unit Outcomes

Here you will learn

 - About different interpretations of the concept of a variable
 - About different aspect of a variable
 - About what types are used with respect to variables
 - To distinguish when two types are compatible
 - To identify the visibility scopes and lifetimes of variables

### The Concept of a Variable

 - **Variable** - An identifier that refers to a value/memory cell.
 - Imperative programming: **mutable** variables
 - Functional programming: **immutable** variables

#### Declarations

 - A variable is defined by its declaration
	 - **Explicit Declaration**

![[Pasted image 20250411193710.png]]

- **Implicit Declaration**

![[Pasted image 20250411193737.png]]

#### Aspects of variable

 - Name
 - Scope
 - Type (optional)
 - Lifetime(s)
 - Reference(s)
 - Value(s)

#### Static vs. Dynamic Concepts

 - A **static** programming language concept (e.g. an aspect of a variable):
	 - Well defined whether or not program is executing
	 - Can be worked out from the program text without too much work
 - A **dynamic** programming language concept:
	 - Directly refers to the program's execution
	 - To examine it, we must trace the program (in head or in debugger)

#### Multiple Lifetimes

