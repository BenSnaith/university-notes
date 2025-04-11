### Unit Outcomes

Here you will learn

 - How procedures, functions and methods are defined in different PLs
 - How these subprograms execute when they are called:
	 - How arguments are passed to them
	 - How results get passed back from them
	 - What other effects (i.e. side effects) the execution of a subprogram can have
	 - How exceptions affect subprogram execution

### The concept of a subprogram

 - **Rough definition**: subprogram = named program block that can be called from other program blocks

 - How do we "call" a subprogram?
 - How are values passed to and from a subprogram?
 - What constitutes a good subprogram?
 - How do subprograms help manage complex programming?

### The concept of a subprogram
#### Subprogram Abstraction

 - What does a subprogram hide and what does it emphasise?
 - Example:

```java
// clumsy, without the use of a subprogram:  
if ((ch >= ’A’ && ch <= ’Z’) || (ch >= ’a’ && ch <= ’z’)) {  
	System.out.println("A letter " + ch);  
}
```

vs.

```java
// subprograms can make programs more readable and maintainable:  
if (isLetter(ch)) {  
	System.out.println("A letter " + ch);  
}
```

#### Components of a Subprogram API

```java
e = queue1.pop();  
t = getCurrentTime();  
System.out.println(t + ": " + e);  
queue1.push(e+1);
```

 - Parameters
 - Global/External variables
 - Input/Output devices
 - Return value(s)

### Procedures and Functions

- **Procedure**: Emphasis on some effect other than returning a value, e.g. modifying variables

```cpp
i++;
new Board(i);
std::cout << i << '\n';
```

 - **Function**: Emphasis on returning a single result value

```cpp
list.get(0);
getTimeNow();
```

### Pure Procedures and Functions

 - **Pure Procedure**: achieve a single coherent goal and not return any values. Has no side effects.
 - **Pure Functions**: returning a value computed from the parameters, no other effect.

 - Why purity?
	 - Pure functions gives us referential transparency for free.
	 - Pure procedures don't have side effects.

#### Referential Transparency

A PL expression is **referentially transparent** if:

 - Replacing any function within it by its defining expression.
 - ...or a variable within it by its value
 - ...does not change its observable behaviour in any context.

Given the function `f()` defined below:

```cpp
int f(int a) { return a + a; }
```

Is the expression `f(g(x))` referentially transparent? Assume `x = 5`.

 - **Test 1**: is `f(g(x))` interchangeable with `g(x) + g(x)`?
 - **Test 2**: is `f(g(x))` interchangeable with `f(g(5))`?
 - Argue that the following expressions are not referentially transparent:

```cpp
f(x++);
f(list.remove(0));
f(getNanoSecondsSinceBoot());
```

#### Why is referential transparency good?

 - Referential Transparency expression can be easily optimised e.g., 

```cpp
2 + x + (4 * x) -> 2 + (5 * x)
```

 - Referential Transparency can be safely parallelised

#### Executing Subprograms

 - Subprogram execution generally requires the use of a Stack.

![[Pasted image 20250411184250.png]]

 - Every time a subprogram is called, an entry (containing the return address) is **pushed** on to the stack.
 - Upon complete of the called subprogram, the stack is **popped** and control is transferred to the return address in the popped stack.

#### Call Stack Demo 1

```cpp
#include <stdio.h>

int square(int y);

int main() {  
	for (int x = 1; x <= 10; x++) {  
		printf("%d ", square(x));  
	}  
	puts("");  
}

int square(int y) {  
	return y * y;  
}
```

#### Call Stack Demo 2

```cpp
#include <stdio.h>  

unsigned long long int factorial(unsigned int number);  

int main(void) {  
	for (unsigned int i = 0; i <= 21; ++i) {  
		printf("%u! = %llu\n", i, factorial(i));  
	}  
}  

// recursive definition of function factorial  
unsigned long long int factorial(unsigned int number) {  
	if (number <= 1) {// base case  
		return 1;  
	}  
	else { // recursive step  
		return (number * factorial(number - 1));  
	}  
}
```

#### Exception Propagation

![[Pasted image 20250411190040.png]]

![[Pasted image 20250411190103.png]]

![[Pasted image 20250411190116.png]]

### Parameter Passing

![[Pasted image 20250411190227.png]]

#### Matching formal and actual parameters

![[Pasted image 20250411190330.png]]

#### Parameters passing mechanisms

 - **Copy parameter passing mechanisms**
	 - Formal parameter = special local variable
	 - Value is copied from (sometimes to) the actual parameter
 - **Reference parameter passing mechanisms
	 - Formal and actual parameter are aliasing, i.e. sharing the same reference (i.e. memory location)
	 - (formal parameter = actual parameter) during a call
	 - No copying of value required - value is shared

#### Value Parameters

- Also known as **copy-in parameter**

![[Pasted image 20250411191558.png]]

 - The actual parameter can be any expression

#### Value Parameters - with Reference Semantics

![[Pasted image 20250411191727.png]]

![[Pasted image 20250411191828.png]]

#### Result Parameter

 - Also known as **copy-out parameter**

![[Pasted image 20250411191923.png]]

 - The actual parameter has to be variable

#### Value-Result Parameter

 - Also known as **copy-in-copy-out parameter**

![[Pasted image 20250411192027.png]]

 - The actual parameter has to be variable

#### Reference Parameter Passing

![[Pasted image 20250411192119.png]]

 - The actual parameter must be variable
 - The formal parameter = the actual parameter variable

