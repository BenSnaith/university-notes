### Unit Objective

- How Booleans, Characters and Symbolic Values conceptually enrich programming.
- How these values and their types are modelled in C, Java, Haskell and Lisp.
- About PL facilities for converting between primitive values and text strings.

### Primitive Types and Values in C/C++
##### C/C++ Booleans

- Booleans were an afterthought in C.
- They did not exist in the original version and were added later.
- Using Boolean in C requires importing the `<stdbool.h>` header.

```C
#include <stdio.h>
#include <stdbool.h>

int main()
{
	bool isPLCCool = false;

	bool areQuizzesFun = false;

	printf("%d\n", isPLCCool); // returns 0 - false
	
	printf("%d\n", areQuizzesFun); // returns 0 - false

	return 0;
}
```

- `bool` is just an `int` type "under-the-hood".
- anything non-zero is considered true, this is like "truthy" values in JS.

##### String Formatting

![[Pasted image 20250217102922.png]]

##### Booleans and Characters in Java

![[Pasted image 20250217103101.png]]

##### Enumerated types in C/C++ and Java

![[Pasted image 20250217103143.png]]

![[Pasted image 20250217103217.png]]

![[Pasted image 20250217103255.png]]

- Basically in C, enums are integers, there are enumerated haha.
- Whereas in Java each enum type on the enum class is its own class.

##### Enumerated types in JavaScript

- There is no explicit enumerated type in JS.
- The keyword `enum` exists, but is reserved for future use
- Several different ways of implementing enumerated types in JS, each with pros and cons
- We will discuss one of these.

- Defining enums as Object Keys
- Use an object to encapsulate an enum type and assign a key to each enum value.

```js
const HouseCategory = {
	DETACHED: "DETACHED",
	SEMIDETACHED: "SEMIDETACHED",
	TERRACE: "TERRACE"
}
```

##### Overview of Haskell primitive values

![[Pasted image 20250217103745.png]]

##### Formatting and parsing in Haskell

![[Pasted image 20250217104039.png]]

### Summary

- C:
	- Limited range of primitive values.
	- Much opportunity for errors to go undetected.
	- Formatting and parsing facilities limited.
- Java:
	- Safer due to a range of abstract values and types.
	- Good generic formatting mechanism.
	- No generic parsing mechanism.
- Haskell:
	- Symbolic primitive values for an purpose, typed.
	- Excellent type-checking improves safety.