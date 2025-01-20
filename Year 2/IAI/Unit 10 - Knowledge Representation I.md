## Knowledge and Knowledge Representation
### Knowledge Representation:
- The Process of encoding knowledge about the world into a format understandable by computers
- Used by knowledge-based agents to reason and make decisions
### Reasoning Example:
1. Rule: If tried to go right but couldn't, then the cell on the right is blocked
2. Fact: I was at cell 5, tried to go right but couldn't
3. Conclusion: Cell 6 is blocked
### Machine Learning Knowledge Example:
- PlayTennis Problem:
	- Rule: If outlook is sunny and temperature is hot and humidity is high and wind is weak, then the player does not play tennis
## Logic and Propositional Logic
### Logic:
- A system for reasoning about assertions (sentences) in a knowledge representation language
- **Propositional Logic**: Studies logical relationships between propositions (statements that can be true or false)
### Key Components:
1. Proposition Symbols: Represent statements (e.g. P, Q, R)
2. Logical Connectives:
	- Not (¬): Negates a statement
	- And (∧): Combines statements where both must be true
	- Or (∨): Combines statements where at least one must be true
	- Implication (→): If one statement is true, another must follow
	- Biconditional (↔): Two statements are true simultaneously
### Logical Connectives
#### Not (¬)

| P     | ¬P    |
| ----- | ----- |
| false | true  |
| true  | false |
#### And (∧)

| P     | Q     | P∧Q   |
| ----- | ----- | ----- |
| false | false | false |
| false | true  | false |
| true  | false | false |
| true  | true  | true  |
#### Or (∨)
| P     | Q     | P∨Q   |
| ----- | ----- | ----- |
| false | false | false |
| false | true  | true  |
| true  | false | true  |
| true  | true  | true  |
#### Implication (→):
| P     | Q     | P→Q   |
| ----- | ----- | ----- |
| false | false | true  |
| false | true  | true  |
| true  | false | false |
| true  | true  | true  |
#### Biconditional (↔):

| P     | Q     | P↔Q   |
| ----- | ----- | ----- |
| false | false | true  |
| false | true  | false |
| true  | false | false |
| true  | true  | true  |
## Models and Entailment
### Model:
- Assignment of a truth value to every propositional symbol (a "possible world")
- Example: {𝑃: 𝑇𝑟𝑢𝑒, 𝑄: 𝐹𝑎𝑙𝑠𝑒, 𝑅: 𝑇𝑟𝑢𝑒}

- $n$ propositional symbols = $2^n$ Possible models
### Entailment:
- KB ⊨ 𝛽
- In evert model in which knowledge base KB is true, sentence 𝛽 is also true
- Example: It is a Tuesday in March ⊨ It is March
## Inference Algorithms
- Purpose:
	- Use rules to derive new facts from existing knowledge
	- Trying to answer the question:
		 Does KB ⊨ 𝛼
### Inference Algorithm 1: Model Checking
- To determine if KB ⊨ 𝛼
	- Enumerate all possible models.
	- If in every model where KB is true, 𝛼 is true, then KB entails 𝛼
	- Otherwise, KB does not entail 𝛼
#### Challenges:
- Computationally expensive as the number of models grows exponentially with symbols, to combat this we can use inference rules:
#### Inference Rule 1: Modus Ponens

If it is raining, then Alex is inside.
It is raining.

----
Alex is Inside

𝛼 → 𝛽
   𝛼
  
--------
𝛽
#### Inference Rule 2: Modus Tollens

If it is raining, then Alex is inside. 
Alex is not inside.

---
It is not raining.

𝛼 → 𝛽  
¬𝛽

---
¬𝛼
#### Inference Rule 3: Contraposition

**Contrapositive**: A proposition formed by **contradicting** both the **premise** and **conclusion** of a given rule and **interchanging** them.

  (premise)          (conclusion)
If it is raining, then Alex is inside

---
If Alex is not inside, then it is not raining
Not (Conclusion)          Not (Premise)

𝛼 → 𝛽

---
¬𝛽 → ¬𝛼

### Inference Algorithm 2: Forward Chaining
#### Purpose:
- Derives conclusions by iteratively applying rules to known facts in the knowledge base
#### Process:
1. Initialize **working memory** with known facts.
2. Identify the **conflict set**: Rules whose premises match known facts.
3. Apply a rule ("fire it") from the conflict set using **Modus Ponens**.
4. Update working memory with the inferred fact.
5. Repeat until the goal is reached or no further inferences can be made.
#### Conflict Resolution Strategies:
1. **First-In, First-Serve** (FIFO).
2. **Last-In, First-Serve** (LIFO).
3. **Prioritisation**: Fire higher-priority rules first.
#### Example: Disease Diagnosis
- **Rules:**
    - R1: If nasal congestion and viremia, then influenza.
    - R2: If runny nose, then nasal congestion.
    - R3: If fever and headache, then viremia.
- **Facts:** Fever, runny nose, headache.
- **Goal:** Determine if the patient has influenza.

| Cycle |                            Working Memory                            | Conflict Set | Rule Fired |
| :---: | :------------------------------------------------------------------: | :----------: | :--------: |
|   1   |                     fever, runny nose, headache                      |    R2, R3    |     R2     |
|   2   |            fever, runny nose, headache, nasal congestion             |    R2, R3    |     R3     |
|   3   |        fever, runny nose, headache, nasal congestion, veremia        |  R2, R3, R1  |     R1     |
|   4   | ever, runny nose, headache, nasal congestion, viremia, **influenza** |  R2, R3, R1  |    Halt    |
R1: **If** nasal congestion and viremia, **Then** influenza  
R2: **If** runny nose, **Then** nasal congestion  
R3: **If** fever and headache, **Then** viremia  

𝛼 → 𝛽  
   𝛼  
   
  𝛽

#### Proof Tree Representation: 
- Visualise the derivation process as a tree where facts lead to intermediate conclusions and, eventually, the goal.

![[Pasted image 20241229004111.png]]

- It is a down-up approach, as it moves from bottom (known facts) to top (goal)

#### Applications of Forward Chaining
1. **Expert Systems:** Use large rule sets for diagnostics (e.g., medical diagnosis, troubleshooting).
2. **Decision Support:** Systems assisting in structured problem-solving.