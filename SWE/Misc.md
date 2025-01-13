Q: When should you use assert

Assertions should be used in these key scenarios:

1. Internal Invariants
```java
public class BinaryTree {
    private Node root;
    
    private void checkBalance() {
        assert isBalanced(root) : "Tree became unbalanced after operation";
    }
}
```

2. Class Invariants
```java
public class Stack {
    private int size;
    private int[] elements;
    
    public void push(int item) {
        assert size < elements.length : "Stack overflow";
        elements[size++] = item;
        assert size <= elements.length : "Size exceeded capacity";
    }
}
```

3. Control Flow Assumptions
```java
switch (direction) {
    case NORTH: // handle north
        break;
    case SOUTH: // handle south
        break;
    default:
        assert false : "Unexpected direction: " + direction;
}
```

4. Private Method Preconditions
```java
private void sortRange(int[] array, int start, int end) {
    assert start >= 0 : "Start index must be non-negative";
    assert end <= array.length : "End index out of bounds";
    assert start <= end : "Invalid range";
    // sorting logic
}
```

Avoid using for:
```java
// Wrong: Public method parameter validation
public void setAge(int age) {
    assert age > 0; // Use if/throw instead
    this.age = age;
}

// Wrong: User input validation
String userInput = scanner.nextLine();
assert userInput != null; // Use explicit checks instead
```