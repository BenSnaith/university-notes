
## Backwards Chaining (BC) Algorithm
- Form of reasoning
- Starts with the goal and works backwards, chaining through rules to find known facts that support the goal
### Properties
- Top-down approach
- Based on Modus Ponens inference rule
- Called a Goal-Driven approach
- Mostly used a depth-first search strategy for proof
### Example Disease Diagnosis 
- Rules:
	R1:  If nasal congestion and viremia, Then influenza
	R2: If runny nose, Then nasal congestion
	R3: If fever and headache, Then viremia

- Starting Facts:
	Fever, runny nose, headache

- Final Goal: Influenza?

| Cycle |       Working Memory        | Conflict Set | Rule Fired |
| :---: | :-------------------------: | :----------: | :--------: |
|   1   |          Influenza          |      R1      |     R1     |
|   2   |  Nasal Congestion, Veremia  |    R2, R3    |     R2     |
|   3   |     Runny Nose, Veremia     |      R3      |     R3     |
|   4   | Runny Nose, Fever, Headache |              |    Halt    |
## Limitations of Propositional Logic
- inability to express relationships between objects or quantify statements
- Example:
	- Problem: Assigning Car colours to Ben, Joe S, Joe F, and Sohail
	- Required 48 rules to express exclusions (e.g., Ben's car is not red and blue simultaneously)
### Challenges:
1. Redundancy: Repetition of rules for similar constraints
2. Scalability: Exponential increase in rules with more objects.

## First-Order Logic
- Not only assumes that the world contains facts (propositions either true or false)
- Also assumes  the following things in the world:
	- Constant Symbols represents objects: Ben, Joe .., Red, Blue, …
	- Predicate Symbols represent relationships: 
		- It can be unary relation such as: is round, is adjacent to something
		- Or n-any relation such as: the sister of, brother of, has colour
### Example:

##### Constant Symbols                           Predicate Symbols
   Ben         Red                                             Person
   Joe F       Blue                                            Colour
   Joe S       White                                         BelongsTo
   Sohail     Black

#### Logical Sentences:
Person (Ben)                   Ben is a person
Colour (Red)                   Red is a colour
¬Colour(Ben)                 Ben is not a colour
Belongs(Red, Sohail)      Red car belongs to Sohail
### First-order Logic - Quantifiers
- #### Universal Quantifier:
	∀x. BelongsTo(Red, x) → ¬BelongsTo(Blue, x)

	For all objects x, if red car belongs to x, then blue car does not belong to x.
	(Anyone who has a red car does not have a blue car)

- #### Existential Quantifier
	∃x. Person (x) ∧ BelongsTo(Red, x)

	There exists and object x such that x is a person and Red car belongs to x.
	(Red car belongs to a person)

- #### Combination of universal and existential quantifiers:
	∀x. Colour(x) → (∃y. Person (y) ∧ BelongsTo(x, y))

	For all objects, x, if x is a colour, then there exists an object y such that y is a person and car with colour x belongs to y

	(A car of every colour belongs to a person)

### Example:
The law says that **it is a crime for an American to sell weapons to hostile nations**. The country **Nono, an enemy of America**, **has some missiles**, and **all of its missiles were sold to it by Colonel West**, **who is American**. **All missiles are weapons** and **all enemies of America count as “hostile”**. 

Question: Is Colonel West a criminal?

#### Represent the facts in first-order logic:
American(x) ∧ Weapon(y) ∧ Sells(x, y, z) ∧ Hostile(z) → Criminal(x) **RULE**
Enemy(Nono, America) **FACT**
∃ x Owns(Nono, x) ∧ Missile(x) **?**
Missile(x) ∧ Owns(Nono, x) → Sells(West, x, Nono)**RULE**
American(West) **FACT**
Missile(x) → Weapon(x) **RULE**
Enemy(x, America) → Hostile(x) **RULE**


∃ x Owns(Nono, x) ∧ Missile(x):{Owns(Nono, M), Missile(M)} **facst**

#### Expert System:
- Rules:
	R1: American(x) ∧ Weapon(y) ∧ Sells(x, y, z) ∧ Hostile(z) → Criminal(x)
	R2: Missile(x) ∧ Owns(Nono, x) → Sells(West, x, Nono)
	R3: Missile(x) → Weapon(x)
	R4: Enemy(x, America) → Hostile(x)

- Known Facts:
	Enemy (Nono, America)
	Owns (Nono, M)
	Missile (M)
	American (West)

- Goal: Criminal (West)
#### FC Algorithm
![[Pasted image 20241229162924.png]]
#### BC Algorithm
![[Pasted image 20241229163007.png]]