# Java Control Flow Statements

## Control Flow in Java

Control flow statements in Java determine the order in which the code executes. They allow you to make decisions, loop through code blocks, and alter the sequential flow of execution.

## Decision-Making Statements

### 1. if Statement

#### What is if Statement?
The `if` statement is the most basic control flow statement that allows Java to execute a certain block of code only if a specified condition evaluates to `true`.

#### Why use if Statement?
- To execute code conditionally
- To implement decision-making logic in your program
- To handle different cases based on input or state

#### Where to use if Statement?
- Input validation
- Error handling
- Business logic implementation
- Feature toggles
- Conditional data processing

#### Syntax
```java
if (condition) {
    // Code to execute if condition is true
}
```

#### Examples.

#### Example 1: Basic if statement
```java
public class BasicIfDemo {
    public static void main(String[] args) {
        int age = 20;
        
        if (age >= 18) {
            System.out.println("You are eligible to vote.");
        }
        
        System.out.println("Program continues execution...");
    }
}
```

#### Example 2: if statement with multiple expressions
```java
public class ComplexIfDemo {
    public static void main(String[] args) {
        int score = 85;
        boolean isPassing = true;
        
        if (score > 70 && isPassing) {
            System.out.println("Good job! You've passed with a high score.");
            
            // Additional code that executes only if condition is true
            int bonusPoints = score / 10;
            System.out.println("You earned " + bonusPoints + " bonus points!");
        }
    }
}
```

### 2. if-else Statement

#### What is if-else Statement?
The `if-else` statement extends the `if` statement by providing an alternative code block to execute when the condition is `false`.

#### Why use if-else Statement?
- To handle two alternative scenarios
- To execute different code blocks based on a condition
- To implement binary decisions

#### Where to use if-else Statement?
- User authentication (success/failure)
- Data validation (valid/invalid)
- Boolean flag checking
- Simple state management
- Pass/fail testing

#### Syntax
```java
if (condition) {
    // Code to execute if condition is true
} else {
    // Code to execute if condition is false
}
```

#### Example 1: Basic if-else statement
```java
public class IfElseDemo {
    public static void main(String[] args) {
        int age = 15;
        
        if (age >= 18) {
            System.out.println("You are eligible to vote.");
        } else {
            System.out.println("Sorry, you are not eligible to vote yet.");
            System.out.println("You need to wait " + (18 - age) + " more years.");
        }
    }
}
```

#### Example 2: if-else with more complex condition
```java
public class IfElseComplexDemo {
    public static void main(String[] args) {
        double balance = 2500.0;
        double withdrawAmount = 3000.0;
        
        if (withdrawAmount <= balance) {
            balance -= withdrawAmount;
            System.out.println("Withdrawal successful. New balance: $" + balance);
        } else {
            System.out.println("Insufficient funds. You need $" + 
                (withdrawAmount - balance) + " more to make this withdrawal.");
            System.out.println("Current balance: $" + balance);
        }
    }
}
```

### 3. if-else-if Statement (else-if Ladder)

#### What is if-else-if Statement?
The `if-else-if` statement (or else-if ladder) allows you to check multiple conditions in sequence and execute the code block associated with the first condition that evaluates to `true`.

#### Why use if-else-if Statement?
- To handle multiple alternative scenarios
- To implement multi-way branching
- To check a series of conditions in order
- To categorize data or inputs

#### Where to use if-else-if Statement?
- Grading systems
- Input classification
- Menu systems
- Error handling with different error types
- State machines with limited states

#### Syntax
```java
if (condition1) {
    // Code to execute if condition1 is true
} else if (condition2) {
    // Code to execute if condition1 is false and condition2 is true
} else if (condition3) {
    // Code to execute if condition1 and condition2 are false and condition3 is true
} else {
    // Code to execute if all conditions are false
}
```

#### Example 1: Grade calculator using if-else-if
```java
public class GradeCalculator {
    public static void main(String[] args) {
        int score = 75;
        char grade;
        
        if (score >= 90) {
            grade = 'A';
        } else if (score >= 80) {
            grade = 'B';
        } else if (score >= 70) {
            grade = 'C';
        } else if (score >= 60) {
            grade = 'D';
        } else {
            grade = 'F';
        }
        
        System.out.println("Score: " + score);
        System.out.println("Grade: " + grade);
        
        // Additional message based on grade
        if (grade == 'A' || grade == 'B') {
            System.out.println("Excellent performance!");
        } else if (grade == 'C') {
            System.out.println("Good performance, but there's room for improvement.");
        } else {
            System.out.println("You need to study harder.");
        }
    }
}
```

#### Example 2: Season detector using if-else-if
```java
public class SeasonDetector {
    public static void main(String[] args) {
        int month = 7; // July
        String season;
        
        if (month == 12 || month == 1 || month == 2) {
            season = "Winter";
        } else if (month >= 3 && month <= 5) {
            season = "Spring";
        } else if (month >= 6 && month <= 8) {
            season = "Summer";
        } else if (month >= 9 && month <= 11) {
            season = "Fall";
        } else {
            season = "Invalid month";
        }
        
        System.out.println("Month: " + month);
        System.out.println("Season: " + season);
    }
}
```

### 4. switch Statement

#### What is switch Statement?
The `switch` statement allows you to select one of many code blocks to be executed based on the value of an expression.

#### Why use switch Statement?
- To handle multiple specific cases efficiently
- As an alternative to long if-else-if chains
- For cleaner, more readable code when checking against exact values
- For better performance with multiple exact-match cases

#### Where to use switch Statement?
- Menu-driven programs
- Command processors
- State machines
- Input handling based on specific values
- Day, month, or enum-based logic

#### Syntax
```java
switch (expression) {
    case value1:
        // Code to execute if expression equals value1
        break;
    case value2:
        // Code to execute if expression equals value2
        break;
    // More cases as needed
    default:
        // Code to execute if expression doesn't match any case
        break;
}
```

#### Example 1: Basic switch statement for days of week
```java
public class DayOfWeekDemo {
    public static void main(String[] args) {
        int day = 4;
        String dayName;
        
        switch (day) {
            case 1:
                dayName = "Monday";
                break;
            case 2:
                dayName = "Tuesday";
                break;
            case 3:
                dayName = "Wednesday";
                break;
            case 4:
                dayName = "Thursday";
                break;
            case 5:
                dayName = "Friday";
                break;
            case 6:
                dayName = "Saturday";
                break;
            case 7:
                dayName = "Sunday";
                break;
            default:
                dayName = "Invalid day";
                break;
        }
        
        System.out.println("Day of the week: " + dayName);
    }
}
```

#### Example 2: switch with fall-through and String input
```java
public class MonthDaysCalculator {
    public static void main(String[] args) {
        String month = "February";
        int year = 2024;
        int days;
        
        switch (month) {
            case "January":
            case "March":
            case "May":
            case "July":
            case "August":
            case "October":
            case "December":
                days = 31;
                break;
            case "April":
            case "June":
            case "September":
            case "November":
                days = 30;
                break;
            case "February":
                // Leap year check
                if ((year % 400 == 0) || ((year % 4 == 0) && (year % 100 != 0))) {
                    days = 29;
                } else {
                    days = 28;
                }
                break;
            default:
                days = 0;
                System.out.println("Invalid month: " + month);
                break;
        }
        
        if (days != 0) {
            System.out.println(month + " " + year + " has " + days + " days.");
        }
    }
}
```

## Looping Statements

### 1. for Loop

#### What is for Loop?
The `for` loop is used to iterate a block of code a specific number of times. It's particularly useful when you know in advance how many times you want to execute the code.

#### Why use for Loop?
- When the number of iterations is known beforehand
- For iterating through arrays or collections
- For repetitive tasks that need to be done a fixed number of times
- For counter-based operations

#### Where to use for Loop?
- Array traversal
- Matrix operations
- Generating sequences
- Fixed-iteration algorithms
- Batch processing

#### Syntax
```java
for (initialization; condition; update) {
    // Code to be repeated
}
```

#### Example 1: Basic for loop to print numbers
```java
public class BasicForLoopDemo {
    public static void main(String[] args) {
        // Print numbers from 1 to 5
        System.out.println("Counting from 1 to 5:");
        for (int i = 1; i <= 5; i++) {
            System.out.println("Count: " + i);
        }
        
        // Print even numbers from 2 to 10
        System.out.println("\nEven numbers from 2 to 10:");
        for (int i = 2; i <= 10; i += 2) {
            System.out.print(i + " ");
        }
    }
}
```

#### Example 2: for loop with arrays
```java
public class ForLoopArrayDemo {
    public static void main(String[] args) {
        int[] numbers = {5, 10, 15, 20, 25};
        int sum = 0;
        
        System.out.println("Array elements:");
        for (int i = 0; i < numbers.length; i++) {
            System.out.println("Element at index " + i + ": " + numbers[i]);
            sum += numbers[i];
        }
        
        System.out.println("\nSum of all elements: " + sum);
        System.out.println("Average: " + (double) sum / numbers.length);
        
        // Enhanced for loop (for-each) - simplified syntax for collections
        System.out.println("\nUsing enhanced for loop:");
        for (int number : numbers) {
            System.out.println("Value: " + number);
        }
    }
}
```

### 2. while Loop

#### What is while Loop?
The `while` loop is used to execute a block of code repeatedly as long as a condition is true. The condition is checked before the loop body is executed.

#### Why use while Loop?
- When the exact number of iterations is not known in advance
- For event-driven loops that depend on external conditions
- For input processing until a specific value is encountered
- For state-based repetitions

#### Where to use while Loop?
- Reading input until a sentinel value
- Processing until a specific condition is met
- Game loops
- Network connections
- Stream processing

#### Syntax
```java
while (condition) {
    // Code to be repeated as long as condition is true
}
```

#### Example 1: Basic while loop
```java
public class BasicWhileDemo {
    public static void main(String[] args) {
        int count = 1;
        
        System.out.println("Counting with while loop:");
        while (count <= 5) {
            System.out.println("Count: " + count);
            count++;
        }
        
        // Backward counting
        System.out.println("\nCounting backward:");
        int countDown = 10;
        while (countDown > 0) {
            System.out.print(countDown + " ");
            countDown--;
        }
        System.out.println("Blast off!");
    }
}
```

#### Example 2: while loop with user input
```java
import java.util.Scanner;

public class WhileWithInputDemo {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input = "";
        
        System.out.println("Enter commands (type 'exit' to quit):");
        
        while (!input.equalsIgnoreCase("exit")) {
            System.out.print("> ");
            input = scanner.nextLine();
            
            if (!input.equalsIgnoreCase("exit")) {
                System.out.println("You entered: " + input);
                
                // Process commands
                if (input.equalsIgnoreCase("help")) {
                    System.out.println("Available commands: help, date, version, exit");
                } else if (input.equalsIgnoreCase("date")) {
                    System.out.println("Current date: " + new java.util.Date());
                } else if (input.equalsIgnoreCase("version")) {
                    System.out.println("Program version: 1.0");
                } else {
                    System.out.println("Unknown command. Type 'help' for available commands.");
                }
            }
        }
        
        System.out.println("Program terminated.");
        scanner.close();
    }
}
```

### 3. do-while Loop

#### What is do-while Loop?
The `do-while` loop is similar to the `while` loop, but it guarantees that the code block is executed at least once, regardless of the condition. The condition is checked after the loop body is executed.

#### Why use do-while Loop?
- When you need to ensure the loop body executes at least once
- For input validation where you need to get input first, then check it
- For menus where you want to display options before checking the user's choice
- For post-condition checking algorithms

#### Where to use do-while Loop?
- Menu systems
- Input validation loops
- Game loops requiring at least one iteration
- User interaction flows
- Algorithms requiring at least one execution

#### Syntax
```java
do {
    // Code to be repeated at least once
} while (condition);
```

#### Example 1: Basic do-while loop
```java
public class BasicDoWhileDemo {
    public static void main(String[] args) {
        int count = 1;
        
        System.out.println("Counting with do-while loop:");
        do {
            System.out.println("Count: " + count);
            count++;
        } while (count <= 5);
        
        // Even when the condition is initially false, the loop executes once
        System.out.println("\nDemonstrating at least one execution:");
        int number = 10;
        do {
            System.out.println("This will print once even though condition is false");
            number++;
        } while (number < 10);
    }
}
```

#### Example 2: do-while with user input validation
```java
import java.util.Scanner;

public class InputValidationDemo {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int userInput;
        
        do {
            System.out.print("Enter a positive number: ");
            
            // Check if input is an integer
            while (!scanner.hasNextInt()) {
                System.out.println("That's not a valid number!");
                System.out.print("Enter a positive number: ");
                scanner.next(); // Discard invalid input
            }
            
            userInput = scanner.nextInt();
            
            if (userInput <= 0) {
                System.out.println("That's not a positive number!");
            }
        } while (userInput <= 0);
        
        System.out.println("You entered a valid positive number: " + userInput);
        scanner.close();
    }
}
```

## Jump Statements

### 1. break Statement

#### What is break Statement?
The `break` statement is used to exit or terminate a loop or a switch statement prematurely.

#### Why use break Statement?
- To exit a loop when a specific condition is met
- To stop processing when you've found what you're looking for
- To implement early termination logic
- To exit a switch case
- To optimize performance by avoiding unnecessary iterations

#### Where to use break Statement?
- Search algorithms (when target is found)
- To handle exceptional conditions in loops
- To implement stop conditions
- In switch statements to prevent fall-through
- To implement custom loop control

#### Syntax
```java
// Inside a loop or switch
break;

// With labeled statements
break label;
```

#### Example 1: break in a for loop
```java
public class BreakInForLoopDemo {
    public static void main(String[] args) {
        System.out.println("Finding the first number divisible by 7 between 1 and 100:");
        
        for (int i = 1; i <= 100; i++) {
            if (i % 7 == 0) {
                System.out.println("Found: " + i);
                break; // Exit the loop once we find the first number
            }
            System.out.println("Checking: " + i);
        }
        
        System.out.println("Loop terminated.");
        
        // Using break in nested loops
        System.out.println("\nPrime number check from 2 to 20:");
        outerLoop: for (int i = 2; i <= 20; i++) {
            for (int j = 2; j < i; j++) {
                if (i % j == 0) {
                    System.out.println(i + " is not a prime number (divisible by " + j + ")");
                    continue outerLoop; // Skip to the next number in outer loop
                }
            }
            System.out.println(i + " is a prime number");
        }
    }
}
```

#### Example 2: break in a switch statement
```java
import java.util.Scanner;

public class BreakInSwitchDemo {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Menu:");
        System.out.println("1. Add");
        System.out.println("2. Subtract");
        System.out.println("3. Multiply");
        System.out.println("4. Divide");
        System.out.print("Enter your choice (1-4): ");
        
        int choice = scanner.nextInt();
        
        System.out.print("Enter first number: ");
        double num1 = scanner.nextDouble();
        
        System.out.print("Enter second number: ");
        double num2 = scanner.nextDouble();
        
        double result = 0;
        
        switch (choice) {
            case 1:
                result = num1 + num2;
                System.out.println("Result: " + result);
                break; // Without break, execution would fall through to the next case
                
            case 2:
                result = num1 - num2;
                System.out.println("Result: " + result);
                break;
                
            case 3:
                result = num1 * num2;
                System.out.println("Result: " + result);
                break;
                
            case 4:
                if (num2 == 0) {
                    System.out.println("Error: Cannot divide by zero");
                } else {
                    result = num1 / num2;
                    System.out.println("Result: " + result);
                }
                break;
                
            default:
                System.out.println("Invalid choice");
                break;
        }
        
        scanner.close();
    }
}
```

### 2. continue Statement

#### What is continue Statement?
The `continue` statement skips the current iteration of a loop and proceeds to the next iteration.

#### Why use continue Statement?
- To skip specific iterations based on a condition
- To filter out certain values in a processing loop
- To avoid deeply nested if statements inside loops
- To implement conditional processing logic efficiently

#### Where to use continue Statement?
- Data filtering
- Error handling within loops
- Input validation
- Processing only certain elements in collections
- Implementing complex iteration patterns

#### Syntax
```java
// Inside a loop
continue;

// With labeled statements
continue label;
```

#### Example 1: continue in a for loop
```java
public class ContinueInForLoopDemo {
    public static void main(String[] args) {
        // Print only odd numbers from 1 to 10
        System.out.println("Odd numbers from 1 to 10:");
        for (int i = 1; i <= 10; i++) {
            if (i % 2 == 0) {
                continue; // Skip even numbers
            }
            System.out.print(i + " ");
        }
        
        // Print numbers from 1 to 20, skipping multiples of 3
        System.out.println("\n\nNumbers from 1 to 20 (excluding multiples of 3):");
        for (int i = 1; i <= 20; i++) {
            if (i % 3 == 0) {
                continue; // Skip multiples of 3
            }
            System.out.print(i + " ");
        }
    }
}
```

#### Example 2: continue with labeled statements
```java
public class LabeledContinueDemo {
    public static void main(String[] args) {
        // Print a pattern using nested loops and continue
        System.out.println("Multiplication table (skipping some combinations):");
        
        outerLoop: for (int i = 1; i <= 5; i++) {
            for (int j = 1; j <= 5; j++) {
                // Skip when sum of indices is even
                if ((i + j) % 2 == 0) {
                    continue;
                }
                
                System.out.printf("%d x %d = %d\n", i, j, i * j);
                
                // Skip to next i when j reaches 3
                if (j == 3) {
                    System.out.println("-- Skipping remaining columns for row " + i + " --");
                    continue outerLoop;
                }
            }
            
            System.out.println("-- End of row " + i + " --");
        }
        
        // Process an array, filtering out negative values
        System.out.println("\nProcessing array values (positive only):");
        int[] values = {15, -7, 22, 9, -13, 0, 35, -8};
        int sum = 0;
        
        for (int value : values) {
            if (value < 0) {
                System.out.println("Skipping negative value: " + value);
                continue;
            }
            
            System.out.println("Processing: " + value);
            sum += value;
        }
        
        System.out.println("Sum of positive values: " + sum);
    }
}
```

## Practice Questions

1. **Leap Year Checker**: Write a Java program that checks if a given year is a leap year. A leap year is divisible by 4, but not by 100 unless it is also divisible by 400. Use appropriate if-else statements to implement the logic.

2. **Grade Calculator with Switch**: Create a program that takes a numerical grade (0-100) as input and outputs the corresponding letter grade using a switch statement:
   - 90-100: A
   - 80-89: B
   - 70-79: C
   - 60-69: D
   - Below 60: F

3. **Prime Number Finder**: Write a program to find all prime numbers between 1 and 100. Use a nested loop with appropriate break or continue statements for efficiency.

4. **Temperature Converter**: Create a menu-driven temperature conversion program that can convert between Celsius, Fahrenheit, and Kelvin. Use a do-while loop to keep the program running until the user chooses to exit.

5. **Pattern Printing**: Write a program that uses nested loops to print the following pattern:
   ```
   *
   **
   ***
   ****
   *****
   ```
   Then modify it to print:
   ```
       *
      **
     ***
    ****
   *****
   ```

   