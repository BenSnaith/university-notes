- Support Video Notes
    
    ## What is a regular expression?
    
    A regular expression is a sequence of characters that can be used for pattern matching within strings, this is the standard definition, but what does it mean?
    
    ## Example
    
    Suppose you are writing some example code for a valid UK National Insurance Number, there are several rules a string must follow in order to be considered a valid National Insurance Number.
    
    _The first two characters must be upper case letters._
    
    _The next six should be numeric_
    
    _The last one should be: A, B, C, D_
    
    To make expressing this rule easier, we opt for a regular expression, any input string can be compared with the expression and if it matches, then it is good to go.
    
    ## Components that make up a RegEx
    
    It’s worth noting that there are multiple dialects of regular expression rather than one standard form, even in one such dialect there may be multiple valid ways of writing essentially the same thing.
    
    Here we will concern ourselves with:
    
    * ← Kleene Star
    
    + ← Plus
    
    ( ) ← Brackets
    
    _Different dialects may use different symbols, or use these symbols in a different way._
    
    The Kleene Star ‘*‘means any number of the preceding item, including 0, so if we had a*, this could be: a; aaa; aaaaaaaaa; aaaaaaaaaaaaaaaaaaaaaaaaaaaaaa; epsilon; (not at all)
    
    The Plus Symbol ‘+’ provides alternatives: A + B + C + D, it can only be one of these for but it cannot be nothing, must be one of them.
    
    The Brackets ‘( )’ allows us to mark out a sub-section of the RegEx, basically like normal brackets, must be done separately or whatever.
    
    ## Searching
    
    Regular Expressions can be used for searching for a string within another string, lets say we have a document which may or may not contain the word harbour, and we would like to change all instances of harbour → port, the document may however use UK spelling “harbour”, US spelling “harbor” or a combination of both
    
    Using a regular expression we can search for both spellings in a single pass
    
    **harb(o + ou)r**
    
- Lecture Notes
    
    ## Why do we care about RegEx?
    
    - Grokking regular expressions, efficient text processing
    
    Applications:
    
    - Text search and manipulation: find specific patterns (variable names and functions) and make bulk changes
    - Form validation: help ensures user inputs adhere to specific patterns or constraints (email addresses, phone number, passwords)
    - Data extraction from web: locate and capture specific patterns (URLs, phone numbers, etc.)
    
    Regular expressions may occur in many places.
    
    - Supported by HTML5, JS, Java, Python, PHP and other languages
    - Many text editors (TextPad, Sublime, VIM, etc) allow it in search/replace
    
    ## Simple Examples
    
    Regular expressions: a way of describing a language via string representation
    
    |   |   |
    |---|---|
    |Regex (common)|Languages|
    |a|{a}|
    |ab|{ab}|
    |[ab] or (a\|b)|{a, b}|
    |(ab)?|{epsilon, ab}|
    |(ab)*|{epsilon, ab, abab, ababab, …}|
    
    ## Expressions in Mathematics
    
    Bracketed formulas with operators and basic values and or variables:
    
    (3 + 5) * 1/2
    
    ## Algebra of Languages — set operations
    
    ![[Untitled 19.png|Untitled 19.png]]
    
    ## Algebra of Languages — Concatenation
    
    ![[Untitled 1 8.png|Untitled 1 8.png]]
    
    ## Algebra of Languages — Iteration
    
    **Intuitive definition**:
    
    L$^k$﻿ = L.L.L.L
    
    for all K ∈ N
    
    **A more methodological definition**: Definition by induction
    
    ![[Untitled 2 8.png|Untitled 2 8.png]]
    
    ## Example
    
    Consider the language
    
    L$^0$﻿ = {ε}
    
    L$^2$﻿ = L.L = {aaaa, aab, baa, bb} (sets of strings formed by concatenating pairs of strings in L)
    
    L$^3$﻿ = L$^2$﻿.L
    
    L$^3$﻿ = {aaaaaa, aaaab, aabaa, aabb, bbaaaa, baab, bbaa, bbb}
    
    ## Algebra of Languages — Kleene Star
    
    Stephen Cole Kleen
    
    **Intuitive definition**:
    
    L* = L$^0$﻿ ∪ L$^1$﻿ ∪ L$^2$﻿ ∪ … (concatenation of any number of L)
    
    **A more methodological definition**
    
    L* is the smallest set width
    
    ε ∈ L*
    
    L*.L ⊆ L*
    
    ## Examples
    
      
    
      
    
      
    
- Trev Tutor
- math