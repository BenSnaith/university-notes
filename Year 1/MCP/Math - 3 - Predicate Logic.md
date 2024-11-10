
    
    **Cardinality** - The amount of items within a set.
    
    A **subset** is a set within a parent set which is fully contained inside of it.
    
    ∈ ∉ ⊆ ⊂⊄
    
    {0, 1, 2} == {0, …, 2}
    
    {0, 1, …, 1000} = 1001 card.
    
    {0, 1, 2, …} = N, the set of all natural numbers.
    
    {…, -2, -1, 0, 1, 2, …} = Z all + and - integer numbers.
    
    ## Set membership notation.
    
    x ∈ S == x (object) is an element of S (set)
    
    1 ∈ {1, 2}
    
    3 ∉ {1, 2}
    
    x ∈ S  
    This is a proposition as it could be true or false.  
    
    ==0 ∈ N==
    
    ==0 ∈ Z==
    
    ==-1 ∈ N==
    
    ==-1 ∈ Z==
    
    Can a set contain a set {1, 2, 3} ∈ S / S ∈ S.
    
    ## Subset relation
    
    S ⊆ T  
    Set S is a subset of T.  
    
    {1} ⊆ {1, 2}
    
    whenever x ∈ S ^ x ∈ T
    
    X where X is in S and X is in T
    
    {1} ⊆ {1, 2}
    
    { } ⊆ T, and empty set is always a subset.
    
    {1} ⊄ { }  
    1 is not a subset of { }  
    
    ![[Untitled 21.png|Untitled 21.png]]
    
    a) the first set implicates the second.
    
    ![[Untitled 1 10.png|Untitled 1 10.png]]
    
    Yes is S == T
    
    ![[Untitled 2 10.png|Untitled 2 10.png]]
    
    b) when using ⊆ you have to be connecting a whole set, whereas ∈ is for 1 element
    
    ![[Untitled 3 8.png|Untitled 3 8.png]]
    
    a) true
    
    b) true
    
    c) true
    
    d) true
    
    e) false cant use a set with ∈
    
    ## Union, intersections and differences.
    
    ![[Untitled 4 7.png|Untitled 4 7.png]]
    
    S ∪ T
    
    x ∈ S ∪ T
    
    (x ∈ S) v (x ∈ T)
    
      
    
    S ∩ T
    
    x ∈ S T
    
    (x ∈ S) ^ (x ∈ T)
    
      
    
    S \ T
    
    x ∈ S but ¬T
    
      
    
    algebras
    
    ![[Untitled 5 7.png|Untitled 5 7.png]]
    
    ## Predicate formulas.
    
    Wait while there is rain, or we are not in a rush and it is raining.
    
    ![[Untitled 6 5.png|Untitled 6 5.png]]
    
    simplified the logic down to just p (isRaining).
    
      
    
    Charge while electricity is cheap
    
    ```Java
    startCharging()
    while(isCheap(price))
    { // Proposition using predicate + object
    	waitABit();
    }
    stopCharging();
    ```
    
    proposition  
    isCheap(), this can be either true or false its Boolean.  
    
    isCheap(electricityPrice)  
    a predicate, an object/value  
    
      
    
    propositional logic (unit 2)
    
    The player is banned if cheating is detected.
    
    c > b
    
    if cheating, then banned
    
      
    
    predicate logic
    
    If any player is cheating then that player will be banned.
    
    c(x) = player caught cheating
    
    b(x) = player is banned
    
    for all players x.
    
    c(x) > c(b)
    
    ![[Untitled 7 4.png|Untitled 7 4.png]]
    
    ![[Untitled 8 4.png|Untitled 8 4.png]]
    
    ![[Untitled 9 3.png|Untitled 9 3.png]]
    
      
    
    {x + 1 | x ∈ {1, 2, 3} ^ x is odd} = {4}
    
    { x | x ∈ N ^ x < 3} = {0, 1, 2}
    
    { x ∈ TheBeatles | PlaysThe(x, drums)} = ringo, paul
    
    { x.father | x ∈ TheBeatles ^ PlaysThe(x, drums)} == ringo.father, paul.father
    
    Ax = All
    
    Ex = there exists
    
    |   |   |   |   |
    |---|---|---|---|
    |A|B|||
    |||||
    |||||
    |||||
    |||||
    |||||
    |||||
    
- Tutorial and Additional Questions
    
    [[Math - Predicate Logic - Additional Questions]]
    
- Support Video Notes
    
    # Further revision / understanding
    
    ## Sets
    
    _What is a set?_  
    A set can be basically anything, all collected together  
    
    An example of a basic set would be.
    
    Let **A** be {1, 2, 3, 4, 5}
    
    … = and so on, at the start or the end it denotes an infinite set.
    
    let B be {…, -1, 0, 1, 2, …}, this contains every possible integer.
    
      
    
    This symbol: ∈, means that the object before is a member of the set afterward.
    
    5 ∈ A, 100 ∈ B
    
    This symbol: ∉, means the object before is not a member of the subsequent set
    
    6 ∉ A so does this ¬(6 ∈ A)
    
    if we was 5 ∉ of our set A, that would be false, because it is a member, it’s not not a member.
    
      
    
    ## Set builder notation
    
    { x ∈ B | x > 0 ^ x < 6}
    
    X can be a member of B, **where** x is greater than 0, and less than 6.
    
    { x ∈ C | x > 10 ^ x < 10}
    
    X can be a member of C, where x is greater than 10 and less than 10.
    
    This set is empty, it’s cardinality is 0, and can be represented as { }
    
    { x ∈ C | x < 7 ^ x > 5}
    
    This set can only contain the number 6, this makes it a singleton set, with a cardinality of 1
    
    {6}
    
      
    
    ## Elements in a set are distinct
    
    Let **D** be {4, 2, 6, 4, 8, 4, 2}
    
    How many elements are in this set.
    
    4, we don’t count duplicates.
    
    |D| = 4
    
      
    
    ## Subsets
    
    E: {2, 3, 4} F: {1, 2, 3, 4, 5}
    
    E ⊆ F
    
    G: {5, 6, 7} H: {3, 5, 7, 9}
    
    G ⊄ H
    
    J: {0, 1, 2} K: {0, 1, 2}
    
    J ⊆ K, identical sets are subsets of one another.
    
    J = K, but ¬(G = H) and ¬(E = F)
    
      
    
    # Set operators.
    
    ## What are they
    
    Set operators perform operations on sets.
    
    We will use, Union, Intersection and Difference.
    
    ![[Untitled 10 3.png|Untitled 10 3.png]]
    
    Let A = {Charlie, Oscar} //Full time education
    
    Let B = {Oscar, Juliet} //Aged 18-22
    
    Oscar is one person.
    
    If being in full time education or being aged 18-22 gets you a travel-card, then everyone gets one.
    
    A ∪ B = {Charlie, Oscar, Juliet}
    
    { x | x ∈ A v x ∈ B }
    
    Now only people in full-time education and aged 18-22 get one.
    
    A ∩ B = {Oscar}
    
    { x | x ∈ A ^ x ∈ B }
    
    If there is no elements, the sets are disjoint.
    
    A \ B = Charlie and B \ A = Juliet, the order here is important.
    
    { x | x ∈ A ^ x ¬∈ B }
    
      
    
    # Predicate Logic
    
    Predicate logic uses variables, that’s the whole difference.
    
    is x > 5?, we don’t know yet but it can only be either true or false.
    
    In predicate logic we have:
    
    - Boolean: True / False
    - Logical Operators: ^ v ¬
    - Term values: 12, -5, 0, 3.14159
    - Term variables: _x y z_
    - Predicate Letters: P Q R
    
      
    
    Predicate P(v1, v2, …) contains n free variables. thus has an arity of n.
    
    isEdible(cake), this is not predicate as we have a value (cake).
    
    isEdible(glass)
    
    isEdible(x), now this is a predicated as we do not know whether it is true or false.
    
      
    
    isPrime(17), not a predicate, we have a value and therefore a T/F answer.
    
    isPrime(x), this is a predicate, we don't know the answer.
    
      
    
    **arity of 1**
    
    P(y) let p(y) be the predicate, y is prime. (we need this or P alone makes no sense)
    
    P(17) = True  
    P(4) = False  
    
    **arity of 2**
    
    R(x, y) x > y
    
    R(6, 5) = True  
    R(5, 5) = False  
    
    The predicate behaves like a Method in Java, and the variables like arguments.
    
    **arity of 3**
    
    R(x, y, z)
    
    **arity of n**
    
    we don’t know the amount of variables.
    
      
    
    R(x) is the predicate P(5, y)
    
    P(5, y) is the predicate 5 > y
    
    if we input 5, we get 5 > 5
    
      
    

## My attempt at understanding the lecture.

The part after the algebra but where it got real confusing for no reason.

  

Predicate Logic is like logic with variables which are subject to change.

We can use java like notation.

  

x ∈ Events | getYear(x) | HeldInYear(x ,getYear(x))

  

**Predicate Formulas for Sets**

  

Truth sets = a unary predicate (one variable) predicate P for set A = subset A where P holds true.

Examples;

|   |   |   |   |
|---|---|---|---|
|Set|Predicate|Truth Set|Set Builder Notation|
|{1, …, 10}|IsEven|{2, 4, 6, 8, 10}|{ x ∈ {1, …, 10} \| isEven(x)|
|TheBeatles|PlaysTheGuitar|{John, Paul, George|{ x ∈ TheBeatles \| PlaysTheGuitar(x)|

  

**Set builder notation**

  

Set builder notation = a construction that builds a set from a truth set using a common pattern

Anatomy of set builder notation; { pattern using x, y | predicate restricting x, y }

Examples;

|   |   |
|---|---|
|Set Builder|Enumeration|
|{ x + 1 \| x ∈ {1, 2, 3} ^ x is odd }|{2, 4}|
|{ x + 1 \| x ∈ {1, 2, 3}}|{2, 3, 4}|
|{ x \| x ∈ N ^ x < 3 }|{0, 1, 2}|
|{ x ∈ TheBeatles \| PlaysThe(x, Drums)}|{Ringo, Paul}|
|{x.father \| x ∈ TheBeatles ^ PlaysThe(x, Drums)}|{RichardStarkley, JamesMcCartney}|

  

**Universal Quantifier**

  

For all of x, where x is something; ∀x

English;

for all players x; isCheating(x) → isBanned(x)

Official math notation;

(∀x ∈ Player)(c(x) → b(x))

alternatively;

(∀x)(x ∈ Player ^ c(x) → b(x))

  

**Existential Qualifier**

  

There exists an x, where x is a member of something and it does something

English;

There exists a player who has been caught cheating

There exists a player x, such that x has been caught cheating

Official math notation;

(∃x ∈ Players)(c(x))

Alternatively;

(∃x)(x ∈ Players ^ c(x))

  

**Quantifiers via a truth table**

  

(∀x ∈ TheBeatles)(PlaysThe(x, Guitar) v PlaysThe(x, Drums)) = True

|x ∈ TheBeatles|PlaysThe(x, Guitar)|PlaysThe(x, Drums)|PlaysThe(x, Guitar) v PlaysThe(x, Drums|
|---|---|---|---|
|John|T|F|T|
|Paul|T|T|T|
|George|T|F|T|
|Ringo|F|T|T|

All the members of TheBeatles play the guitar or drums, so this is TRUE.

  

(∃x ∈ TheBeatles)(PlaysThe(x, Guitar) ^ PlaysThe(x, Drums)) = True

|x ∈ TheBeatles|PlaysThe(x, Guitar)|PlaysThe(x, Drums)|PlaysThe(x, Guitar) ^ PlaysThe(x, Drums|
|---|---|---|---|
|John|T|F|F|
|Paul|T|T|T|
|George|T|F|F|
|Ringo|F|T|F|

The exists a member of TheBeatles that play the guitar and drums.