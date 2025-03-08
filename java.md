# Java Introduction

## What is Java?
Java is a high-level, class-based, object-oriented programming language designed to have as few implementation dependencies as possible. It was developed by James Gosling at Sun Microsystems (now owned by Oracle) and released in 1995. Java is known for its "write once, run anywhere" (WORA) principle, meaning that compiled Java code can run on all platforms that support Java without recompilation.

## How Java Works
Java works through a unique compilation and execution process:

1. **Write Code**: Developers write Java code in `.java` files.
2. **Compilation**: The Java compiler (`javac`) compiles the source code into bytecode stored in `.class` files.
3. **JVM Execution**: The Java Virtual Machine (JVM) loads, verifies, and executes the bytecode.
4. **Platform Independence**: The JVM acts as an intermediary between the bytecode and the operating system, allowing Java programs to run on any device with a JVM installed.

This architecture gives Java several advantages:
- **Platform Independence**: Java programs run on any platform with a compatible JVM.
- **Security**: The JVM provides a sandbox environment that restricts the program's access to system resources.
- **Automatic Memory Management**: The JVM includes a garbage collector that automatically manages memory.

## JDK and its Components
The Java Development Kit (JDK) is a software development environment used for developing Java applications. The key components include:

1. **Java Runtime Environment (JRE)**: Contains the JVM, class libraries, and other components needed to run Java applications.
   
2. **Development Tools**:
   - **javac**: The Java compiler that converts source code to bytecode.
   - **java**: The Java launcher that runs Java applications.
   - **javadoc**: Generates HTML documentation from Java source code.
   - **jar**: Archives Java files into a single file.
   - **javap**: Disassembles class files.

3. **Java API**: A collection of pre-written packages, classes, and interfaces with their respective methods.

4. **Debugging Tools**: Tools for finding and fixing bugs in Java applications.

## First Java Program

### Syntax
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### Explanation:
- `public class HelloWorld`: Declares a public class named HelloWorld. The class name must match the filename (HelloWorld.java).
- `public static void main(String[] args)`: The main method, which is the entry point of the program.
- `System.out.println("Hello, World!")`: Prints "Hello, World!" to the console.

### Steps to Run:
1. Save the code in a file called `HelloWorld.java`.
2. Compile it with: `javac HelloWorld.java`.
3. Run it with: `java HelloWorld`.

## Variables and Data Types in Java

### What are Variables?
Variables are containers for storing data values. In Java, all variables must be declared before use.

### Variable Declaration Syntax:
```java
dataType variableName = value;
```

### Primitive Data Types
Java has eight primitive data types:

1. **byte**: 8-bit integer (-128 to 127)
   ```java
   byte myByte = 100;
   ```

2. **short**: 16-bit integer (-32,768 to 32,767)
   ```java
   short myShort = 5000;
   ```

3. **int**: 32-bit integer (-2^31 to 2^31-1)
   ```java
   int myInt = 100000;
   ```

4. **long**: 64-bit integer (-2^63 to 2^63-1)
   ```java
   long myLong = 15000000000L;  // Note the 'L' suffix
   ```

5. **float**: 32-bit floating point number
   ```java
   float myFloat = 5.75f;  // Note the 'f' suffix
   ```

6. **double**: 64-bit floating point number
   ```java
   double myDouble = 19.99;
   ```

7. **boolean**: true or false
   ```java
   boolean isJavaFun = true;
   ```

8. **char**: 16-bit Unicode character
   ```java
   char myLetter = 'A';
   ```

### Reference Data Types
Reference data types include:

1. **String**: A sequence of characters
   ```java
   String greeting = "Hello World";
   ```

2. **Arrays**: Collection of similar data types
   ```java
   int[] numbers = {1, 2, 3, 4, 5};
   ```

3. **Classes**: Blueprint for creating objects
   ```java
   MyClass myObject = new MyClass();
   ```

4. **Interfaces**: Abstract type used to specify behavior for classes

### Variable Naming Rules:
- Names must start with a letter, underscore (_), or dollar sign ($).
- Names cannot contain spaces.
- Names cannot be Java keywords.
- Names are case-sensitive (age and Age are different variables).

### Examples of Variable Usage

#### Example 1: Working with different data types
```java
public class VariableExample {
    public static void main(String[] args) {
        // Integer variables
        int age = 25;
        
        // Double variables for precise calculations
        double price = 19.99;
        
        // Character variable
        char grade = 'A';
        
        // Boolean variable
        boolean isActive = true;
        
        // String variable (not primitive)
        String name = "John Doe";
        
        // Output all variables
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Price: $" + price);
        System.out.println("Grade: " + grade);
        System.out.println("Active status: " + isActive);
    }
}
```

#### Example 2: Type conversion and casting
```java
public class TypeConversion {
    public static void main(String[] args) {
        // Implicit conversion (widening)
        int intValue = 100;
        long longValue = intValue; // Automatic conversion from int to long
        float floatValue = longValue; // Automatic conversion from long to float
        
        System.out.println("Int value: " + intValue);
        System.out.println("Long value: " + longValue);
        System.out.println("Float value: " + floatValue);
        
        // Explicit conversion (narrowing) - requires casting
        double doubleValue = 9.78;
        int narrowedValue = (int) doubleValue; // Manual casting from double to int
        
        System.out.println("Double value: " + doubleValue);
        System.out.println("Narrowed to int: " + narrowedValue); // Output will be 9 (decimal part is truncated)
    }
}
```

## Practice Questions

1. **Basic Variable Declaration**: Write a Java program that declares variables for a person's name, age, height (in meters), and whether they are a student. Print all these details in a formatted way.

2. **Type Conversion**: Write a Java program that demonstrates both implicit and explicit type conversion. Include conversions between numeric data types and explain what happens when converting from larger to smaller data types.

3. **Calculate Average**: Write a Java program that calculates and displays the average of five floating-point numbers. Use appropriate variable declarations and formatting.

4. **Memory Usage**: Write a Java program that prints the memory size (in bytes) of each primitive data type using the `Byte.SIZE`, `Short.SIZE`, etc. constants.

5. **String Manipulation**: Create a Java program that declares a String variable with your full name, and then:
   - Print the length of the string
   - Convert it to uppercase and print
   - Extract and print your first name only
   - Check if your name contains the letter 'a'

# Java Comments, Output, Type Casting, and Operators

## Comments in Java

### What are Comments?
Comments are explanatory text that are ignored by the compiler. They are used to make code more readable and to provide information about the code to other developers.

### Why use Comments?
- Document your code for others (and your future self)
- Explain complex algorithms or logic
- Temporarily disable code during debugging
- Generate documentation with tools like Javadoc

### Where to use Comments?
- Before methods to explain functionality
- Alongside complex code segments
- At the beginning of a class to explain its purpose
- Before variables that need explanation

### Types of Comments and Syntax

#### 1. Single-line Comments
Used for brief explanations on a single line.
```java
// This is a single-line comment
int x = 10; // This initializes variable x to 10
```

#### 2. Multi-line Comments
Used for explanations that span multiple lines.
```java
/* This is a multi-line comment
   that spans across
   several lines */
```

#### 3. Documentation Comments (Javadoc)
Used to generate API documentation.
```java
/**
 * This is a documentation comment
 * @author Your Name
 * @param args command line arguments
 * @return void
 */
public static void main(String[] args) {
    // Method body
}
```

### Examples

#### Example 1: Using different types of comments
```java
// Program to demonstrate various comment types in Java

public class CommentDemo {
    /**
     * The main method is the entry point of the application
     * @param args command line arguments
     */
    public static void main(String[] args) {
        // Declaring and initializing a variable
        int sum = 0;
        
        /* This block calculates the sum
           of numbers from 1 to 5 */
        for (int i = 1; i <= 5; i++) {
            sum += i; // Adding the current number to sum
        }
        
        // Displaying the result
        System.out.println("Sum: " + sum);
    }
}
```

#### Example 2: Using comments for code documentation
```java
/**
 * Calculator class provides basic arithmetic operations
 * @author Your Name
 * @version 1.0
 */
public class Calculator {
    /**
     * Adds two numbers and returns the result
     * @param a first number
     * @param b second number
     * @return sum of a and b
     */
    public int add(int a, int b) {
        return a + b; // Return the sum
    }
    
    // Other calculator methods could be implemented here
}
```

## Output in Java

### What is Output?
Output refers to the process of displaying or writing data from a program to an external device like a console, file, or network.

### Why use Output?
- Display results to users
- Debug programs
- Log program activities
- Communicate with other systems

### Where to use Output?
- To show the results of calculations
- For user interaction
- During debugging
- To log program execution
- To write data to files

### Output Methods and Syntax

#### 1. System.out.println()
Prints the argument and then terminates the line.
```java
System.out.println("Hello, World!");
```

#### 2. System.out.print()
Prints the argument but does not terminate the line.
```java
System.out.print("Hello, ");
System.out.print("World!");
// Output: Hello, World!
```

#### 3. System.out.printf()
Provides formatted output using format specifiers.
```java
System.out.printf("Name: %s, Age: %d, Height: %.2f", "John", 25, 1.75);
// Output: Name: John, Age: 25, Height: 1.75
```

### Common Format Specifiers
- `%s` - String
- `%d` - Integer (decimal)
- `%f` - Floating point
- `%c` - Character
- `%b` - Boolean
- `%.2f` - Float with 2 decimal places
- `%n` - New line

### Examples

#### Example 1: Basic output methods
```java
public class OutputDemo {
    public static void main(String[] args) {
        // Using println
        System.out.println("Line 1");
        System.out.println("Line 2");
        
        // Using print
        System.out.print("This will ");
        System.out.print("be on the same line.");
        System.out.println(); // New line
        
        // Using printf for formatted output
        String name = "Alice";
        int age = 30;
        double height = 1.65;
        System.out.printf("Name: %s, Age: %d, Height: %.2f meters%n", name, age, height);
    }
}
```

#### Example 2: Advanced formatted output
```java
public class FormattedOutputDemo {
    public static void main(String[] args) {
        // Table formatting
        System.out.println("Product Details:");
        System.out.printf("%-15s %-10s %s%n", "Product", "Price", "Quantity");
        System.out.printf("%-15s $%-9.2f %d%n", "Laptop", 1299.99, 5);
        System.out.printf("%-15s $%-9.2f %d%n", "Mouse", 24.99, 10);
        System.out.printf("%-15s $%-9.2f %d%n", "Keyboard", 49.99, 8);
        
        // Date formatting
        System.out.printf("%nToday is %tB %<te, %<tY%n", new java.util.Date());
        
        // Number formatting
        double number = 12345.6789;
        System.out.printf("Number formatting: %,.2f%n", number);
    }
}
```

## Type Casting in Java

### What is Type Casting?
Type casting is the process of converting a variable from one data type to another. In Java, there are two types of casting: implicit (automatic) and explicit (manual).

### Why use Type Casting?
- To convert between compatible data types
- To perform operations between different data types
- To store results in variables of different types
- To use library functions that require specific data types

### Where to use Type Casting?
- When performing arithmetic with mixed data types
- When storing a value in a variable of a different type
- When passing arguments to methods expecting different types
- When returning values from methods

### Types of Type Casting

#### 1. Implicit Casting (Widening)
Automatic conversion from smaller to larger data types.
```java
int myInt = 9;
double myDouble = myInt; // Automatic casting: int to double
```

Widening casting is done automatically when:
- byte → short → int → long → float → double

#### 2. Explicit Casting (Narrowing)
Manual conversion from larger to smaller data types.
```java
double myDouble = 9.78;
int myInt = (int) myDouble; // Manual casting: double to int
```

Narrowing casting must be done manually when:
- double → float → long → int → short → byte

### Examples

#### Example 1: Implicit and explicit casting
```java
public class TypeCastingDemo {
    public static void main(String[] args) {
        // Implicit casting (widening)
        byte byteValue = 100;
        short shortValue = byteValue;  // byte to short
        int intValue = shortValue;     // short to int
        long longValue = intValue;     // int to long
        float floatValue = longValue;  // long to float
        double doubleValue = floatValue; // float to double
        
        System.out.println("Implicit Casting Example:");
        System.out.println("byte value: " + byteValue);
        System.out.println("short value: " + shortValue);
        System.out.println("int value: " + intValue);
        System.out.println("long value: " + longValue);
        System.out.println("float value: " + floatValue);
        System.out.println("double value: " + doubleValue);
        
        // Explicit casting (narrowing)
        double doubleNum = 9.78;
        float floatNum = (float) doubleNum;    // double to float
        long longNum = (long) floatNum;        // float to long
        int intNum = (int) longNum;           // long to int
        short shortNum = (short) intNum;      // int to short
        byte byteNum = (byte) shortNum;       // short to byte
        
        System.out.println("\nExplicit Casting Example:");
        System.out.println("double value: " + doubleNum);
        System.out.println("float value: " + floatNum);
        System.out.println("long value: " + longNum);
        System.out.println("int value: " + intNum);
        System.out.println("short value: " + shortNum);
        System.out.println("byte value: " + byteNum);
    }
}
```

#### Example 2: Type casting with potential data loss
```java
public class DataLossDemo {
    public static void main(String[] args) {
        // Integer overflow example
        int largeValue = 130;
        byte smallByte = (byte) largeValue;
        
        System.out.println("Original int value: " + largeValue);
        System.out.println("After casting to byte: " + smallByte); // Data loss due to overflow
        
        // Decimal truncation
        double pi = 3.14159;
        int iPi = (int) pi;
        
        System.out.println("Original double value: " + pi);
        System.out.println("After casting to int: " + iPi); // Decimal part is truncated
        
        // String to numeric conversion
        String numberString = "123";
        int number = Integer.parseInt(numberString); // Convert String to int
        double doubleNumber = Double.parseDouble("456.789"); // Convert String to double
        
        System.out.println("String to int: " + number);
        System.out.println("String to double: " + doubleNumber);
    }
}
```

## Operators in Java

### What are Operators?
Operators are special symbols that perform operations on operands (variables and values).

### Why use Operators?
- Perform arithmetic calculations
- Make comparisons between values
- Perform logical operations
- Assign values to variables
- Perform bitwise operations

### Where to use Operators?
- In mathematical calculations
- In decision-making statements (if, switch)
- In loops (for, while)
- For string concatenation
- In complex expressions and algorithms

### Types of Operators and Syntax

#### 1. Arithmetic Operators
Perform basic mathematical operations.
```java
int a = 10, b = 5;
System.out.println(a + b);  // Addition: 15
System.out.println(a - b);  // Subtraction: 5
System.out.println(a * b);  // Multiplication: 50
System.out.println(a / b);  // Division: 2
System.out.println(a % b);  // Modulus (remainder): 0
```

#### 2. Assignment Operators
Assign values to variables.
```java
int x = 10;          // Simple assignment
x += 5;              // x = x + 5; (15)
x -= 3;              // x = x - 3; (12)
x *= 2;              // x = x * 2; (24)
x /= 4;              // x = x / 4; (6)
x %= 4;              // x = x % 4; (2)
```

#### 3. Comparison Operators
Compare two values.
```java
int a = 10, b = 5;
System.out.println(a == b); // Equal to: false
System.out.println(a != b); // Not equal to: true
System.out.println(a > b);  // Greater than: true
System.out.println(a < b);  // Less than: false
System.out.println(a >= b); // Greater than or equal to: true
System.out.println(a <= b); // Less than or equal to: false
```

#### 4. Logical Operators
Perform logical "AND", "OR" and "NOT" operations.
```java
boolean x = true, y = false;
System.out.println(x && y); // Logical AND: false
System.out.println(x || y); // Logical OR: true
System.out.println(!x);     // Logical NOT: false
```

#### 5. Bitwise Operators
Perform operations on individual bits.
```java
int a = 5;  // binary: 101
int b = 3;  // binary: 011
System.out.println(a & b);  // Bitwise AND: 1
System.out.println(a | b);  // Bitwise OR: 7
System.out.println(a ^ b);  // Bitwise XOR: 6
System.out.println(~a);     // Bitwise NOT: -6
System.out.println(a << 1); // Left shift: 10
System.out.println(a >> 1); // Right shift: 2
```

#### 6. Unary Operators
Perform operations on a single operand.
```java
int a = 10;
System.out.println(+a);    // Unary plus: 10
System.out.println(-a);    // Unary minus: -10
System.out.println(++a);   // Pre-increment: 11
System.out.println(a++);   // Post-increment: 11 (a becomes 12)
System.out.println(--a);   // Pre-decrement: 11
System.out.println(a--);   // Post-decrement: 11 (a becomes 10)
System.out.println(!true); // Logical complement: false
```

#### 7. Ternary Operator
Shorthand for if-then-else statement.
```java
int age = 20;
String status = (age >= 18) ? "Adult" : "Minor";
System.out.println(status); // Output: Adult
```

### Examples

#### Example 1: Arithmetic and assignment operators
```java
public class OperatorDemo {
    public static void main(String[] args) {
        // Arithmetic operators
        int a = 10, b = 3;
        System.out.println("Arithmetic Operations:");
        System.out.println("a + b = " + (a + b));
        System.out.println("a - b = " + (a - b));
        System.out.println("a * b = " + (a * b));
        System.out.println("a / b = " + (a / b));  // Integer division
        System.out.println("a % b = " + (a % b));
        
        // Division with different data types
        System.out.println("10.0 / 3 = " + (10.0 / 3)); // Double division
        
        // Assignment operators
        int x = 10;
        System.out.println("\nAssignment Operations:");
        System.out.println("Original x: " + x);
        
        x += 5;  // x = x + 5
        System.out.println("After x += 5: " + x);
        
        x -= 3;  // x = x - 3
        System.out.println("After x -= 3: " + x);
        
        x *= 2;  // x = x * 2
        System.out.println("After x *= 2: " + x);
        
        x /= 6;  // x = x / 6
        System.out.println("After x /= 6: " + x);
        
        x %= 2;  // x = x % 2
        System.out.println("After x %= 2: " + x);
    }
}
```

#### Example 2: Comparison, logical, and ternary operators
```java
public class LogicalOperatorDemo {
    public static void main(String[] args) {
        int age = 25;
        int income = 50000;
        
        // Comparison operators
        System.out.println("Comparison Operations:");
        System.out.println("age > 18: " + (age > 18));
        System.out.println("age == 25: " + (age == 25));
        System.out.println("income < 30000: " + (income < 30000));
        
        // Logical operators
        System.out.println("\nLogical Operations:");
        boolean hasHighIncome = income > 45000;
        boolean isAdult = age >= 18;
        
        System.out.println("Is adult with high income: " + (isAdult && hasHighIncome));
        System.out.println("Is adult OR has high income: " + (isAdult || hasHighIncome));
        System.out.println("Is not adult: " + (!isAdult));
        
        // Complex condition
        boolean isEligible = (age >= 18 && age <= 65) && income >= 30000;
        System.out.println("Is eligible for loan: " + isEligible);
        
        // Ternary operator
        System.out.println("\nTernary Operation:");
        String status = (age >= 18) ? "Adult" : "Minor";
        System.out.println("Age status: " + status);
        
        int max = (a > b) ? a : b;
        System.out.println("Maximum of " + a + " and " + b + " is: " + max);
        
        // Nested ternary
        String ageCategory = (age < 18) ? "Minor" : (age < 65) ? "Adult" : "Senior";
        System.out.println("Age category: " + ageCategory);
    }
}
```

## Practice Questions

1. **Comments Usage**: Write a Java program that includes all three types of comments (single-line, multi-line, and documentation). The program should include comments explaining a simple calculator function that adds two numbers.

2. **Formatted Output**: Write a Java program that calculates the area and perimeter of a rectangle. Use `System.out.printf()` to display the results with 2 decimal places in a well-formatted table.

3. **Type Casting**: Create a Java program that demonstrates both widening and narrowing conversions. Include examples of potential data loss and how to handle it. Also, convert a string to an integer and a double.

4. **Operator Precedence**: Write a Java program that demonstrates operator precedence with complex mathematical expressions. Include examples with parentheses to change the natural order of operations.

5. **Calculator Application**: Create a simple calculator application that takes two numbers and an operator (+, -, *, /, %) as input. Use appropriate operators to perform calculations and display the result. Make sure to handle potential errors like division by zero.

# Java Strings and Math Class

## Strings in Java

### What is a String?
In Java, a String is a sequence of characters. It is not a primitive data type like int or char; instead, it's an object of the class `java.lang.String`. Strings are immutable, which means once created, their values cannot be changed.

### Why use Strings?
- To store and manipulate text data
- To represent names, messages, addresses, etc.
- To read and write text from/to files, console, or network
- To parse and process textual information

### Where to use Strings?
- User interface elements (labels, messages)
- File I/O operations
- Data parsing and manipulation
- Network communication
- Database operations

### String Creation and Syntax

#### Creating Strings
```java
// String literal (preferred way)
String str1 = "Hello World";

// Using new keyword
String str2 = new String("Hello World");
```

### Common String Methods

1. **length()**: Returns the length of the string.
   ```java
   String text = "Hello";
   int length = text.length(); // Returns 5
   ```

2. **charAt(int index)**: Returns the character at specified index.
   ```java
   char c = text.charAt(1); // Returns 'e'
   ```

3. **substring(int beginIndex)**: Returns substring from beginIndex to the end.
   ```java
   String sub = text.substring(2); // Returns "llo"
   ```

4. **substring(int beginIndex, int endIndex)**: Returns substring from beginIndex to endIndex-1.
   ```java
   String sub = text.substring(1, 4); // Returns "ell"
   ```

5. **concat(String str)**: Concatenates specified string to the end.
   ```java
   String newText = text.concat(" World"); // Returns "Hello World"
   ```

6. **indexOf(String str)**: Returns index of first occurrence of specified string.
   ```java
   int index = "Hello World".indexOf("World"); // Returns 6
   ```

7. **toLowerCase()** / **toUpperCase()**: Converts to lower/upper case.
   ```java
   String lower = text.toLowerCase(); // Returns "hello"
   String upper = text.toUpperCase(); // Returns "HELLO"
   ```

8. **trim()**: Removes whitespace from both ends.
   ```java
   String trimmed = "  Hello  ".trim(); // Returns "Hello"
   ```

9. **replace(char oldChar, char newChar)**: Replaces occurrences of oldChar with newChar.
   ```java
   String replaced = text.replace('e', 'a'); // Returns "Hallo"
   ```

10. **split(String regex)**: Splits string around matches of the regex.
    ```java
    String[] parts = "Hello,World".split(","); // Returns ["Hello", "World"]
    ```

11. **equals(Object obj)**: Compares string content.
    ```java
    boolean isEqual = text.equals("Hello"); // Returns true
    ```

12. **contains(CharSequence s)**: Checks if string contains the specified sequence.
    ```java
    boolean contains = text.contains("ell"); // Returns true
    ```

### String Concatenation
Strings can be concatenated using the + operator or concat() method.
```java
String firstName = "John";
String lastName = "Doe";

// Using + operator
String fullName = firstName + " " + lastName; // "John Doe"

// Using concat() method
String fullName2 = firstName.concat(" ").concat(lastName); // "John Doe"
```

### String vs StringBuilder vs StringBuffer

1. **String**: Immutable, thread-safe
   ```java
   String s = "Hello";
   s = s + " World"; // Creates a new String object
   ```

2. **StringBuilder**: Mutable, not thread-safe, more efficient for string manipulation
   ```java
   StringBuilder sb = new StringBuilder("Hello");
   sb.append(" World"); // Modifies the same object
   String result = sb.toString();
   ```

3. **StringBuffer**: Mutable, thread-safe, synchronized
   ```java
   StringBuffer sb = new StringBuffer("Hello");
   sb.append(" World"); // Thread-safe operation
   String result = sb.toString();
   ```

### Examples

#### Example 1: String methods demonstration
```java
public class StringMethodsDemo {
    public static void main(String[] args) {
        String text = "Java Programming";
        
        // Basic properties
        System.out.println("Original String: " + text);
        System.out.println("Length: " + text.length());
        
        // Case conversion
        System.out.println("Uppercase: " + text.toUpperCase());
        System.out.println("Lowercase: " + text.toLowerCase());
        
        // Character extraction
        System.out.println("Character at index 5: " + text.charAt(5));
        
        // Substring extraction
        System.out.println("Substring from index 5: " + text.substring(5));
        System.out.println("Substring from index 5 to 11: " + text.substring(5, 11));
        
        // Finding characters/substrings
        System.out.println("Index of 'Pro': " + text.indexOf("Pro"));
        System.out.println("Last index of 'a': " + text.lastIndexOf('a'));
        
        // Checking properties
        System.out.println("Starts with 'Java': " + text.startsWith("Java"));
        System.out.println("Ends with 'ming': " + text.endsWith("ming"));
        System.out.println("Contains 'gram': " + text.contains("gram"));
        
        // Replace operations
        System.out.println("Replace 'a' with 'o': " + text.replace('a', 'o'));
        System.out.println("Replace 'Programming' with 'Developer': " + 
                          text.replace("Programming", "Developer"));
        
        // Trimming
        String spacedText = "   Trimmed String   ";
        System.out.println("Before trim: '" + spacedText + "'");
        System.out.println("After trim: '" + spacedText.trim() + "'");
        
        // Splitting
        String csv = "apple,orange,banana,grape";
        String[] fruits = csv.split(",");
        System.out.println("Split CSV into array:");
        for (String fruit : fruits) {
            System.out.println("- " + fruit);
        }
    }
}
```

#### Example 2: String, StringBuilder, and StringBuffer comparison
```java
public class StringPerformanceDemo {
    public static void main(String[] args) {
        // Performance comparison for concatenation
        long startTime, endTime;
        
        // Using String concatenation
        startTime = System.currentTimeMillis();
        String str = "";
        for (int i = 0; i < 10000; i++) {
            str += i; // Creates a new String object in each iteration
        }
        endTime = System.currentTimeMillis();
        System.out.println("Time taken using String: " + (endTime - startTime) + "ms");
        
        // Using StringBuilder
        startTime = System.currentTimeMillis();
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < 10000; i++) {
            sb.append(i); // Modifies the same object
        }
        String result1 = sb.toString();
        endTime = System.currentTimeMillis();
        System.out.println("Time taken using StringBuilder: " + (endTime - startTime) + "ms");
        
        // Using StringBuffer
        startTime = System.currentTimeMillis();
        StringBuffer sbf = new StringBuffer();
        for (int i = 0; i < 10000; i++) {
            sbf.append(i); // Thread-safe operation
        }
        String result2 = sbf.toString();
        endTime = System.currentTimeMillis();
        System.out.println("Time taken using StringBuffer: " + (endTime - startTime) + "ms");
        
        // Demonstrating common operations
        StringBuilder builder = new StringBuilder("Hello");
        System.out.println("\nStringBuilder operations:");
        System.out.println("Original: " + builder);
        
        // Append operation
        builder.append(" World");
        System.out.println("After append: " + builder);
        
        // Insert operation
        builder.insert(5, " Beautiful");
        System.out.println("After insert: " + builder);
        
        // Delete operation
        builder.delete(5, 15);
        System.out.println("After delete: " + builder);
        
        // Replace operation
        builder.replace(0, 5, "Hi");
        System.out.println("After replace: " + builder);
        
        // Reverse operation
        builder.reverse();
        System.out.println("After reverse: " + builder);
    }
}
```

## Math Class in Java

### What is the Math Class?
The `java.lang.Math` class provides methods for performing basic numeric operations such as elementary exponential, logarithm, square root, and trigonometric functions. It contains methods for calculating maximum/minimum values, rounding, and other common mathematical operations.

### Why use the Math Class?
- To perform mathematical calculations
- For scientific and engineering applications
- For graphical applications and game development
- To handle statistical and numerical operations

### Where to use the Math Class?
- Financial applications
- Scientific calculations
- Game development
- Data analysis
- Algorithm implementation

### Common Math Methods and Constants

#### Constants
```java
Math.PI    // Represents π (pi), approximately 3.14159
Math.E     // Represents e, approximately 2.71828
```

#### Basic Methods
```java
Math.abs(x)       // Returns absolute value of x
Math.max(x, y)    // Returns the greater of x and y
Math.min(x, y)    // Returns the smaller of x and y
Math.round(x)     // Rounds x to the nearest integer
Math.floor(x)     // Returns the largest integer <= x
Math.ceil(x)      // Returns the smallest integer >= x
```

#### Exponential and Logarithmic Methods
```java
Math.pow(x, y)    // Returns x raised to the power of y
Math.sqrt(x)      // Returns square root of x
Math.cbrt(x)      // Returns cube root of x
Math.exp(x)       // Returns e raised to the power of x
Math.log(x)       // Returns natural logarithm (base e) of x
Math.log10(x)     // Returns base 10 logarithm of x
```

#### Trigonometric Methods
```java
Math.sin(x)       // Returns sine of x (x in radians)
Math.cos(x)       // Returns cosine of x (x in radians)
Math.tan(x)       // Returns tangent of x (x in radians)
Math.asin(x)      // Returns arc sine of x
Math.acos(x)      // Returns arc cosine of x
Math.atan(x)      // Returns arc tangent of x
Math.toDegrees(x) // Converts angle x from radians to degrees
Math.toRadians(x) // Converts angle x from degrees to radians
```

#### Random Number Generation
```java
Math.random()     // Returns a random number between 0.0 (inclusive) and 1.0 (exclusive)
```

### Examples

#### Example 1: Basic math operations
```java
public class MathBasicsDemo {
    public static void main(String[] args) {
        // Constants
        System.out.println("Value of PI: " + Math.PI);
        System.out.println("Value of E: " + Math.E);
        
        // Basic operations
        System.out.println("\nBasic Operations:");
        System.out.println("Absolute value of -5.7: " + Math.abs(-5.7));
        System.out.println("Maximum of 10 and 20: " + Math.max(10, 20));
        System.out.println("Minimum of 10 and 20: " + Math.min(10, 20));
        
        // Rounding operations
        System.out.println("\nRounding Operations:");
        double value = 3.75;
        System.out.println("Original value: " + value);
        System.out.println("Rounded (nearest integer): " + Math.round(value));
        System.out.println("Floor (largest integer <= value): " + Math.floor(value));
        System.out.println("Ceiling (smallest integer >= value): " + Math.ceil(value));
        
        // Power and root functions
        System.out.println("\nPower and Root Functions:");
        System.out.println("2 raised to power 3: " + Math.pow(2, 3));
        System.out.println("Square root of 25: " + Math.sqrt(25));
        System.out.println("Cube root of 27: " + Math.cbrt(27));
        
        // Logarithmic functions
        System.out.println("\nLogarithmic Functions:");
        System.out.println("Natural log of e: " + Math.log(Math.E));
        System.out.println("Base 10 log of 100: " + Math.log10(100));
        
        // Random number generation
        System.out.println("\nRandom Number Generation:");
        System.out.println("Random number (0.0-1.0): " + Math.random());
        
        // Generate random number between 1 and 100
        int randomNum = (int)(Math.random() * 100) + 1;
        System.out.println("Random number (1-100): " + randomNum);
    }
}
```

#### Example 2: Trigonometric functions and applications
```java
public class MathTrigDemo {
    public static void main(String[] args) {
        // Conversion between degrees and radians
        System.out.println("Converting between degrees and radians:");
        double degrees = 45.0;
        double radians = Math.toRadians(degrees);
        System.out.println(degrees + " degrees = " + radians + " radians");
        System.out.println(radians + " radians = " + Math.toDegrees(radians) + " degrees");
        
        // Trigonometric functions
        System.out.println("\nTrigonometric functions for 45 degrees (π/4 radians):");
        System.out.println("Sine: " + Math.sin(radians));
        System.out.println("Cosine: " + Math.cos(radians));
        System.out.println("Tangent: " + Math.tan(radians));
        
        // Inverse trigonometric functions
        System.out.println("\nInverse trigonometric functions:");
        double value = 0.5;
        System.out.println("Arcsine of " + value + ": " + Math.asin(value) + " radians");
        System.out.println("Arccosine of " + value + ": " + Math.acos(value) + " radians");
        System.out.println("Arctangent of " + value + ": " + Math.atan(value) + " radians");
        
        // Practical application: Calculate distance between two points
        System.out.println("\nCalculating distance between two points:");
        double x1 = 2.0, y1 = 3.0;
        double x2 = 5.0, y2 = 7.0;
        
        double distance = Math.sqrt(Math.pow(x2 - x1, 2) + Math.pow(y2 - y1, 2));
        System.out.println("Distance between (" + x1 + "," + y1 + ") and (" + 
                          x2 + "," + y2 + "): " + distance);
        
        // Practical application: Calculate the area of a circle
        System.out.println("\nCalculating the area of a circle:");
        double radius = 5.0;
        double area = Math.PI * Math.pow(radius, 2);
        System.out.println("Area of circle with radius " + radius + ": " + area);
    }
}
```

## Practice Questions

1. **String Manipulation**: Write a Java program that takes a sentence as input and performs the following operations:
   - Count the total number of characters (excluding spaces)
   - Count the number of words
   - Reverse the entire sentence
   - Convert the first letter of each word to uppercase

2. **Password Validator**: Create a Java program that validates a password based on the following criteria:
   - At least 8 characters long
   - Contains at least one uppercase letter
   - Contains at least one lowercase letter
   - Contains at least one digit
   - Contains at least one special character (@, #, $, %, &, *)
   Use String methods to check each condition and provide appropriate feedback to the user.

3. **Math Calculator**: Develop a Java application that acts as a scientific calculator. It should provide options for:
   - Basic arithmetic operations (add, subtract, multiply, divide)
   - Power and root functions
   - Trigonometric functions (allowing input in degrees and converting to radians)
   - Logarithmic functions
   Use the Math class methods to implement these operations.

4. **Random Number Game**: Create a number guessing game where the computer generates a random number between 1 and 100, and the player has to guess it. The program should provide hints ("higher" or "lower") after each guess. Use Math.random() for generating the number.

5. **String vs StringBuilder Performance**: Write a Java program that compares the performance of String concatenation versus StringBuilder for creating a long string with thousands of iterations. The program should:
   - Measure and display the time taken for each approach
   - Calculate the performance difference as a percentage
   - Allow the user to input the number of iterations

