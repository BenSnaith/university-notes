- Support Video Notes
    
    ## Gaussian Elimination
    
    Is a means of solving a system of Linear equations, we are going to use these equations, which are linear as they do not contain exponents:
    
    x + y + z = 10
    
    3y + x + 2z = 21
    
    3x + 2y + 4z = 32
    
    When we say solving, we mean determining the values of x, y and z in this case. We are going to solve these equations using a matrix.
    
    We have 4 variables and their outcome so we will need 4 columns, we also have 3 equations so we will need 3 rows, this will be our matrix below:
    
    |X|Y|Z|Out|
    |---|---|---|---|
    |1|1|1|10|
    |1|3|2|21|
    |3|2|4|32|
    
    Our aim is to make the three in the bottom left corner 0. we can see this as a puzzle that must be solved by making a combination of legal moves, the legal moves are:
    
    - Swapping any two rows.
    - Multiplying a row by any constant.
    - Adding or subtracting rows or multiples of rows.
    
    We are going to begin by subtracting the first row from the second row, and placing the result in the second row
    
    |X|Y|Z|Out|
    |---|---|---|---|
    |1|1|1|10|
    |0|2|1|11|
    |3|2|4|32|
    
    We did this because we now have a 0 in one of the place where we want it.
    
    Next we are going to subtract Row 1 multiplied by 3 from row three
    
    |X|Y|Z|Out|
    |---|---|---|---|
    |1|1|1|10|
    |0|2|1|11|
    |0|-1|1|2|
    
    Negative numbers are completely fine. Next we are going to take Row 2 and add it to double row three, the result will override Row 3
    
    |X|Y|Z|Out|
    |---|---|---|---|
    |1|1|1|10|
    |0|2|1|11|
    |0|0|3|15|
    
    No we have all our zeros where we want them. these three moves are all we need to solve any set of linear equations that can actually be solved. If fractions were to appear at any point during the process, that would be fine, if any equation contained a -, that would also be fine.
    
    Why do we want 0’s in this corner, well this is arbitrary and they just have to be in one of the corners but we just choose this one. but it doesn’t even need to be a corner, all that matters is one row doesn’t have to contain any zero’s it can but we don’t car about them, one row must have 1 zero, and the last row must contain 2 with one of them being the other variable which is 0.
    
    So what do we do with this? let’s turn the bottom equation back into a form that we can recognise
    
    0x + 0y + 3z = 15  
    3z = 15  
    z = 5  
    
    Now let’s take the middle row
    
    2y + z(5 we know this from the previous) = 11  
    2y = 6  
    y = 3  
    
    Finally let’s take the top row
    
    x + y(3) + z(5) = 10  
    x + 8 = 10  
    x = 2  
    
- Lecture Notes
    
    ## System of Linear Equations
    
    - A linear equation is similar to a linear function, although an equation has a single input per variable, whereas a function has a set of input per variable
    - e.g. 3x = 12
    - A ‘system of linear equations’ is simply a collection of equations. That’s one or more, but usually more than one.
    - Try this:
    
    x + 3y = 17
    
    2x = 10
    
    x = 5
    
    y = 4
    
    ## A more challenging example.
    
    ![[Untitled 25.png|Untitled 25.png]]
    
    ## Augmented matrix
    
    ![[Untitled 1 14.png|Untitled 1 14.png]]
    
    ## Row echelon form (our target)
    
    ![[Untitled 2 14.png|Untitled 2 14.png]]
    
    ## The rules (to each row echelon form)
    
    - Any two rows can be swapped
    - Any row can be multiplied by a constant
    - A row can be added to or subtracted to by a row (or a multiple of another row), with the result overwriting either row.
    
    ## Solving for x, y, and z
    
    ![[Untitled 3 12.png|Untitled 3 12.png]]
    
    ![[Untitled 4 11.png|Untitled 4 11.png]]
    
    ![[Untitled 5 11.png|Untitled 5 11.png]]
    
    ![[Untitled 6 8.png|Untitled 6 8.png]]
    
    ![[Untitled 7 7.png|Untitled 7 7.png]]
    
    ## Another example
    
    ![[Untitled 8 7.png|Untitled 8 7.png]]
    
    ![[Untitled 9 6.png|Untitled 9 6.png]]
    
    ![[Untitled 10 6.png|Untitled 10 6.png]]
    
    ![[Untitled 11 4.png|Untitled 11 4.png]]
    
    ![[Untitled 12 4.png|Untitled 12 4.png]]
    
    ![[Untitled 13 3.png|Untitled 13 3.png]]
    
    ![[Untitled 14 3.png|Untitled 14 3.png]]
    
- Trev Tutor