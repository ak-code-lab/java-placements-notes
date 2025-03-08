# User Input in Java

## What is User Input in Java?
User input in Java refers to the process of accepting and processing data from a user during program execution. Java provides several classes and methods to handle different types of input from various sources such as keyboard, files, or network connections.

## Why Use User Input?
1. **Interactivity**: Makes applications dynamic and responsive to user actions
2. **Customization**: Allows users to provide specific data for processing
3. **Flexibility**: Programs can adapt based on user-provided information
4. **User Experience**: Creates engaging applications that respond to user needs
5. **Data Collection**: Gathers information for processing, analysis, or storage

## Where to Use User Input?
1. **Console Applications**: Command-line programs requiring user interaction
2. **Form Processing**: Handling user submissions in desktop or web applications
3. **Configuration**: Setting application parameters at runtime
4. **Gaming**: Getting player actions and commands
5. **Data Entry Systems**: Applications for inputting and storing data

## Input Methods in Java

### 1. Scanner Class

#### What is Scanner?
The `Scanner` class is part of the `java.util` package and provides methods for reading different types of input (integers, strings, etc.) from various sources.

#### Syntax:
```java
import java.util.Scanner;

// Create Scanner object
Scanner scanner = new Scanner(System.in);  // For keyboard input

// Reading different types of input
String name = scanner.nextLine();       // Read a line of text
int age = scanner.nextInt();            // Read an integer
double salary = scanner.nextDouble();   // Read a double
boolean isEmployed = scanner.nextBoolean(); // Read a boolean

// Close the scanner when done
scanner.close();
```

#### Example 1: Basic Scanner Usage
```java
import java.util.Scanner;

public class BasicScannerExample {
    public static void main(String[] args) {
        // Create Scanner object
        Scanner scanner = new Scanner(System.in);
        
        // Prompt for name
        System.out.print("Enter your name: ");
        String name = scanner.nextLine();
        
        // Prompt for age
        System.out.print("Enter your age: ");
        int age = scanner.nextInt();
        
        // Display information
        System.out.println("Hello, " + name + "!");
        System.out.println("You are " + age + " years old.");
        
        // Close scanner
        scanner.close();
    }
}
```

#### Example 2: Handling Input Issues
```java
import java.util.Scanner;
import java.util.InputMismatchException;

public class InputValidationExample {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        int number = 0;
        boolean validInput = false;
        
        while (!validInput) {
            try {
                System.out.print("Enter a number: ");
                number = scanner.nextInt();
                validInput = true;
            } catch (InputMismatchException e) {
                System.out.println("Error: Please enter a valid number.");
                scanner.nextLine(); // Clear the invalid input
            }
        }
        
        System.out.println("You entered: " + number);
        scanner.close();
    }
}
```

### 2. BufferedReader Class

#### What is BufferedReader?
`BufferedReader` provides efficient reading of characters, arrays, and lines from various input sources. It's more efficient than Scanner for reading large amounts of text.

#### Syntax:
```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

// Create BufferedReader object
BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));

// Reading input
String name = reader.readLine();  // Reads a line of text

// Convert string input to other types
int age = Integer.parseInt(reader.readLine());  // Convert to int
double salary = Double.parseDouble(reader.readLine());  // Convert to double

// Close the reader when done
reader.close();
```

#### Example: Using BufferedReader
```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

public class BufferedReaderExample {
    public static void main(String[] args) {
        try (BufferedReader reader = new BufferedReader(new InputStreamReader(System.in))) {
            System.out.print("Enter your name: ");
            String name = reader.readLine();
            
            System.out.print("Enter your age: ");
            int age = Integer.parseInt(reader.readLine());
            
            System.out.println("Hello, " + name + "!");
            System.out.println("You are " + age + " years old.");
            
        } catch (IOException e) {
            System.out.println("Error reading input: " + e.getMessage());
        } catch (NumberFormatException e) {
            System.out.println("Error: Please enter a valid number for age.");
        }
    }
}
```

### 3. Console Class

#### What is Console?
The `Console` class, introduced in Java 6, provides methods for accessing the character-based console device, if available. It's useful for secure password input.

#### Syntax:
```java
import java.io.Console;

// Get Console instance
Console console = System.console();

// Reading input
String username = console.readLine("Enter username: ");
char[] password = console.readPassword("Enter password: ");  // Doesn't echo input

// Process password safely
// ... use password ...

// Clear password from memory when done
java.util.Arrays.fill(password, ' ');
```

#### Example: Using Console for Secure Input
```java
import java.io.Console;
import java.util.Arrays;

public class ConsoleExample {
    public static void main(String[] args) {
        Console console = System.console();
        
        if (console == null) {
            System.out.println("Console is not available. Run this program from a terminal/console.");
            System.exit(1);
        }
        
        String username = console.readLine("Enter your username: ");
        char[] password = console.readPassword("Enter your password: ");
        
        // Validate credentials (example only)
        boolean isAuthenticated = authenticate(username, password);
        
        // Clear password from memory
        Arrays.fill(password, ' ');
        
        if (isAuthenticated) {
            console.printf("Welcome, %s! You are logged in.\n", username);
        } else {
            console.printf("Authentication failed.\n");
        }
    }
    
    private static boolean authenticate(String username, char[] password) {
        // This is a simple example. In a real application, you would check against a secure database.
        String validUser = "admin";
        char[] validPass = {'p', 'a', 's', 's', 'w', 'o', 'r', 'd'};
        
        boolean result = username.equals(validUser) && Arrays.equals(password, validPass);
        
        // Clear sensitive data
        Arrays.fill(validPass, ' ');
        
        return result;
    }
}
```

### 4. Command Line Arguments

#### What are Command Line Arguments?
Command line arguments are parameters that can be passed to a Java program when it is executed from the command line.

#### Syntax:
```java
public class CommandLineExample {
    public static void main(String[] args) {
        // args array contains all command line arguments
        
        System.out.println("Number of arguments: " + args.length);
        
        for (int i = 0; i < args.length; i++) {
            System.out.println("Argument " + i + ": " + args[i]);
        }
    }
}
```

#### Example: Processing Command Line Arguments
```java
public class Calculator {
    public static void main(String[] args) {
        if (args.length != 3) {
            System.out.println("Usage: java Calculator <number1> <operation> <number2>");
            System.out.println("Operations: add, subtract, multiply, divide");
            return;
        }
        
        try {
            double num1 = Double.parseDouble(args[0]);
            String operation = args[1].toLowerCase();
            double num2 = Double.parseDouble(args[2]);
            double result = 0;
            
            switch (operation) {
                case "add":
                    result = num1 + num2;
                    break;
                case "subtract":
                    result = num1 - num2;
                    break;
                case "multiply":
                    result = num1 * num2;
                    break;
                case "divide":
                    if (num2 == 0) {
                        System.out.println("Error: Division by zero");
                        return;
                    }
                    result = num1 / num2;
                    break;
                default:
                    System.out.println("Invalid operation: " + operation);
                    return;
            }
            
            System.out.println("Result: " + result);
            
        } catch (NumberFormatException e) {
            System.out.println("Error: Please provide valid numbers");
        }
    }
}
```

## Best Practices for User Input

1. **Always Validate Input**: Never trust user input without validation
2. **Close Input Resources**: Always close Scanner, BufferedReader, etc. when done
3. **Handle Exceptions**: Use try-catch blocks to handle potential errors
4. **Provide Clear Prompts**: Tell users exactly what format of input is expected
5. **Use Appropriate Method**: Choose the right input method based on your needs
6. **Buffer Management**: Be careful of leftover newline characters in input buffers

## Practice Questions

### Question 1: Basic Input Handling
Write a Java program that asks the user for their name, age, and height (in meters), then displays a summary of the information entered.

### Question 2: Input Validation
Create a program that asks the user to enter a number between 1 and 100. Validate the input and keep asking until a valid number is entered.

### Question 3: Menu-Based System
Develop a simple calculator program that displays a menu of operations (addition, subtraction, multiplication, division), takes two numbers as input, and displays the result of the chosen operation.

### Question 4: File Input
Write a program that reads numbers from a file (one number per line) and calculates their sum and average.

### Question 5: Secure Password Entry
Create a login system that securely reads a username and password. The password should not be displayed on screen as it's typed. Compare the entered credentials with stored values and display an appropriate message.