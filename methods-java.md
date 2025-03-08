# Java Methods

## What is a Method in Java?
A method in Java is a block of code that performs a specific task. It is designed to be reusable, helping you avoid redundant code and making your program more modular and maintainable. Methods are defined inside a class and can be called by their name.

## Why Use Methods?
1. **Code Reusability**: Write code once and use it multiple times
2. **Modularity**: Break down complex problems into smaller, manageable parts
3. **Maintainability**: Easier to debug and modify isolated blocks of code
4. **Abstraction**: Hide implementation details while exposing functionality
5. **Organization**: Structure your code in a logical manner

## Where to Use Methods?
1. **Repetitive Tasks**: When the same operation needs to be performed multiple times
2. **Complex Calculations**: To break down complicated logic into simpler steps
3. **Data Processing**: When transforming input data to output
4. **Event Handling**: To execute code in response to user actions
5. **API Development**: To create interfaces for other developers

## Syntax

```java
accessModifier returnType methodName(parameterType parameter1, parameterType parameter2, ...) {
    // Method body
    // Code to be executed
    
    return value; // If the return type is not void
}
```

**Components**:
- **Access Modifier**: Determines the visibility (e.g., `public`, `private`, `protected`)
- **Return Type**: Data type of the value returned by the method (or `void` if nothing is returned)
- **Method Name**: Name that identifies the method (follows camelCase convention)
- **Parameters**: Input values the method operates on (optional)
- **Method Body**: The actual code to be executed
- **Return Statement**: Returns a value to the caller (required if return type is not `void`)

## Examples

### Example 1: A simple method that adds two numbers

```java
public class Calculator {
    // Method to add two integers
    public int add(int num1, int num2) {
        int sum = num1 + num2;
        return sum;
    }
    
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        int result = calc.add(5, 3);
        System.out.println("Sum: " + result); // Output: Sum: 8
    }
}
```

### Example 2: A method with no return value (void)

```java
public class Greeting {
    // Method that doesn't return any value
    public void printWelcomeMessage(String name) {
        System.out.println("Hello, " + name + "! Welcome to Java Programming.");
    }
    
    public static void main(String[] args) {
        Greeting greeting = new Greeting();
        greeting.printWelcomeMessage("Alice"); // Output: Hello, Alice! Welcome to Java Programming.
    }
}
```

## Practice Questions

1. **Basic Method Creation**:
   Write a Java method named `calculateArea` that takes the radius of a circle as a parameter and returns the area of the circle.

2. **Method Overloading**:
   Create a class with two methods having the same name `calculateArea`. One should calculate the area of a rectangle (length and width as parameters) and the other should calculate the area of a triangle (base and height as parameters).

3. **Method with Array Parameter**:
   Write a method named `findMax` that takes an array of integers as a parameter and returns the maximum value in the array.

4. **Method with Variable Arguments**:
   Create a method named `average` that can accept a variable number of double values and returns their average.

5. **Recursive Method**:
   Implement a recursive method named `factorial` that calculates the factorial of a given number.


# Java Method Concepts

## Method Overloading

### What is Method Overloading?
Method overloading is a feature in Java that allows a class to have multiple methods with the same name but different parameters. The compiler distinguishes these methods based on the number, type, and order of parameters.

### Why Use Method Overloading?
1. **Improved Readability**: Using the same name for related operations makes code more intuitive
2. **Reduced Complexity**: No need to remember different method names for similar operations
3. **Consistency**: Provides a consistent interface for related functionality
4. **Code Organization**: Groups related methods under a common name
5. **Flexibility**: Allows methods to handle different types or numbers of inputs

### Where to Use Method Overloading?
1. **Constructors**: Creating objects with different initialization parameters
2. **Utility Methods**: Methods that perform similar operations on different data types
3. **Mathematical Operations**: Functions that can work with different numeric types
4. **String Processing**: Methods that handle different text formats or inputs
5. **API Design**: Creating flexible interfaces for other developers

### Syntax
```java
class ClassName {
    // Method with one parameter
    returnType methodName(dataType1 parameter1) {
        // Method implementation
    }
    
    // Method with the same name but different parameters
    returnType methodName(dataType1 parameter1, dataType2 parameter2) {
        // Method implementation
    }
    
    // Method with the same name but different parameter types
    returnType methodName(differentDataType parameter1) {
        // Method implementation
    }
}
```

### Examples

#### Example 1: Method Overloading with Different Parameter Numbers
```java
public class Calculator {
    // Method with two parameters
    public int add(int a, int b) {
        return a + b;
    }
    
    // Overloaded method with three parameters
    public int add(int a, int b, int c) {
        return a + b + c;
    }
    
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println("Sum of 5 and 10: " + calc.add(5, 10));        // Calls first method
        System.out.println("Sum of 5, 10, and 15: " + calc.add(5, 10, 15)); // Calls second method
    }
}
```

#### Example 2: Method Overloading with Different Parameter Types
```java
public class Display {
    // Method for integer
    public void printValue(int value) {
        System.out.println("Printing integer: " + value);
    }
    
    // Method for double
    public void printValue(double value) {
        System.out.println("Printing double: " + value);
    }
    
    // Method for String
    public void printValue(String value) {
        System.out.println("Printing string: " + value);
    }
    
    public static void main(String[] args) {
        Display display = new Display();
        display.printValue(10);       // Calls first method
        display.printValue(10.5);     // Calls second method
        display.printValue("Hello");  // Calls third method
    }
}
```

### Practice Questions
1. Create a class with an overloaded method `calculate` that can find the area of a circle, rectangle, and triangle based on different parameters passed.

2. Write a program with an overloaded method `max` that returns the maximum of two integers, three integers, or two doubles.

3. Create a class named `StringUtility` with an overloaded method `concatenate` that can join two strings, three strings, or an array of strings.

4. Implement a `MyMath` class with overloaded methods for `power` that can handle different numeric types (int, long, double).

5. Design a class with an overloaded `printArray` method that can print arrays of different types (int[], double[], String[]).

## Method Scope

### What is Method Scope?
Method scope in Java refers to the visibility and accessibility of variables within a method. Variables declared inside a method are local to that method and can only be accessed within that method's block.

### Why Use Method Scope?
1. **Encapsulation**: Keeps variables confined to where they're needed
2. **Memory Management**: Local variables exist only while the method executes
3. **Name Isolation**: Allows reuse of variable names in different methods
4. **Reduced Complexity**: Limits the context that a developer needs to consider
5. **Bug Prevention**: Prevents unintended variable modification

### Where to Use Method Scope?
1. **Temporary Variables**: Variables needed only for intermediate calculations
2. **Method-Specific Logic**: Data relevant only to a specific method's operation
3. **Iterator Variables**: Loop counters and similar control variables
4. **Local Caching**: Storing temporary results within a method
5. **Parameter Handling**: Processing method parameters

### Syntax
```java
public class ScopeExample {
    // Class-level variable (instance variable)
    private int classVar = 10;
    
    public void methodA() {
        // Method-level variable (local variable)
        int localVar = 20;
        System.out.println(classVar);  // Can access class variable
        System.out.println(localVar);  // Can access local variable
    }
    
    public void methodB() {
        System.out.println(classVar);   // Can access class variable
        // System.out.println(localVar); // ERROR: Cannot access localVar defined in methodA
    }
}
```

### Examples

#### Example 1: Basic Method Scope
```java
public class ScopeDemo {
    // Instance variable
    private int instanceVar = 100;
    
    public void demonstrateScope() {
        // Local variable
        int localVar = 200;
        
        System.out.println("Instance variable: " + instanceVar);
        System.out.println("Local variable: " + localVar);
        
        // Local block
        {
            // Block-scoped variable
            int blockVar = 300;
            System.out.println("Block variable: " + blockVar);
            
            // Can access all variables
            System.out.println("Can access instance var: " + instanceVar);
            System.out.println("Can access local var: " + localVar);
        }
        
        // Cannot access blockVar here
        // System.out.println(blockVar); // Compilation error
    }
    
    public void anotherMethod() {
        System.out.println("Instance variable: " + instanceVar);
        // Cannot access localVar here
        // System.out.println(localVar); // Compilation error
    }
    
    public static void main(String[] args) {
        ScopeDemo demo = new ScopeDemo();
        demo.demonstrateScope();
    }
}
```

#### Example 2: Method Parameters and Variable Shadowing
```java
public class ShadowDemo {
    // Instance variable
    private int value = 10;
    
    public void printValue() {
        System.out.println("Instance value: " + value);
    }
    
    public void setValue(int value) {
        // Parameter 'value' shadows the instance variable 'value'
        // Using 'this' to refer to instance variable
        this.value = value;
        
        System.out.println("Parameter value: " + value);
        System.out.println("Instance value after setting: " + this.value);
    }
    
    public static void main(String[] args) {
        ShadowDemo demo = new ShadowDemo();
        demo.printValue();   // Prints: Instance value: 10
        demo.setValue(20);   // Sets the instance variable value to 20
        demo.printValue();   // Prints: Instance value: 20
    }
}
```

### Practice Questions
1. Write a program that demonstrates variable shadowing by creating a class with an instance variable and a method that has a parameter with the same name.

2. Create a class with methods that demonstrate the different kinds of variable scope: instance variables, local method variables, and block-scoped variables.

3. Write a program that shows how to access class-level variables from different methods within the same class.

4. Create a program that demonstrates how local variables are initialized within their scope and what happens when you try to use them before initialization.

5. Implement a method that uses the same variable name in nested blocks to demonstrate how inner blocks can shadow variables from outer blocks.

## Method Recursion

### What is Method Recursion?
Method recursion in Java is a technique where a method calls itself to solve a problem by breaking it down into smaller instances of the same problem. Each recursive call works on a simpler version until a base case is reached.

### Why Use Method Recursion?
1. **Simplicity**: Elegant solutions for problems that have a recursive nature
2. **Problem Decomposition**: Breaking complex problems into smaller, similar subproblems
3. **Readability**: Often more concise and easier to understand for some algorithms
4. **Natural Fit**: Ideal for problems with recursive mathematical definitions
5. **Tree-Like Structures**: Effective for traversing hierarchical data structures

### Where to Use Method Recursion?
1. **Mathematical Calculations**: Factorial, Fibonacci series, etc.
2. **Tree Traversal**: Binary trees, file systems, organizational hierarchies
3. **Sorting Algorithms**: Quicksort, Mergesort
4. **Graph Algorithms**: Depth-first search, path finding
5. **Divide and Conquer**: Problems that can be divided into smaller, similar subproblems

### Syntax
```java
returnType methodName(parameters) {
    // Base case - condition to stop recursion
    if (baseCondition) {
        return baseValue;
    }
    // Recursive case - method calls itself with modified parameters
    else {
        return methodName(modifiedParameters);
    }
}
```

### Examples

#### Example 1: Factorial Calculation using Recursion
```java
public class FactorialExample {
    public int factorial(int n) {
        // Base case: factorial of 0 or 1 is 1
        if (n <= 1) {
            return 1;
        }
        // Recursive case: n! = n * (n-1)!
        else {
            return n * factorial(n - 1);
        }
    }
    
    public static void main(String[] args) {
        FactorialExample example = new FactorialExample();
        int result = example.factorial(5);
        System.out.println("Factorial of 5 is: " + result);
        // Output: Factorial of 5 is: 120
    }
}
```

#### Example 2: Fibonacci Series using Recursion
```java
public class FibonacciExample {
    public int fibonacci(int n) {
        // Base cases
        if (n <= 0) {
            return 0;
        }
        else if (n == 1) {
            return 1;
        }
        // Recursive case: fib(n) = fib(n-1) + fib(n-2)
        else {
            return fibonacci(n - 1) + fibonacci(n - 2);
        }
    }
    
    public static void main(String[] args) {
        FibonacciExample example = new FibonacciExample();
        
        System.out.println("Fibonacci Series (First 10 numbers):");
        for (int i = 0; i < 10; i++) {
            System.out.print(example.fibonacci(i) + " ");
        }
        // Output: 0 1 1 2 3 5 8 13 21 34
    }
}
```

### Practice Questions
1. Write a recursive method to calculate the sum of all numbers from 1 to n.

2. Implement a recursive method to calculate the power of a number (x^n).

3. Create a recursive method to reverse a string.

4. Write a recursive method to check if a given string is a palindrome.

5. Implement a recursive method to find the greatest common divisor (GCD) of two numbers using the Euclidean algorithm.