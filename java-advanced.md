# Java Advanced Topics Study Guide

## 1. Java Exceptions

### What are Exceptions?
Exceptions in Java are events that disrupt the normal flow of program execution. They represent problems that occur during a program's execution, such as trying to open a file that doesn't exist or dividing by zero.

### Why use Exceptions?
- Separate error-handling code from regular code
- Propagate errors up the call stack
- Group and differentiate error types
- Create a robust application that handles unexpected conditions gracefully

### Where to use Exceptions?
- When validating user input
- During file and network operations
- When handling database connections
- When dealing with operations that might fail due to external factors
- To enforce business rules in applications

### Exception Hierarchy
```
Throwable
├── Error (unchecked)
└── Exception
    ├── RuntimeException (unchecked)
    └── Other exceptions (checked)
```

### Syntax

#### Try-Catch Block
```java
try {
    // Code that might throw an exception
} catch (ExceptionType e) {
    // Code to handle the exception
} finally {
    // Code that always executes, regardless of whether an exception occurred
}
```

#### Throwing Exceptions
```java
if (condition) {
    throw new ExceptionType("Error message");
}
```

#### Custom Exceptions
```java
public class CustomException extends Exception {
    public CustomException() {
        super();
    }
    
    public CustomException(String message) {
        super(message);
    }
}
```

### Examples

#### Example 1: Handling File Operations with Exceptions
```java
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class FileReaderExample {
    public static void main(String[] args) {
        try {
            File file = new File("nonexistent.txt");
            Scanner scanner = new Scanner(file);
            while (scanner.hasNextLine()) {
                System.out.println(scanner.nextLine());
            }
            scanner.close();
        } catch (FileNotFoundException e) {
            System.out.println("Error: File not found.");
            System.out.println("Exception details: " + e.getMessage());
        } finally {
            System.out.println("File operation attempt completed.");
        }
    }
}
```

#### Example 2: Custom Exception for Business Logic
```java
public class InsufficientFundsException extends Exception {
    private double amount;
    
    public InsufficientFundsException(double amount) {
        super(String.format("Insufficient funds. Missing %.2f", amount));
        this.amount = amount;
    }
    
    public double getAmount() {
        return amount;
    }
}

public class BankAccount {
    private double balance;
    private String accountNumber;
    
    public BankAccount(String accountNumber, double initialBalance) {
        this.accountNumber = accountNumber;
        this.balance = initialBalance;
    }
    
    public void withdraw(double amount) throws InsufficientFundsException {
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawal successful. New balance: " + balance);
        } else {
            double shortfall = amount - balance;
            throw new InsufficientFundsException(shortfall);
        }
    }
    
    public static void main(String[] args) {
        BankAccount account = new BankAccount("12345", 1000);
        try {
            account.withdraw(1500);
        } catch (InsufficientFundsException e) {
            System.out.println("Transaction failed: " + e.getMessage());
            System.out.println("You need " + e.getAmount() + " more to complete this transaction.");
        }
    }
}
```

### Practice Questions

1. Write a program that takes user input for division. Handle the case where a user might enter zero as a divisor.

2. Create a custom exception called `AgeVerificationException` that is thrown when a user enters an age less than 18. Write a method that validates age and uses this exception.

3. What's the difference between checked and unchecked exceptions? Write examples of both.

4. Write a program that demonstrates the use of multiple catch blocks and the order in which they should be placed.

5. Implement a resource management example using try-with-resources syntax for automatically closing resources.

## 2. Regular Expressions (Regex)

### What is Regex?
Regular expressions (regex) are special text strings for describing search patterns. In Java, they are primarily used for pattern matching with strings.

### Why use Regex?
- Validate input formats (email, phone numbers, etc.)
- Search and replace operations in text
- Extract information from strings
- Parse and transform text data
- Text filtering and formatting

### Where to use Regex?
- Form validation
- Data extraction and scraping
- Text processing applications
- Compiler design
- Search functionalities

### Syntax

#### Common Regex Patterns
- `.` - Matches any single character
- `^` - Matches beginning of line
- `$` - Matches end of line
- `[abc]` - Matches any one of the characters a, b, or c
- `[^abc]` - Matches any character except a, b, or c
- `a|b` - Matches either a or b
- `\d` - Matches a digit
- `\w` - Matches a word character
- `\s` - Matches a whitespace character
- `*` - Matches 0 or more occurrences
- `+` - Matches 1 or more occurrences
- `?` - Matches 0 or 1 occurrence
- `{n}` - Matches exactly n occurrences
- `{n,}` - Matches at least n occurrences
- `{n,m}` - Matches between n and m occurrences

#### Java Regex Methods
```java
// Pattern and Matcher classes
Pattern pattern = Pattern.compile("regex");
Matcher matcher = pattern.matcher("text to search");

// String class methods
boolean matches = string.matches("regex");
String replaced = string.replaceAll("regex", "replacement");
String[] parts = string.split("regex");
```

### Examples

#### Example 1: Email Validation
```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class EmailValidator {
    private static final String EMAIL_PATTERN = 
        "^[a-zA-Z0-9_+&*-]+(?:\\.[a-zA-Z0-9_+&*-]+)*@(?:[a-zA-Z0-9-]+\\.)+[a-zA-Z]{2,7}$";
    
    private static final Pattern pattern = Pattern.compile(EMAIL_PATTERN);
    
    public static boolean isValid(String email) {
        if (email == null) {
            return false;
        }
        Matcher matcher = pattern.matcher(email);
        return matcher.matches();
    }
    
    public static void main(String[] args) {
        String[] emails = {"user@domain.com", "invalid@", "invalid", "user.name@domain.co.in"};
        
        for (String email : emails) {
            System.out.println(email + " is " + (isValid(email) ? "valid" : "invalid"));
        }
    }
}
```

#### Example 2: Finding and Replacing Text
```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class RegexReplaceExample {
    public static void main(String[] args) {
        String text = "The price of the item is $25.99 and another item costs $10.50";
        
        // Find all prices in the text
        Pattern pricePattern = Pattern.compile("\\$([0-9]+\\.[0-9]+)");
        Matcher matcher = pricePattern.matcher(text);
        
        System.out.println("Original text: " + text);
        
        // Find and print all prices
        System.out.println("\nFound prices:");
        while (matcher.find()) {
            System.out.println("Price: $" + matcher.group(1));
        }
        
        // Replace prices with a 10% increase
        StringBuffer result = new StringBuffer();
        matcher.reset();
        
        while (matcher.find()) {
            double price = Double.parseDouble(matcher.group(1));
            double newPrice = price * 1.1; // 10% increase
            matcher.appendReplacement(result, "\\$" + String.format("%.2f", newPrice));
        }
        matcher.appendTail(result);
        
        System.out.println("\nText with 10% price increase: " + result.toString());
    }
}
```

### Practice Questions

1. Write a regex pattern to validate a phone number in the format: (XXX) XXX-XXXX.

2. Create a program that extracts all URLs from a given text.

3. Write a program that validates passwords with the following rules: at least 8 characters, must contain at least one uppercase letter, one lowercase letter, one number, and one special character.

4. Implement a function that uses regex to check if a date is in the format DD/MM/YYYY and is a valid date.

5. Write a program that identifies and counts all words in a text that begin with a vowel.

## 3. Threads

### What are Threads?
Threads are lightweight processes within a program that can execute concurrently. They allow multiple operations to overlap in execution, improving efficiency and responsiveness.

### Why use Threads?
- Improve application performance
- Handle multiple tasks simultaneously
- Utilize multi-core processors effectively
- Keep UI responsive while performing background tasks
- Handle asynchronous operations

### Where to use Threads?
- GUI applications to keep the interface responsive
- Server applications handling multiple client requests
- Applications performing I/O operations
- Background tasks like file processing
- Resource-intensive operations

### Syntax

#### Creating Threads

**Method 1: Extending Thread Class**
```java
class MyThread extends Thread {
    public void run() {
        // Code to be executed in this thread
    }
}

// Usage
MyThread thread = new MyThread();
thread.start();
```

**Method 2: Implementing Runnable Interface**
```java
class MyRunnable implements Runnable {
    public void run() {
        // Code to be executed in this thread
    }
}

// Usage
Thread thread = new Thread(new MyRunnable());
thread.start();
```

**Method 3: Using Lambda Expression (Java 8+)**
```java
Thread thread = new Thread(() -> {
    // Code to be executed in this thread
});
thread.start();
```

#### Thread Synchronization
```java
public synchronized void synchronizedMethod() {
    // Only one thread can execute this at a time
}

// Or using synchronized block
public void method() {
    synchronized(this) {
        // Synchronized block
    }
}
```

### Examples

#### Example 1: Basic Thread Implementation
```java
public class ThreadExample {
    public static void main(String[] args) {
        // Creating thread using Runnable
        Thread thread1 = new Thread(new Runnable() {
            @Override
            public void run() {
                for (int i = 1; i <= 5; i++) {
                    System.out.println("Thread 1: " + i);
                    try {
                        Thread.sleep(500);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        });
        
        // Creating thread using lambda (Java 8+)
        Thread thread2 = new Thread(() -> {
            for (int i = 1; i <= 5; i++) {
                System.out.println("Thread 2: " + i);
                try {
                    Thread.sleep(700);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        });
        
        // Start the threads
        thread1.start();
        thread2.start();
        
        // Main thread continues execution
        for (int i = 1; i <= 5; i++) {
            System.out.println("Main Thread: " + i);
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        
        System.out.println("Main thread is finished.");
    }
}
```

#### Example 2: Thread Synchronization
```java
public class BankAccount {
    private double balance;
    private final Object lock = new Object();
    
    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }
    
    public void deposit(double amount) {
        synchronized (lock) {
            System.out.println(Thread.currentThread().getName() + " is depositing " + amount);
            double newBalance = balance + amount;
            try {
                // Simulate processing time
                Thread.sleep(100);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            balance = newBalance;
            System.out.println(Thread.currentThread().getName() + " completed deposit. New balance: " + balance);
        }
    }
    
    public void withdraw(double amount) {
        synchronized (lock) {
            if (balance >= amount) {
                System.out.println(Thread.currentThread().getName() + " is withdrawing " + amount);
                double newBalance = balance - amount;
                try {
                    // Simulate processing time
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                balance = newBalance;
                System.out.println(Thread.currentThread().getName() + " completed withdrawal. New balance: " + balance);
            } else {
                System.out.println(Thread.currentThread().getName() + " insufficient funds. Current balance: " + balance);
            }
        }
    }
    
    public double getBalance() {
        return balance;
    }
    
    public static void main(String[] args) {
        BankAccount account = new BankAccount(1000);
        
        Runnable depositTask = () -> {
            for (int i = 0; i < 5; i++) {
                account.deposit(100);
            }
        };
        
        Runnable withdrawTask = () -> {
            for (int i = 0; i < 5; i++) {
                account.withdraw(100);
            }
        };
        
        Thread depositThread = new Thread(depositTask, "DepositThread");
        Thread withdrawThread = new Thread(withdrawTask, "WithdrawThread");
        
        depositThread.start();
        withdrawThread.start();
        
        try {
            depositThread.join();
            withdrawThread.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        
        System.out.println("Final balance: " + account.getBalance());
    }
}
```

### Practice Questions

1. Write a multi-threaded program that counts occurrences of a specific word in multiple text files concurrently.

2. Create a producer-consumer problem implementation using wait() and notify() methods.

3. Implement a thread pool that processes a collection of tasks concurrently.

4. Write a program that demonstrates a race condition and then fix it using proper synchronization.

5. Create a program that uses CountDownLatch to coordinate the start of multiple threads.

# Lambda Expressions and Advanced Sorting in Java

## Lambda Expressions

### What are Lambda Expressions?
Lambda expressions are a feature introduced in Java 8 that provide a clear and concise way to represent a method interface using an expression. They implement functional interfaces (interfaces with a single abstract method) and enable you to treat functionality as a method argument.

### Why Use Lambda Expressions?
1. **Concise Code**: Reduces boilerplate code compared to anonymous classes
2. **Functional Programming**: Enables functional programming concepts in Java
3. **Readability**: Makes code more readable and maintainable
4. **Parallel Processing**: Works well with streams for parallel processing
5. **API Integration**: Seamlessly works with the Stream API and Collections framework

### Where to Use Lambda Expressions?
1. **Event Handling**: Responding to UI events
2. **Stream Operations**: Filtering, mapping, and reducing collections
3. **Sorting**: Providing custom comparators
4. **Threading**: Running code in separate threads
5. **Callback Mechanisms**: Implementing callback functionality

### Syntax:
```java
// Basic lambda syntax
(parameters) -> expression

// For multiple statements
(parameters) -> {
    statement1;
    statement2;
    return result;
}
```

### Examples:

#### Example 1: Basic Lambda Expression
```java
import java.util.ArrayList;
import java.util.List;

public class BasicLambdaExample {
    public static void main(String[] args) {
        List<String> names = new ArrayList<>();
        names.add("Alice");
        names.add("Bob");
        names.add("Charlie");
        names.add("David");
        
        // Using lambda expression with forEach
        System.out.println("Names in the list:");
        names.forEach((name) -> System.out.println(name));
        
        // Filter names starting with 'A'
        System.out.println("\nNames starting with 'A':");
        names.stream()
             .filter(name -> name.startsWith("A"))
             .forEach(name -> System.out.println(name));
    }
}
```

#### Example 2: Lambda with Functional Interfaces
```java
import java.util.function.Predicate;
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.ArrayList;
import java.util.List;

public class FunctionalInterfacesExample {
    public static void main(String[] args) {
        List<Integer> numbers = new ArrayList<>();
        for (int i = 1; i <= 10; i++) {
            numbers.add(i);
        }
        
        // Predicate - returns boolean
        Predicate<Integer> isEven = n -> n % 2 == 0;
        
        // Consumer - accepts single input, returns no result
        Consumer<Integer> display = n -> System.out.print(n + " ");
        
        // Function - accepts one argument, produces one result
        Function<Integer, Integer> square = n -> n * n;
        
        System.out.println("Original numbers:");
        numbers.forEach(display);
        
        System.out.println("\n\nEven numbers:");
        numbers.stream()
               .filter(isEven)
               .forEach(display);
        
        System.out.println("\n\nSquared numbers:");
        numbers.stream()
               .map(square)
               .forEach(display);
    }
}
```

## Advanced Sorting in Java

### What is Advanced Sorting?
Advanced sorting in Java refers to custom and complex sorting operations that go beyond the basic natural ordering of elements. It involves using comparators, lambda expressions, and specialized APIs to sort collections based on multiple criteria or custom logic.

### Why Use Advanced Sorting?
1. **Custom Order**: Sort elements based on specific business requirements
2. **Multiple Criteria**: Sort by multiple properties or conditions
3. **Complex Objects**: Sort objects with multiple attributes
4. **Performance Optimization**: Choose sorting algorithms based on data characteristics
5. **Data Analysis**: Arrange data for better analysis and presentation

### Where to Use Advanced Sorting?
1. **Data Processing**: Organizing and analyzing large datasets
2. **User Interfaces**: Displaying data in a specific order
3. **Reports Generation**: Arranging data in reports
4. **Search Algorithms**: Improving search efficiency
5. **Database Operations**: In-memory sorting before database operations

### Methods for Advanced Sorting:

#### 1. Comparator Interface

Syntax:
```java
import java.util.Comparator;

// Create a comparator
Comparator<Type> comparator = new Comparator<Type>() {
    @Override
    public int compare(Type o1, Type o2) {
        // Comparison logic
        return result; // -1, 0, or 1
    }
};

// With lambda expression
Comparator<Type> comparator = (o1, o2) -> {
    // Comparison logic
    return result; // -1, 0, or 1
};
```

Example: Sorting with Comparator
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

class Person {
    private String name;
    private int age;
    
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public String getName() {
        return name;
    }
    
    public int getAge() {
        return age;
    }
    
    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}

public class ComparatorExample {
    public static void main(String[] args) {
        List<Person> people = new ArrayList<>();
        people.add(new Person("Alice", 25));
        people.add(new Person("Bob", 30));
        people.add(new Person("Charlie", 22));
        people.add(new Person("David", 28));
        
        System.out.println("Original list: " + people);
        
        // Sort by age using anonymous class
        Collections.sort(people, new Comparator<Person>() {
            @Override
            public int compare(Person p1, Person p2) {
                return Integer.compare(p1.getAge(), p2.getAge());
            }
        });
        
        System.out.println("Sorted by age (anonymous class): " + people);
        
        // Sort by name using lambda
        Collections.sort(people, (p1, p2) -> p1.getName().compareTo(p2.getName()));
        
        System.out.println("Sorted by name (lambda): " + people);
    }
}
```

#### 2. Comparing and Then Comparing

Syntax:
```java
import java.util.Comparator;

// Chaining multiple comparisons
Comparator<Type> comparator = Comparator
    .comparing(Type::getProperty1)
    .thenComparing(Type::getProperty2)
    .thenComparing(Type::getProperty3);
```

Example: Multiple Field Sorting
```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

class Student {
    private String firstName;
    private String lastName;
    private double gpa;
    
    public Student(String firstName, String lastName, double gpa) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.gpa = gpa;
    }
    
    public String getFirstName() {
        return firstName;
    }
    
    public String getLastName() {
        return lastName;
    }
    
    public double getGpa() {
        return gpa;
    }
    
    @Override
    public String toString() {
        return firstName + " " + lastName + " (GPA: " + gpa + ")";
    }
}

public class MultipleFieldSortingExample {
    public static void main(String[] args) {
        List<Student> students = new ArrayList<>();
        students.add(new Student("John", "Smith", 3.5));
        students.add(new Student("Alice", "Johnson", 3.8));
        students.add(new Student("John", "Doe", 3.2));
        students.add(new Student("Alice", "Brown", 3.8));
        
        System.out.println("Original list:");
        students.forEach(System.out::println);
        
        // Sort by last name, then first name, then GPA (descending)
        students.sort(
            Comparator.comparing(Student::getLastName)
                      .thenComparing(Student::getFirstName)
                      .thenComparing(Student::getGpa, Comparator.reverseOrder())
        );
        
        System.out.println("\nSorted by last name, first name, and GPA (descending):");
        students.forEach(System.out::println);
    }
}
```

#### 3. Reversed and Nulls Handling

Syntax:
```java
// Reverse order
Comparator<Type> reversed = Comparator.comparing(Type::getProperty).reversed();

// Null handling
Comparator<Type> withNulls = Comparator.nullsFirst(
    Comparator.comparing(Type::getProperty)
);
```

Example: Reversed Order and Null Handling
```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

class Product {
    private String name;
    private Double price; // Using Double instead of double to allow null
    
    public Product(String name, Double price) {
        this.name = name;
        this.price = price;
    }
    
    public String getName() {
        return name;
    }
    
    public Double getPrice() {
        return price;
    }
    
    @Override
    public String toString() {
        return name + " ($" + (price != null ? price : "N/A") + ")";
    }
}

public class NullHandlingExample {
    public static void main(String[] args) {
        List<Product> products = new ArrayList<>();
        products.add(new Product("Laptop", 1200.0));
        products.add(new Product("Phone", 800.0));
        products.add(new Product("Headphones", null)); // Unknown price
        products.add(new Product("Tablet", 500.0));
        products.add(new Product("Charger", null)); // Unknown price
        
        System.out.println("Original list:");
        products.forEach(System.out::println);
        
        // Sort by price (descending) with nulls last
        products.sort(
            Comparator.comparing(Product::getPrice, Comparator.nullsLast(Comparator.reverseOrder()))
        );
        
        System.out.println("\nSorted by price (descending) with nulls last:");
        products.forEach(System.out::println);
        
        // Sort by price (ascending) with nulls first
        products.sort(
            Comparator.comparing(Product::getPrice, Comparator.nullsFirst(Comparator.naturalOrder()))
        );
        
        System.out.println("\nSorted by price (ascending) with nulls first:");
        products.forEach(System.out::println);
    }
}
```

#### 4. Sorting with Streams

Syntax:
```java
import java.util.stream.Collectors;

// Sorting with streams
List<Type> sorted = list.stream()
    .sorted(Comparator.comparing(Type::getProperty))
    .collect(Collectors.toList());
```

Example: Sorting with Streams
```java
import java.util.Arrays;
import java.util.Comparator;
import java.util.List;
import java.util.stream.Collectors;

class Employee {
    private String name;
    private String department;
    private double salary;
    
    public Employee(String name, String department, double salary) {
        this.name = name;
        this.department = department;
        this.salary = salary;
    }
    
    public String getName() {
        return name;
    }
    
    public String getDepartment() {
        return department;
    }
    
    public double getSalary() {
        return salary;
    }
    
    @Override
    public String toString() {
        return name + " (" + department + ", $" + salary + ")";
    }
}

public class StreamSortingExample {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee("John", "IT", 75000),
            new Employee("Alice", "HR", 65000),
            new Employee("Bob", "IT", 80000),
            new Employee("David", "Finance", 90000),
            new Employee("Emily", "HR", 68000)
        );
        
        System.out.println("Original employees:");
        employees.forEach(System.out::println);
        
        // Group by department and sort by salary within each group
        System.out.println("\nEmployees grouped by department and sorted by salary:");
        employees.stream()
                 .collect(Collectors.groupingBy(Employee::getDepartment))
                 .forEach((dept, emps) -> {
                     System.out.println("\nDepartment: " + dept);
                     emps.stream()
                         .sorted(Comparator.comparing(Employee::getSalary).reversed())
                         .forEach(System.out::println);
                 });
        
        // Top 3 highest paid employees
        System.out.println("\nTop 3 highest paid employees:");
        employees.stream()
                 .sorted(Comparator.comparing(Employee::getSalary).reversed())
                 .limit(3)
                 .forEach(System.out::println);
    }
}
```

#### 5. Custom Sorting Logic

Example: Complex Custom Sorting
```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

class Task {
    public enum Priority { LOW, MEDIUM, HIGH, CRITICAL }
    
    private String title;
    private Priority priority;
    private boolean completed;
    private int estimatedHours;
    
    public Task(String title, Priority priority, boolean completed, int estimatedHours) {
        this.title = title;
        this.priority = priority;
        this.completed = completed;
        this.estimatedHours = estimatedHours;
    }
    
    public String getTitle() {
        return title;
    }
    
    public Priority getPriority() {
        return priority;
    }
    
    public boolean isCompleted() {
        return completed;
    }
    
    public int getEstimatedHours() {
        return estimatedHours;
    }
    
    @Override
    public String toString() {
        return title + " [" + priority + ", " + 
               (completed ? "Completed" : "Pending") + 
               ", " + estimatedHours + "h]";
    }
}

public class CustomSortingExample {
    public static void main(String[] args) {
        List<Task> tasks = new ArrayList<>();
        tasks.add(new Task("Fix bug in login module", Task.Priority.HIGH, false, 4));
        tasks.add(new Task("Update documentation", Task.Priority.LOW, false, 2));
        tasks.add(new Task("Deploy to production", Task.Priority.CRITICAL, false, 3));
        tasks.add(new Task("Review code", Task.Priority.MEDIUM, true, 2));
        tasks.add(new Task("Add new feature", Task.Priority.HIGH, false, 8));
        tasks.add(new Task("Refactor utils class", Task.Priority.MEDIUM, false, 5));
        
        System.out.println("Original task list:");
        tasks.forEach(System.out::println);
        
        // Complex custom sorting:
        // 1. Incomplete tasks before completed
        // 2. Sort by priority (CRITICAL > HIGH > MEDIUM > LOW)
        // 3. For same priority, sort by estimated hours (ascending)
        Comparator<Task> customTaskComparator = Comparator
            // First by completion status (incomplete first)
            .comparing(Task::isCompleted)
            // Then by priority (reversed because CRITICAL is highest)
            .thenComparing(Task::getPriority, Comparator.reverseOrder())
            // Then by estimated hours (ascending)
            .thenComparing(Task::getEstimatedHours);
        
        tasks.sort(customTaskComparator);
        
        System.out.println("\nTasks sorted by custom business logic:");
        tasks.forEach(System.out::println);
    }
}
```

## Practice Questions

### Question 1: Basic Lambda Expression
Write a program that uses lambda expressions to filter a list of integers to find all numbers that are divisible by 3 and greater than 10.

### Question 2: Functional Interfaces with Lambda
Create a program that demonstrates the use of the following functional interfaces with lambda expressions:
- Predicate: to check if a string is longer than 5 characters
- Consumer: to print a string in uppercase
- Function: to count the number of vowels in a string

### Question 3: Sorting Person Objects
Create a class `Person` with fields for name, age, and city. Write a program that sorts a list of Person objects by:
- Age in ascending order
- Name in alphabetical order
- City in alphabetical order and then by age in descending order

### Question 4: Null Handling and Custom Comparator
Create a program with a list of products where some products have null prices. Implement sorting that:
- Places products with null prices at the beginning
- Sorts the remaining products by price in descending order

### Question 5: Advanced Stream Sorting
Create a program that processes a list of employees with fields for name, department, salary, and years of experience. Use streams to:
- Group employees by department
- For each department, find the employee with the highest salary
- Sort departments by their average salary in descending order