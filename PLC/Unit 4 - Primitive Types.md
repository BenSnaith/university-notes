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
- anything non-zero is considered true.

