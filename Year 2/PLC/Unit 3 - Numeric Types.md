### Unit Outcomes

- About different ways to write numeric expressions.
- About different numeric types and operations built-in and definable across PLs.
- How to detect numerical errors specific to CPU Integers and floating-point numbers.

### CPU Numbers - Integers

- Integer Overflow in __Java__.

```java
int i = 2147483647;

i += 2;

System.out.println(i); // prints -2147483647
```

- __NOTE:__ There is no underflow among integers.

- Overflow is NOT detected by default by most PLs.
- Programmers are expected to handle it themselves.

### CPU Numbers - Miniature Numbers

![[Pasted image 20250204131414.png]]

### CPU Numbers - Floats

```java
double tiny = 1.0E-100;
double huge = 1.0E+100;

System.out.println(tiny * tiny);
```

- Output => 0; the exponent of tiny is too small.
- This is an example of __underflow__.

```java
double tiny = 1.0E-100;
double huge = 1.0E+100;

System.out.println(huge * huge * tiny);
```

- Output => -ve / +ve infinity.
- Because the positive exponent of huge is too large.
- This is an example of __overflow__.

```java
double tiny = 1.0E-100;
double huge = 1.0E+100;

System.out.println(huge * tiny * huge);
```

- Output => 1.0E200 (Correct!)
- __NO__ overflow or underflow.
- This shows that order matters.

```java
double tiny = 1.0E-100;
double huge = 1.0E+100;

System.out.println(huge == tiny + huge);
```

- Output => True 
- This is incorrect because the least significant digits are wrong.
- This is an example of a __rounding__ problem.

![[Pasted image 20250204133044.png]]

### Expressions (are trees)

![[Pasted image 20250204133202.png]]

- How will such trees be communicated to the computer?
- How will the computer evaluate the trees?

### Expressions in PLs

```java
(-b + Math.sqrt(Math.pow(b, 2) - 4 * a * c)) / (2 * a); // Java
```

```ada

```

```haskell

```

### Expression notes

- Automatic conversion.
- BIDMAS operations precedence.
- Algebraic laws.

### Numeric Types - C/C++ - CPU-level efficiency

- char, short, int, long:
	- Size not defined by language, depends on CPU/OS/Compiler
	- Signed and unsigned versions, e.g. signed long, unsigned long
	- Overflows ignored.
- float, double, long double
	- Range and precision depend on CPU type.
	- Rounding, infinity, and NaN behaviour depend on CPU type.

### Numeric Types - Java

- Defined by __language__, not the OS/CPU/Compiler

![[Pasted image 20250204134748.png]]

### Numeric Types - Ada

![[Pasted image 20250204134920.png]]

![[Pasted image 20250204134937.png]]

### Numeric Types - Haskell, Lisp, Python

![[Pasted image 20250204135018.png]]

