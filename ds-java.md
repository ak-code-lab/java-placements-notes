# Data Structures in Java

## What are Data Structures in Java?
Data structures in Java are used to store, manage, and manipulate data efficiently. Java provides built-in data structures through the **java.util** package, such as **ArrayList, LinkedList, and HashMap**.

## Why use Data Structures?
- Improve data organization and retrieval efficiency.
- Optimize performance for different operations (insertion, deletion, searching).
- Reduce memory usage and enhance program scalability.
- Provide ready-to-use implementations of common data structures.

## Where are Data Structures used?
- **Software development**: Managing collections of data efficiently.
- **Databases**: Storing and retrieving records in an organized manner.
- **Graphical applications**: Handling UI components dynamically.
- **Networking**: Managing and routing data efficiently.

---
## 1. ArrayList

### What is ArrayList?
`ArrayList` is a resizable array implementation of the `List` interface in Java. It allows dynamic resizing and provides fast random access.

### Syntax
```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<String> names = new ArrayList<>();
        names.add("Alice");
        names.add("Bob");
        names.add("Charlie");

        System.out.println(names.get(1)); // Output: Bob
    }
}
```

### Key Features:
- Allows duplicate elements.
- Maintains insertion order.
- Provides fast random access (O(1)).
- Slower insertions/deletions compared to `LinkedList`.

---
## 2. LinkedList

### What is LinkedList?
`LinkedList` is a doubly-linked list implementation of the `List` interface. It is efficient for insertions and deletions.

### Syntax
```java
import java.util.LinkedList;

public class Main {
    public static void main(String[] args) {
        LinkedList<Integer> numbers = new LinkedList<>();
        numbers.add(10);
        numbers.add(20);
        numbers.add(30);
        
        System.out.println(numbers.getFirst()); // Output: 10
    }
}
```

### Key Features:
- Elements are linked using pointers.
- Provides fast insertions and deletions (O(1) for adding/removing at ends).
- Slower random access compared to `ArrayList` (O(n)).
- Uses more memory due to extra node pointers.

---
## 3. HashMap

### What is HashMap?
`HashMap` is a key-value pair implementation of the `Map` interface. It allows fast data retrieval using hashing.

### Syntax
```java
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        HashMap<String, Integer> ages = new HashMap<>();
        ages.put("Alice", 25);
        ages.put("Bob", 30);
        ages.put("Charlie", 22);
        
        System.out.println(ages.get("Bob")); // Output: 30
    }
}
```

### Key Features:
- Stores data in key-value pairs.
- Provides fast lookup (O(1) in average case).
- Keys are unique; values can be duplicate.
- Does not maintain insertion order.

---
## Practice Questions
1. What is the difference between `ArrayList` and `LinkedList`?
2. How does `HashMap` store key-value pairs internally?
3. Implement a Java program that demonstrates inserting and removing elements from a `LinkedList`.
4. Write a program that counts word occurrences in a sentence using `HashMap`.
5. When should you use an `ArrayList` over a `LinkedList` and vice versa?

