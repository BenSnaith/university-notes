- Support Video Notes
    
    ## Languages and Alphabets
    
    This is the syntax we use to denote an **Alphabet.**
    
    ![[Untitled 18.png|Untitled 18.png]]
    
    Σ ← This symbol is called sigma (patrick bateman)
    
    Notice that this alphabet is similar to out own, but for the sake of simplicity we have just used the first 10 letters, a-j
    
    An **Alphabet** is a set of symbols, meaning there are no duplicates and the order of symbols within the set is irrelevant. An alphabet is a **finite** set meaning its contents cannot go indefinitely, it is also non-empty, so Σ = { } is not a valid alphabet despite it being a valid **set.**
    
    We can make words from the symbols within our alphabet, such as: **ace**
    
    This is a word as it comprises letters from our alphabet and we would write it in this way:
    
    **ace is a** **word over** Σ
    
    There is no requirement to use the words in order.
    
    **bed is a** **word over** Σ
    
    Each symbols can be used as many times as needed.
    
    **bee is a** **word over** Σ
    
    The word doesn’t even have to be a real, dictionary word, here word takes a different meaning.
    
    **bdjfch is a** **word over** Σ
    
    This is not a word over our alphabet: **Fake**, the symbol K does not appear in our alphabet and therefore, this is not a valid word.
    
    ε ← This is called epsilon and it denotes an empty word, which is an acceptable word over any alphabet
    
    Σ* ← This is a set that contains infinite words for the original and it is infinite, how? see this example
    
    Σ = {a, b, c }
    
    Σ* = {a, aa, aaa, aaaa, aaaaa, aaaaaa, aaaaaaa, aaaaaaaa, aaaaaaaaa}
    
    This just goes on forever, so aababababbbcbcbcbccbccbcbcccbcbcbccbbcbab would be a word in there somewhere, it would be infinite even if our alphabet only contained one single symbol
    
    Notice how we call the objects in out alphabet **Symbols** and not **Letters**, this is because our alphabet can be comprised of any symbols and not just letters, these are all valid alphabets
    
    Σ = {a, b, c, d, e, f, g, h, i, j}
    
    Σ = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
    
    Σ = {heart, diamond, club, spade}
    
    Lets introduce the concept of a **Language** here is one:
    
    Σ = {a, b, c, d, e, f, g, h, i, j}
    
    L = {bad, fade, hi}
    
    Since all the words in the language can be formed using symbols from our alphabet, we can say that this is a **Language over our Alphabet,** we can also use this notation: L ⊆ Σ*
    
    Notice that some words: face, bag, if, are words over the alphabet, but are not part of this language, perhaps they belong to some other language?
    
    L$_2$﻿ = {face, bag, if}
    
    You might see other notation (similar to set builder notation} used when building a language, as it is not always practical or possible to write out every single combination, A language containing all possible decimal numbers would be an example of an infinite language, and one that we can not write out.
    
    L = {_Literally all possible decimal numbers_}
    
    Here is our alphabet
    
    Σ = {1, 2, 3, 4, 5, 6, 7, 8, 9, **.** }
    
    (take note of the decimal)
    
    Now we can’t actually allow all possible patterns of these symbols for the set we are attempting to create as these are not valid: 1.2.3; 00001; ..019; .1 etc.
    
    So how do we define what is acceptable in our language.
    
    **L = {0} ∪ { 0 . w****$^1$**﻿ **| w****$^1$**﻿ **∈ (Σ \ {.})* }**
    
    In English: **Our language consists of 0 and 0 + . + word****$^1$**﻿**, where word****$^1$**﻿ **is a member of** Σ **excluding .**
    
    So word$^1$﻿ will follow 0. and can consist of anything in the alphabet that isn’t the . (decimal)
    
    But wait, decimal numbers don’t just start with 0, so lets use a union operation to account for this.
    
    **∪ { x w | x ∈ (Σ \ {0, .}) ^ w ∈ (Σ \ {.})*}**
    
    This would be connected with the last part to create
    
    L = **{0} ∪ { 0 . w****$^1$**﻿ **| w****$^1$**﻿ **∈ (Σ \ {.})* } ∪ { x w | x ∈ (Σ \ {0, .}) ^ w ∈ (Σ \ {.})*}**
    
    ## Finite State Machines
    
    a.k.a Deterministic Finite State Automata
    
    Is a mathematical model that accepts a word as an input, however a word here is defined as a sequence of symbols rather than Standard English words. Based on this definition, these are all words:
    
    20p, 50p, 2p
    
    3.14159
    
    WORD
    
    dot dot dash dot
    
    Ultimately, the finite state machine can be used to determine whether a word is good (accepted) or bad (rejected), lets say we have a machine to determine whether an input is a well formed decimal number.
    
    In this case we would expect it to recognise these as good: **12.3, 0**
    
    And these as bad: **00, 1.2.3**
    
    An intuitive means of representing a finite state machine is by using a State Transition Diagram
    
    **Circles** represent **states** out machine can be in
    
    **Arrows** represent **transitions**
    
    Each **state** has a unique **identifier** such as N and N$_0$﻿ is our starting state
    
    ![[Untitled 1 7.png|Untitled 1 7.png]]
    
    The arrow coming from nowhere shows where the machine starts and the diagram can only have one of these.
    
    Σ = {1, 2, 3, 4, 5, 6, 7, 8, 9, **.** }
    
    ![[Untitled 2 7.png|Untitled 2 7.png]]
    
    Depending on what the symbol is we are dealing, we take one of the given paths, where ever we end up with the first symbol, that is where we move on from with the second symbol, a circle within a circle is a goal state and if by the end of our word, the current state is a goal state, then the word is valid.
    
    **Transition Table:**
    
    ![[Untitled 3 6.png|Untitled 3 6.png]]
    
- Lecture Notes
    
    ## Why do we care?
    
    Formal language and automate are essential in:
    
    - Development of better programming languages and tools
    - Computer processing of natural languages
    - Grokking regular expressions, efficient text processing
    
    Applications:
    
    - Robotics
    - Chemistry
    - Mechanical Engineering
    - Many more!
    
    ## Languages
    
    Language: a system through which we communicate to each other.
    
    - Sets of symbols
    - Rules for manipulation
    
    |Natural Languages|Formal Languages|
    |---|---|
    |Languages that people speak|Designed for specific applications|
    |Sets of symbols|Important role in programming languages in CS|
    |Sets of words on these symbols|Can forbid some words|
    |Rules to joining these words to form a sentence||
    
    ## Alphabets, Words and Languages
    
    **Alphabet**
    
    - Set of symbols
    - Σ: denotes an alphabet
    - Elements are knows as letters
    
    **Word**
    
    - A sequence of symbols of the alphabet
    
    **Language**
    
    - A set of words
    
    **Words over an alphabet Σ**
    
    - Words using only symbols from the alphabet Σ
    
    L**anguage over an alphabet Σ**
    
    - Language with words over alphabet Σ
    
    ## Empty Word, Word Length
    
    If _w_ is a word, its length is written as |w| like cardinality
    
    |aabb| = 4
    
    |10001| = 5
    
    |a| = 1
    
    **Is there a word of length 0?**
    
    ε is the empty word, the only word where |ε| = 0
    
    ## Word Concatenation
    
    a . (dot) operator:
    
    - to “glue” symbols together in a word
    - to “glue” words, connect words to form bigger words
    
    a.b.f.f.a.b = abffab
    
    ## Set of all words.
    
    Assume an alphabet:
    
    Σ = {a, b}
    
    The set of all words over this alphabet
    
    Σ* = {a, aa, aaa, aaaa, aaaaa, } infinite
    
    ## Defining languages as set builder notation.
    
    Assume these alphabets:
    
    Σ$_1$﻿ = {a, b}, Σ$_2$﻿ = {0, 1}, Σ$_3$﻿ = {a}
    
    Some languages:
    
    ![[Untitled 4 5.png|Untitled 4 5.png]]
    
    ## Automata for language checking
    
    Automata theory:
    
    - Study of abstract computer devices or “machines”
    - These computer devices or “machines” follow a pre-defined sequence of operations automatically
    
    Automaton:
    
    - Abstract model of digital computer that has a mechanism to read an input string over a given alphabet
    - Decides whether a string belong to a language or not
    - Contains internal states
    - Transition from one state to another: transition relation
    - Types: Deterministic and non-deterministic
    
    ## Deterministic Finite Automation (DFA)
    
    ![[Untitled 5 5.png|Untitled 5 5.png]]
    
    ## Automata as maths objects. (formally)
    
    ![[Untitled 6 3.png|Untitled 6 3.png]]
    
    ## DFA: How it works?
    
    - The automaton is in the initial state
    - The automaton reads the string (left to right)
    - Each transition consumes one input symbol
    - The transition function decides the next state
    - At the end of the string, the string is accepted if a final state has been reached
    - Otherwise, the string is rejected
    
    ## Example
    
    ![[Untitled 7 2.png|Untitled 7 2.png]]
    
    ## Decoding math descriptions of automata
    
    ![[Untitled 8 2.png|Untitled 8 2.png]]
    
- Trev Tutor
    
    [Video](https://www.youtube.com/watch?v=7MBpk4gJRkk)