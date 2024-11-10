- Support Video Notes
    
    A matrix is an ordered array of values, and matrices are just the plural of a matrix.
    
    The orientation of a matrix matters:
    
    [ 6 8 ]
    
    [ 3 1 ] [ 6 3 9 1 ]
    
    [ 9 4 ] [ 8 1 4 9 ]
    
    [ 1 9 ]
    
    These two matrices are not the same, the order of values within a matrix matters:
    
    [ 6 8 ] [ 6 8 ]
    
    [ 3 1 ] [ 9 1 ]
    
    [ 9 4 ] [ 3 4 ]
    
    [ 1 9 ] [ 1 9 ]
    
    The two are not the same.
    
    [ 6 10 7 ]
    
    [ 9 19 1 ]
    
    [ 4 26 3 ]
    
    [ 0 17 8 ]
    
    This matrix has four rows and three columns and would therefore be referred to as a 4 x 3 matrix.
    
    This is a 2 x 5 matrix
    
    [ 6 2 7 4 2 ]
    
    [ 8 1 4 9 2 ]
    
    Matrices with only one column are called vectors
    
    [ 6 ]
    
    [ 9 ]
    
    [ 4 ]
    
    [ 0 ]
    
    This is a vector of size four.
    
    To refer to a specific element within a matrix we much use the coordinates
    
    1 2 3
    
    1 [ 6 10 7 ]
    
    2 [ 9 19 1 ]
    
    3 [ 4 26 3 ]
    
    4 [ 0 17 8 ]
    
    So for this matrix M, if we wanted to access the entry 26 we would use the coordinates 3,2 (row, then column)
    
    M$_3,$﻿$_2$﻿ = 26
    
    A matrix is just a means of representing data, very much like an array, also like an array, operations can be performed on a matrix or on a combination of matrices to manipulate it.
    
    One such operation is **Transposition**, Transposition occurs in such as way that rows become columns and columns become rows
    
    [ 10 20 30 ] [ 10 40 ]
    
    [ 40 50 60 ] [ 20 50 ]
    
    [ 30 60 ]
    
    **Scalar Multiplication (think scalable)** involves multiplying each value in a matrix by some other value. if we have this matrix M.
    
    [ 1 2 3 ]
    
    [ 2 0 1 ]
    
    If we want to establish 3M, everything is multiplied by three
    
    [ 3 6 9 ]
    
    [ 6 0 3 ]
    
    We can perform **Addition** of two or more matrices as long as they are of the same dimensions
    
    [ 6 8 ] + [ 8 7 ] = [ 14 15 ]
    
    [ 3 4 ] + [ 9 6 ] = [ 12 10 ]
    
    **Matrix Multiplication** is a little more involved, when multiplying two matrices, the number of columns in A needs to be equal to the number of rows in B
    
    [ 1 9 ]
    
    [ 4 8 3 ] * [ 6 8 ] = [ 58 115 ]
    
    [ 2 5 ]
    
    We first multiply row 1 of A with column 1 of B, so we do:
    
    4 x 1 + 8 x 6 + 3 x 2 = 58
    
    And then do the same with the second row.
    
    Additional rows in our first matrix would result in additional rows in our result matrix, additional columns in our second matrix would result in addition columns in our results matrix.
    
    For a **Dot Product**, we take two vectors of equal length and get the output of a single value
    
    [ 1 ] [ 5 ]
    
    [ 2 ] [ 6 ]
    
    [ 3 ] [ 7 ]
    
    [ 4 ] [ 8 ]
    
    Each result is first multiplied
    
    1 x 5 = 5
    
    2 x 6 = 12
    
    3 x 7 = 21
    
    4 x 8 = 32
    
    Then add them all together, which is 70.
    
- Lecture (Richard)
    
    Matrices and Vectors
    
    **Matrix**
    
    Each value in a matrix is called an entry, numbers can be repeated, the order and the orientation is very important
    
    They are arranged in rows and columns: R x C e.g 5 x 3
    
    ![[Untitled 24.png|Untitled 24.png]]
    
    If this matrix were named M, the zero would be found at:
    
    M$_4,$﻿$_3$﻿
    
    Note that the first row and column are named starting with 1, not 0
    
    **Vector**
    
    A column vector is a matrix with a single column, same goes for a row vector
    
    V$_n$﻿ = position of number
    
    **Matrix vs Array**
    
    A matrix is a mathematical principle and an array is a data structure, such as how a number is a mathematical principle and an integer variable is a data structure, be that much smaller.
    
    **Transposition M****$^T$**﻿
    
    - Rows become columns, columns become rows.
    
    ![[Untitled 1 13.png|Untitled 1 13.png]]
    
    This is an example of transposition, any matrix can be transposed.
    
    We do this so we can organise the same data in different ways.
    
    **Why care?**
    
    - Image processing
    - Signal processing
    - As an intermediate step to something else
    
    **Transposition is NOT ROTATION**
    
    ![[Untitled 2 13.png|Untitled 2 13.png]]
    
    **Transposition**
    
    ![[Untitled 3 11.png|Untitled 3 11.png]]
    
    **Scalar Multiplication (Scalable)**
    
    - Each entry in the matrix is multiplied by a single value
    
    ![[Untitled 4 10.png|Untitled 4 10.png]]
    
    ![[Untitled 5 10.png|Untitled 5 10.png]]
    
    ![[Untitled 6 7.png|Untitled 6 7.png]]
    
    ![[Untitled 7 6.png|Untitled 7 6.png]]
    
    **Why do we care?**
    
    Take a matrix of quiz scores for example, say there are 10 scores, if we want to only use the top 8 we could multiply the whole matrix by an amount to get this value
    
    **Geometric Applications**
    
    - Scaling of a shape can be achieved via scalar multiplication
    
    ![[Untitled 8 6.png|Untitled 8 6.png]]
    
    Everything has doubled, the width, height and distance from the origin
    
    - More likely format (specifying bottom-left and width/height
    
    ![[Untitled 9 5.png|Untitled 9 5.png]]
    
    **Addition**
    
    - Addition is only possible with two matrices of the same width and height (look the same)
    
    ![[Untitled 10 5.png|Untitled 10 5.png]]
    
    **Applications of matrix addition**
    
    - Stat analysis
    - Cryptography
    - Games development
    - 3D Modelling
    - Machine leaning
    
    **Geometric Applications**
    
    ![[Untitled 11 3.png|Untitled 11 3.png]]
    
    **Dot Production**
    
    - Applied to two vectors to get a single value
    - Each pair is multiplied, and these individual results are added, they must be the same size
    
    ![[Untitled 12 3.png|Untitled 12 3.png]]
    
    **Multiplication**
    
    Width of the first must be the same as the height of the second
    
    ![[Untitled 13 2.png|Untitled 13 2.png]]
    
    ![[Untitled 14 2.png|Untitled 14 2.png]]
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    
      
    

4

6

12

2

  

  

  

  

2 x 2 2 x 2

2 x 2 = 4

3 x 1 = 3

  

2 x 4 = 8

3 x 6 = 18