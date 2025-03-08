# Java OOP Concepts

## 1. Classes and Objects

### What is a Class?
A class is a blueprint or template that defines the properties (attributes) and behaviors (methods) that objects of its type will have. It serves as a structure for creating objects.

### Why use Classes?
- Classes provide a way to structure code by grouping related data and functions
- They enable object-oriented programming paradigms like inheritance, encapsulation, and polymorphism
- They make code more modular, reusable, and maintainable

### Where to use Classes?
- When you need to create multiple instances (objects) with similar properties and behaviors
- When modeling real-world entities in your program
- When organizing related functionality into logical units

### Syntax
```java
public class ClassName {
    // Attributes (variables)
    dataType attributeName1;
    dataType attributeName2;
    
    // Methods
    returnType methodName1(parameters) {
        // method body
    }
    
    returnType methodName2(parameters) {
        // method body
    }
}
```

### What is an Object?
An object is an instance of a class. It has a state (defined by its attributes) and behavior (defined by its methods).

### Syntax for Creating Objects
```java
ClassName objectName = new ClassName();
```

### Examples

**Example 1: Creating a simple Car class and objects**
```java
public class Car {
    // Attributes
    String brand;
    String model;
    int year;
    
    // Method
    void displayInfo() {
        System.out.println("Car: " + year + " " + brand + " " + model);
    }
}

// Creating objects
public class Main {
    public static void main(String[] args) {
        // Create first car object
        Car car1 = new Car();
        car1.brand = "Toyota";
        car1.model = "Corolla";
        car1.year = 2022;
        car1.displayInfo();
        
        // Create second car object
        Car car2 = new Car();
        car2.brand = "Honda";
        car2.model = "Civic";
        car2.year = 2023;
        car2.displayInfo();
    }
}
```

**Example 2: Student class with multiple attributes and methods**
```java
public class Student {
    // Attributes
    String name;
    int id;
    double gpa;
    
    // Methods
    void study() {
        System.out.println(name + " is studying");
    }
    
    void displayDetails() {
        System.out.println("Student ID: " + id);
        System.out.println("Name: " + name);
        System.out.println("GPA: " + gpa);
    }
}

// Using the Student class
public class Main {
    public static void main(String[] args) {
        Student student1 = new Student();
        student1.name = "John";
        student1.id = 101;
        student1.gpa = 3.8;
        
        student1.displayDetails();
        student1.study();
    }
}
```

### Practice Questions

1. Create a `Book` class with attributes for title, author, and pages. Include methods to display book information and check if it's a long book (over 300 pages).

2. Write a program that creates three different `Rectangle` objects with length and width attributes. Include methods to calculate area and perimeter.

3. Design a `BankAccount` class with attributes for account number, holder name, and balance. Implement methods for deposit, withdrawal, and checking balance.

4. Create a `MobilePhone` class with attributes for brand, model, and battery percentage. Include methods to make calls (reduces battery by 5%), charge phone (increases battery), and display phone status.

5. Write a `Temperature` class that can store a temperature value and has methods to convert between Celsius and Fahrenheit scales.

## 2. Class Attributes

### What are Class Attributes?
Class attributes (also called fields, variables, or properties) are data members that belong to a class. They represent the state or characteristics of the class and its objects.

### Why use Class Attributes?
- To store data that describes objects
- To maintain the state of objects throughout their lifecycle
- To provide data that methods can operate on

### Where to use Class Attributes?
- When you need to track properties of objects
- When you need to share data across multiple methods within a class
- When implementing encapsulation to protect data

### Syntax
```java
class ClassName {
    // Access modifier + data type + variable name
    private dataType attributeName;
    public dataType attributeName2;
    protected dataType attributeName3;
    dataType attributeName4; // default access
    
    // Static attribute (belongs to the class, not objects)
    static dataType staticAttributeName;
    
    // Final attribute (constant)
    final dataType CONSTANT_NAME = value;
}
```

### Examples

**Example 1: Different types of attributes**
```java
public class Employee {
    // Instance variables (unique to each object)
    private String name;
    private int id;
    private double salary;
    
    // Static variable (shared among all objects)
    static String companyName = "ABC Corp";
    
    // Constant
    final int VACATION_DAYS = 20;
    
    // Method to display employee details
    void displayDetails() {
        System.out.println("ID: " + id);
        System.out.println("Name: " + name);
        System.out.println("Company: " + companyName);
        System.out.println("Vacation days: " + VACATION_DAYS);
    }
}
```

**Example 2: Using class attributes**
```java
public class Circle {
    // Attributes
    double radius;
    String color;
    
    // Static attribute
    static final double PI = 3.14159;
    
    // Method using attributes
    double calculateArea() {
        return PI * radius * radius;
    }
    
    double calculateCircumference() {
        return 2 * PI * radius;
    }
}

// Using the Circle class
public class Main {
    public static void main(String[] args) {
        Circle circle1 = new Circle();
        circle1.radius = 5.0;
        circle1.color = "Red";
        
        System.out.println("Area: " + circle1.calculateArea());
        System.out.println("Circumference: " + circle1.calculateCircumference());
        
        // Accessing static attribute
        System.out.println("PI value: " + Circle.PI);
    }
}
```

### Practice Questions

1. Create a `Counter` class with private instance variables for count and a static variable to track the total number of Counter objects created.

2. Design a `Student` class with attributes for name, ID, and an array of grades. Add a static attribute to track the highest GPA among all students.

3. Create a `Car` class with instance variables for make, model, and year. Add a static variable for the number of cars manufactured and a final variable for the VIN (Vehicle Identification Number).

4. Implement a `Library` class with attributes for books available, books borrowed, and a static attribute for the total number of books across all libraries.

5. Design a `Product` class with attributes for name, price, and stock quantity. Include a static variable for the total inventory value of all products.

## 3. Class Methods

### What are Class Methods?
Class methods are functions defined within a class that describe the behaviors of objects of that class. They can access and manipulate the class attributes and perform operations.

### Why use Class Methods?
- To define behaviors for objects
- To manipulate attribute values
- To implement functionality that operates on the object's state
- To provide interfaces for interacting with objects

### Where to use Class Methods?
- When defining operations that an object can perform
- When implementing getters and setters for encapsulation
- When providing utility functions related to the class
- When implementing business logic

### Syntax
```java
class ClassName {
    // Instance method
    returnType methodName(parameters) {
        // method body
    }
    
    // Static method (belongs to the class, not objects)
    static returnType staticMethodName(parameters) {
        // method body
    }
    
    // Void method (returns nothing)
    void methodWithNoReturn() {
        // method body
    }
}
```

### Examples

**Example 1: Instance and Static Methods**
```java
public class Calculator {
    // Instance variables
    private double result;
    
    // Instance methods
    void add(double number) {
        result += number;
    }
    
    void subtract(double number) {
        result -= number;
    }
    
    double getResult() {
        return result;
    }
    
    void clear() {
        result = 0;
    }
    
    // Static methods
    static double square(double number) {
        return number * number;
    }
    
    static double cube(double number) {
        return number * number * number;
    }
}

// Using the Calculator class
public class Main {
    public static void main(String[] args) {
        // Using instance methods
        Calculator calc = new Calculator();
        calc.add(10);
        calc.add(5);
        calc.subtract(3);
        System.out.println("Result: " + calc.getResult());
        
        // Using static methods (no object needed)
        System.out.println("Square of 4: " + Calculator.square(4));
        System.out.println("Cube of 3: " + Calculator.cube(3));
    }
}
```

**Example 2: Methods with Parameters and Return Values**
```java
public class StringHelper {
    // Method with parameters and return value
    String concatenate(String str1, String str2) {
        return str1 + str2;
    }
    
    // Method with parameters but no return value
    void printRepeated(String text, int times) {
        for (int i = 0; i < times; i++) {
            System.out.println(text);
        }
    }
    
    // Static utility method
    static boolean isPalindrome(String text) {
        String clean = text.replaceAll("\\s+", "").toLowerCase();
        int length = clean.length();
        
        for (int i = 0; i < length / 2; i++) {
            if (clean.charAt(i) != clean.charAt(length - 1 - i)) {
                return false;
            }
        }
        
        return true;
    }
}
```

### Practice Questions

1. Create a `MathUtils` class with static methods for calculating the factorial of a number, checking if a number is prime, and finding the GCD of two numbers.

2. Design a `ShoppingCart` class with methods to add items, remove items, calculate the total price, and apply a discount.

3. Implement a `DateFormatter` class with methods to format dates in different styles (e.g., "dd/mm/yyyy", "month day, year", etc.).

4. Create a `StringAnalyzer` class with methods to count vowels, consonants, and special characters in a string.

5. Design a `Shape` class with methods to calculate area and perimeter for different shapes (circle, rectangle, triangle).

## 4. Constructors

### What are Constructors?
Constructors are special methods in a class that are called when an object of the class is created. They initialize the newly created object and its attributes.

### Why use Constructors?
- To initialize object attributes with default or specified values
- To ensure objects are in a valid state when created
- To perform any setup operations required for the object
- To control how objects are created

### Where to use Constructors?
- In class definitions to control object initialization
- When objects need specific initialization based on parameters
- When implementing constructor overloading for different initialization scenarios

### Syntax
```java
class ClassName {
    // Default constructor (no parameters)
    public ClassName() {
        // initialization code
    }
    
    // Parameterized constructor
    public ClassName(dataType param1, dataType param2) {
        // initialization using parameters
    }
    
    // Constructor overloading - multiple constructors with different parameters
}
```

### Examples

**Example 1: Default and Parameterized Constructors**
```java
public class Person {
    String name;
    int age;
    
    // Default constructor
    public Person() {
        name = "Unknown";
        age = 0;
    }
    
    // Parameterized constructor
    public Person(String personName, int personAge) {
        name = personName;
        age = personAge;
    }
    
    void displayInfo() {
        System.out.println("Name: " + name + ", Age: " + age);
    }
}

// Using constructors
public class Main {
    public static void main(String[] args) {
        // Using default constructor
        Person person1 = new Person();
        person1.displayInfo();
        
        // Using parameterized constructor
        Person person2 = new Person("John", 25);
        person2.displayInfo();
    }
}
```

**Example 2: Constructor Overloading**
```java
public class Box {
    double width;
    double height;
    double depth;
    
    // Constructor for a cube (all sides equal)
    public Box(double side) {
        width = height = depth = side;
    }
    
    // Constructor for a rectangular box
    public Box(double w, double h, double d) {
        width = w;
        height = h;
        depth = d;
    }
    
    // Default constructor
    public Box() {
        width = height = depth = 1;
    }
    
    // Calculate volume
    double volume() {
        return width * height * depth;
    }
}

// Using the Box class
public class Main {
    public static void main(String[] args) {
        // Create boxes using different constructors
        Box box1 = new Box();  // Default 1x1x1
        Box box2 = new Box(5);  // Cube 5x5x5
        Box box3 = new Box(2, 3, 4);  // Box 2x3x4
        
        System.out.println("Box 1 volume: " + box1.volume());
        System.out.println("Box 2 volume: " + box2.volume());
        System.out.println("Box 3 volume: " + box3.volume());
    }
}
```

### Practice Questions

1. Create a `BankAccount` class with constructors for initializing accounts with or without an initial balance. Include methods for deposit, withdrawal, and balance inquiry.

2. Design a `Book` class with multiple constructors to initialize books with different combinations of title, author, publisher, and year of publication.

3. Implement a `Student` class with constructors for creating student objects with name, ID, and an array of courses they're enrolled in.

4. Create a `Point` class to represent a point in 2D space with appropriate constructors and methods to calculate distance from origin and distance between two points.

5. Design a `Pizza` class with constructors for different sizes and toppings. Include a method to calculate the price based on size and number of toppings.

## 5. Modifiers

### What are Modifiers?
Modifiers are keywords that change the properties of a class, method, or variable. Java has two types of modifiers: access modifiers and non-access modifiers.

### Why use Modifiers?
- To control the visibility and accessibility of classes, methods, and variables
- To specify special behaviors like immutability, inheritance prevention, or class-level properties
- To enforce encapsulation and information hiding
- To enable polymorphism and other OOP features

### Where to use Modifiers?
- Before class declarations to control class visibility and behavior
- Before variable declarations to control their accessibility and properties
- Before method declarations to control their accessibility and behavior

### Syntax

**Access Modifiers:**
```java
// Classes
public class PublicClass { }
class DefaultClass { }  // default/package-private

// Variables and Methods
public int publicVar;
private int privateVar;
protected int protectedVar;
int defaultVar;  // default/package-private

public void publicMethod() { }
private void privateMethod() { }
protected void protectedMethod() { }
void defaultMethod() { }  // default/package-private
```

**Non-Access Modifiers:**
```java
// Class modifiers
final class FinalClass { }  // cannot be subclassed
abstract class AbstractClass { }  // cannot be instantiated

// Method modifiers
final void finalMethod() { }  // cannot be overridden
abstract void abstractMethod();  // must be implemented by subclasses
static void staticMethod() { }  // belongs to class, not objects
synchronized void synchronizedMethod() { }  // thread-safe

// Variable modifiers
final int CONSTANT = 100;  // cannot be changed
static int classVariable;  // belongs to class, not objects
volatile int volatileVar;  // special handling for threads
transient int transientVar;  // not included in serialization
```

### Access Modifier Visibility Table

| Modifier | Class | Package | Subclass | World |
|----------|-------|---------|----------|-------|
| public | Yes | Yes | Yes | Yes |
| protected | Yes | Yes | Yes | No |
| default | Yes | Yes | No | No |
| private | Yes | No | No | No |

### Examples

**Example 1: Access Modifiers**
```java
public class Account {
    // Access modifiers for variables
    private double balance;  // Accessible only within this class
    protected String owner;  // Accessible in this class and subclasses
    public String type;  // Accessible everywhere
    int transactions;  // Default access - accessible in this package
    
    // Access modifiers for methods
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            transactions++;
        }
    }
    
    private void updateTransactionLog() {
        System.out.println("Transaction logged");
    }
    
    protected double getBalance() {
        return balance;
    }
}
```

**Example 2: Non-Access Modifiers**
```java
public class MathConstants {
    // final variable (constant)
    public static final double PI = 3.14159;
    
    // static variable (class variable)
    public static int calculationCount = 0;
    
    // static method
    public static double square(double num) {
        calculationCount++;
        return num * num;
    }
    
    // final method
    public final double calculateCircleArea(double radius) {
        return PI * radius * radius;
    }
}

// Abstract class example
abstract class Shape {
    protected String color;
    
    // Constructor
    public Shape(String color) {
        this.color = color;
    }
    
    // Abstract method (must be implemented by subclasses)
    public abstract double calculateArea();
    
    // Concrete method
    public String getColor() {
        return color;
    }
}

// Concrete subclass implementing abstract method
class Circle extends Shape {
    private double radius;
    
    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }
    
    // Implementation of abstract method
    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}
```

### Practice Questions

1. Create a `Vehicle` class with private attributes for make, model, and year. Include appropriate getters and setters and a final method that cannot be overridden.

2. Design an `Animal` abstract class with abstract methods for making sounds and eating. Create two concrete subclasses that implement these methods.

3. Implement a `Database` class with private connection details, a static connection counter, and synchronized methods for thread-safe operations.

4. Create a `Configuration` class with private static final variables for application settings and public static methods to access these settings.

5. Design a `Person` class with private attributes, protected methods that subclasses can override, and a final method that cannot be overridden.

## 6. Encapsulation

### What is Encapsulation?
Encapsulation is one of the four fundamental OOP concepts. It is the practice of hiding the internal state (attributes) of an object and requiring all interaction to be performed through an object's methods.

### Why use Encapsulation?
- To protect data from unauthorized access and modification
- To maintain the integrity of object state
- To hide implementation details and expose only necessary functionality
- To make code more maintainable by controlling how data is accessed and modified
- To reduce dependencies between different parts of a program

### Where to use Encapsulation?
- When you want to control how data is accessed and modified
- When implementing data validation for attribute values
- When you need to change the internal implementation without affecting client code
- When protecting sensitive information

### Syntax
```java
public class ClassName {
    // Private attributes
    private dataType attribute1;
    private dataType attribute2;
    
    // Getters
    public dataType getAttribute1() {
        return attribute1;
    }
    
    // Setters
    public void setAttribute1(dataType value) {
        // Optional validation
        if (validationCondition) {
            this.attribute1 = value;
        }
    }
}
```

### Examples

**Example 1: Basic Encapsulation with Getters and Setters**
```java
public class BankAccount {
    // Private attributes
    private String accountNumber;
    private String accountHolder;
    private double balance;
    
    // Constructor
    public BankAccount(String accountNumber, String accountHolder) {
        this.accountNumber = accountNumber;
        this.accountHolder = accountHolder;
        this.balance = 0.0;
    }
    
    // Getters
    public String getAccountNumber() {
        return accountNumber;
    }
    
    public String getAccountHolder() {
        return accountHolder;
    }
    
    public double getBalance() {
        return balance;
    }
    
    // Setters with validation
    public void setAccountHolder(String accountHolder) {
        if (accountHolder != null && !accountHolder.isEmpty()) {
            this.accountHolder = accountHolder;
        }
    }
    
    // No setter for account number (immutable)
    
    // Methods to modify balance
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println(amount + " deposited successfully");
        } else {
            System.out.println("Invalid deposit amount");
        }
    }
    
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println(amount + " withdrawn successfully");
        } else {
            System.out.println("Invalid withdrawal amount or insufficient funds");
        }
    }
}

// Using the BankAccount class
public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount("123456789", "John Doe");
        
        // Using getters
        System.out.println("Account Holder: " + account.getAccountHolder());
        System.out.println("Account Number: " + account.getAccountNumber());
        System.out.println("Balance: $" + account.getBalance());
        
        // Using methods to modify state
        account.deposit(1000);
        account.withdraw(500);
        
        // Using setter
        account.setAccountHolder("John Smith");
        
        // Final state
        System.out.println("Updated Account Holder: " + account.getAccountHolder());
        System.out.println("Current Balance: $" + account.getBalance());
    }
}
```

**Example 2: Encapsulation with Data Validation**
```java
public class Employee {
    private int id;
    private String name;
    private int age;
    private double salary;
    
    // Constructor
    public Employee(int id, String name, int age, double salary) {
        this.id = id;
        this.name = name;
        setAge(age);  // Using setter for validation
        setSalary(salary);  // Using setter for validation
    }
    
    // Getters
    public int getId() {
        return id;
    }
    
    public String getName() {
        return name;
    }
    
    public int getAge() {
        return age;
    }
    
    public double getSalary() {
        return salary;
    }
    
    // Setters with validation
    public void setName(String name) {
        if (name != null && !name.isEmpty()) {
            this.name = name;
        } else {
            System.out.println("Invalid name");
        }
    }
    
    public void setAge(int age) {
        if (age >= 18 && age <= 65) {
            this.age = age;
        } else {
            System.out.println("Invalid age. Must be between 18 and 65.");
            this.age = 18;  // Default value
        }
    }
    
    public void setSalary(double salary) {
        if (salary > 0) {
            this.salary = salary;
        } else {
            System.out.println("Invalid salary");
            this.salary = 0;
        }
    }
    
    // Method to calculate annual salary
    public double getAnnualSalary() {
        return salary * 12;
    }
    
    // Method to give raise
    public void raiseSalary(double percentage) {
        if (percentage > 0) {
            double raiseAmount = salary * percentage / 100;
            salary += raiseAmount;
            System.out.println("Salary raised by " + percentage + "%");
        } else {
            System.out.println("Invalid raise percentage");
        }
    }
}
```

### Practice Questions

1. Create a `Product` class with encapsulated attributes for ID, name, price, and stock. Include validation in setters (e.g., price cannot be negative).

2. Design a `Student` class with private attributes for name, ID, and grades. Include methods to add grades, calculate GPA, and display student information.

3. Implement a `CreditCard` class with private attributes for card number, holder name, expiration date, and CVV. Only show masked versions of sensitive data through getters.

4. Create a `HealthProfile` class with encapsulated attributes for patient information (name, age, height, weight). Include methods to calculate BMI and determine if the BMI is in the healthy range.

5. Design a `SavingsAccount` class with private attributes for balance, interest rate, and transaction history. Include methods for deposit, withdrawal, and calculating interest, with appropriate validation.

# Java Advanced OOP Concepts

## 1. Packages and API

### What are Packages?
Packages in Java are a way to organize classes, interfaces, and sub-packages. They act as containers for classes and provide a namespace mechanism to avoid name conflicts. A package is essentially a directory structure that organizes your Java projects.

### Why use Packages?
- To organize related classes and interfaces
- To avoid naming conflicts through unique namespaces
- To control access through package-level visibility
- To make classes easier to find and maintain
- To provide reusable components that can be imported into other projects

### Where to use Packages?
- When developing large applications with many classes
- When creating libraries for reuse
- When collaborating with other developers
- When organizing code by functionality or domain

### Syntax

**Creating a package:**
```java
// Declare package at the top of the file
package com.company.project.module;

// Class definition
public class MyClass {
    // Class members
}
```

**Importing and using a package:**
```java
// Import a specific class
import packageName.ClassName;

// Import all classes from a package
import packageName.*;

// Using a fully qualified name without import
packageName.ClassName object = new packageName.ClassName();
```

### What is an API?
An API (Application Programming Interface) is a set of classes, interfaces, and methods that allows programmers to access certain features or data. In Java, the standard API (Java API) is a collection of packages that provide pre-built classes and interfaces for common programming tasks.

### Examples

**Example 1: Creating and Using a Custom Package**
```java
// File: com/mycompany/math/Calculator.java
package com.mycompany.math;

public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
    
    public int subtract(int a, int b) {
        return a - b;
    }
    
    public int multiply(int a, int b) {
        return a * b;
    }
    
    public double divide(int a, int b) {
        if (b == 0) {
            throw new ArithmeticException("Division by zero");
        }
        return (double) a / b;
    }
}

// File: com/mycompany/app/Main.java
package com.mycompany.app;

import com.mycompany.math.Calculator;

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        
        System.out.println("10 + 5 = " + calc.add(10, 5));
        System.out.println("10 - 5 = " + calc.subtract(10, 5));
        System.out.println("10 * 5 = " + calc.multiply(10, 5));
        System.out.println("10 / 5 = " + calc.divide(10, 5));
    }
}
```

**Example 2: Using Java Standard API**
```java
// File: ApiExample.java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Date;
import java.text.SimpleDateFormat;
import java.util.Scanner;

public class ApiExample {
    public static void main(String[] args) {
        // Using ArrayList from java.util package
        ArrayList<String> names = new ArrayList<>();
        names.add("John");
        names.add("Alice");
        names.add("Bob");
        
        // Using Collections class
        Collections.sort(names);
        System.out.println("Sorted names: " + names);
        
        // Using Date and SimpleDateFormat
        Date currentDate = new Date();
        SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        System.out.println("Current date: " + dateFormat.format(currentDate));
        
        // Using Scanner for input
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter your name: ");
        String input = scanner.nextLine();
        System.out.println("Hello, " + input + "!");
        scanner.close();
    }
}
```

### Practice Questions

1. Create a package structure `com.bookstore` with separate subpackages for `model`, `service`, and `view`. Implement a `Book` class in the model package and use it in a class in the service package.

2. Write a program that uses at least three different classes from the `java.util` package to manipulate a collection of strings.

3. Create a utility package with classes for different mathematical operations (basic arithmetic, statistics, geometry). Use these classes in a main program.

4. Implement a simple text processing application using classes from the `java.io` package to read from and write to text files.

5. Create a package with a class that has both public and package-private methods. Demonstrate how access is affected when using this class from within the same package and from a different package.

## 2. Inheritance

### What is Inheritance?
Inheritance is a fundamental OOP concept where a class (subclass/derived class) can inherit attributes and methods from another class (superclass/base class). It represents an "is-a" relationship between classes.

### Why use Inheritance?
- To promote code reusability
- To establish a hierarchy of classes
- To extend functionality of existing classes
- To achieve method overriding (runtime polymorphism)
- To organize classes with common attributes and behaviors

### Where to use Inheritance?
- When multiple classes share common attributes and behaviors
- When creating specialized versions of existing classes
- When building frameworks and class hierarchies
- When implementing "is-a" relationships (e.g., a Car is a Vehicle)

### Syntax
```java
// Base class / Parent class / Superclass
class Parent {
    // attributes and methods
}

// Derived class / Child class / Subclass
class Child extends Parent {
    // additional attributes and methods
    // can override parent methods
}
```

### Examples

**Example 1: Basic Inheritance**
```java
// Base class
class Vehicle {
    protected String brand;
    protected String model;
    protected int year;
    
    public Vehicle(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }
    
    public void display() {
        System.out.println("Brand: " + brand);
        System.out.println("Model: " + model);
        System.out.println("Year: " + year);
    }
    
    public void start() {
        System.out.println("Starting the vehicle...");
    }
}

// Derived class
class Car extends Vehicle {
    private int doors;
    private String fuelType;
    
    public Car(String brand, String model, int year, int doors, String fuelType) {
        super(brand, model, year);  // Call to parent constructor
        this.doors = doors;
        this.fuelType = fuelType;
    }
    
    // Override parent method
    @Override
    public void display() {
        super.display();  // Call parent method
        System.out.println("Doors: " + doors);
        System.out.println("Fuel Type: " + fuelType);
    }
    
    // New method in subclass
    public void drift() {
        System.out.println("The car is drifting!");
    }
}

// Testing the inheritance
public class Main {
    public static void main(String[] args) {
        Car myCar = new Car("Toyota", "Corolla", 2022, 4, "Gasoline");
        myCar.start();  // Inherited method
        myCar.display();  // Overridden method
        myCar.drift();  // New method
    }
}
```

**Example 2: Multilevel Inheritance**
```java
// Base class
class Animal {
    protected String name;
    
    public Animal(String name) {
        this.name = name;
    }
    
    public void eat() {
        System.out.println(name + " is eating");
    }
    
    public void sleep() {
        System.out.println(name + " is sleeping");
    }
}

// Intermediate derived class
class Mammal extends Animal {
    protected String furColor;
    
    public Mammal(String name, String furColor) {
        super(name);
        this.furColor = furColor;
    }
    
    public void giveBirth() {
        System.out.println(name + " is giving birth to live young");
    }
}

// Final derived class
class Dog extends Mammal {
    private String breed;
    
    public Dog(String name, String furColor, String breed) {
        super(name, furColor);
        this.breed = breed;
    }
    
    public void bark() {
        System.out.println(name + " is barking");
    }
    
    public void fetch() {
        System.out.println(name + " is fetching");
    }
    
    @Override
    public void eat() {
        System.out.println(name + " the dog is eating dog food");
    }
    
    public void displayDetails() {
        System.out.println("Name: " + name);
        System.out.println("Fur Color: " + furColor);
        System.out.println("Breed: " + breed);
    }
}

// Testing multilevel inheritance
public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog("Rex", "Brown", "German Shepherd");
        
        // Methods from Animal (base class)
        myDog.eat();
        myDog.sleep();
        
        // Method from Mammal (intermediate class)
        myDog.giveBirth();
        
        // Methods from Dog class
        myDog.bark();
        myDog.fetch();
        myDog.displayDetails();
    }
}
```

### Practice Questions

1. Create a class hierarchy for shapes with a base class `Shape` and derived classes `Circle`, `Rectangle`, and `Triangle`. Include appropriate attributes and methods for calculating area and perimeter.

2. Implement an `Employee` hierarchy with a base class and specialized classes like `Manager`, `Developer`, and `SalesPerson`. Include methods for calculating salary that are overridden in each subclass.

3. Design a `BankAccount` hierarchy with a base class and derived classes like `SavingsAccount`, `CheckingAccount`, and `FixedDepositAccount`. Override methods for deposit, withdrawal, and interest calculation.

4. Create a hierarchy for electronic devices with `Device` as the base class and `Phone`, `Laptop`, and `Tablet` as derived classes. Include appropriate attributes and methods that demonstrate inheritance and overriding.

5. Implement a `Person` class with derived classes `Student` and `Teacher`. Each should have appropriate attributes and methods, including some that override the parent class methods.

## 3. Polymorphism

### What is Polymorphism?
Polymorphism (from Greek meaning "many forms") is the ability of an object to take on many forms. In Java, polymorphism allows objects of different classes to be treated as objects of a common superclass, and the specific method implementation to be determined at runtime.

### Why use Polymorphism?
- To increase code flexibility and reusability
- To implement "one interface, multiple implementations"
- To simplify code that deals with multiple related classes
- To create more modular and extensible designs
- To enable dynamic method binding (runtime polymorphism)

### Where to use Polymorphism?
- When designing class hierarchies with shared behaviors
- When implementing frameworks that need to handle various subtypes
- When creating pluggable or extensible components
- When developing methods that should work with multiple object types

### Types of Polymorphism
1. **Compile-time Polymorphism (Static Binding)**
   - Method overloading (same method name, different parameters)

2. **Runtime Polymorphism (Dynamic Binding)**
   - Method overriding (same method signature in parent and child classes)

### Syntax

**Method Overloading (Compile-time Polymorphism):**
```java
class Calculator {
    // Method overloading
    int add(int a, int b) {
        return a + b;
    }
    
    double add(double a, double b) {
        return a + b;
    }
    
    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

**Method Overriding (Runtime Polymorphism):**
```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("Cat meows");
    }
}

// Using polymorphic reference
Animal myPet = new Dog();  // Animal reference, Dog object
myPet.makeSound();  // Calls Dog's implementation
```

### Examples

**Example 1: Runtime Polymorphism with Method Overriding**
```java
// Base class
class Shape {
    protected String color;
    
    public Shape(String color) {
        this.color = color;
    }
    
    public double calculateArea() {
        return 0.0;  // Default implementation
    }
    
    public void displayInfo() {
        System.out.println("This is a shape with color: " + color);
    }
}

// Derived class 1
class Circle extends Shape {
    private double radius;
    
    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }
    
    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
    
    @Override
    public void displayInfo() {
        System.out.println("This is a " + color + " circle with radius: " + radius);
    }
}

// Derived class 2
class Rectangle extends Shape {
    private double length;
    private double width;
    
    public Rectangle(String color, double length, double width) {
        super(color);
        this.length = length;
        this.width = width;
    }
    
    @Override
    public double calculateArea() {
        return length * width;
    }
    
    @Override
    public void displayInfo() {
        System.out.println("This is a " + color + " rectangle with length: " + length + " and width: " + width);
    }
}

// Testing polymorphism
public class Main {
    public static void main(String[] args) {
        // Polymorphic array of shapes
        Shape[] shapes = new Shape[3];
        shapes[0] = new Circle("Red", 5.0);
        shapes[1] = new Rectangle("Blue", 4.0, 6.0);
        shapes[2] = new Circle("Green", 3.0);
        
        // Polymorphic behavior
        for (Shape shape : shapes) {
            shape.displayInfo();  // Calls the appropriate overridden method
            System.out.println("Area: " + shape.calculateArea());
            System.out.println();
        }
        
        // Polymorphic method
        displayShapeInfo(new Circle("Yellow", 2.0));
        displayShapeInfo(new Rectangle("Purple", 3.0, 5.0));
    }
    
    // Method that works with any Shape
    public static void displayShapeInfo(Shape shape) {
        System.out.println("Shape Information:");
        shape.displayInfo();
        System.out.println("Area: " + shape.calculateArea());
        System.out.println();
    }
}
```

**Example 2: Compile-time Polymorphism with Method Overloading**
```java
public class Calculator {
    // Method overloading - same name, different parameters
    
    // Addition with two integers
    public int add(int a, int b) {
        System.out.println("Adding two integers");
        return a + b;
    }
    
    // Addition with three integers
    public int add(int a, int b, int c) {
        System.out.println("Adding three integers");
        return a + b + c;
    }
    
    // Addition with two doubles
    public double add(double a, double b) {
        System.out.println("Adding two doubles");
        return a + b;
    }
    
    // Addition with an array of integers
    public int add(int[] numbers) {
        System.out.println("Adding an array of integers");
        int sum = 0;
        for (int num : numbers) {
            sum += num;
        }
        return sum;
    }
    
    // Subtraction method
    public int subtract(int a, int b) {
        return a - b;
    }
    
    // Overloaded subtraction method
    public double subtract(double a, double b) {
        return a - b;
    }
}

// Testing method overloading
public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        
        // Testing different versions of add method
        System.out.println(calc.add(5, 3));
        System.out.println(calc.add(5, 3, 2));
        System.out.println(calc.add(5.5, 3.5));
        System.out.println(calc.add(new int[]{1, 2, 3, 4, 5}));
        
        // Testing overloaded subtract methods
        System.out.println(calc.subtract(10, 5));
        System.out.println(calc.subtract(10.5, 5.5));
    }
}
```

### Practice Questions

1. Create a class hierarchy for `Vehicle` with subclasses like `Car`, `Motorcycle`, and `Truck`. Override a `displayInfo()` method in each subclass, then create an array of `Vehicle` references and demonstrate polymorphic behavior.

2. Implement a `PaymentMethod` class hierarchy with subclasses like `CreditCard`, `DebitCard`, and `CashPayment`. Override a `processPayment()` method in each. Write a `Store` class that accepts any payment method.

3. Design a `MediaPlayer` interface with methods like `play()`, `pause()`, and `stop()`. Implement this interface in classes like `AudioPlayer` and `VideoPlayer` with different implementations of these methods.

4. Create a `Shape` class with overloaded constructors for different shapes (one for circles, one for rectangles, etc.) and demonstrate how to create different shapes using the appropriate constructor.

5. Implement an `Employee` class with an overloaded `calculateSalary()` method that can calculate salary based on different parameters (hourly rate and hours worked, fixed salary, salary plus commission, etc.).

## 4. Inner Classes

### What are Inner Classes?
Inner classes are classes defined within other classes. They allow for logical grouping of classes that are used only in one place, increasing encapsulation and creating more readable, maintainable code.

### Why use Inner Classes?
- To logically group classes that belong together
- To increase encapsulation and hide implementation details
- To access private members of the outer class
- To implement helper classes used only by the outer class
- To create more readable and maintainable code

### Where to use Inner Classes?
- When a class is only used by its outer class
- When you need to access private members of the outer class
- When implementing helper classes for specific functionality
- When creating event listeners or callback interfaces
- When implementing complex data structures (e.g., nodes in a linked list)

### Types of Inner Classes
1. **Member Inner Class** - Defined directly inside a class
2. **Static Nested Class** - Similar to member class but with static keyword
3. **Local Inner Class** - Defined inside a method or block
4. **Anonymous Inner Class** - One-time use class with no name

### Syntax

**Member Inner Class:**
```java
class OuterClass {
    private int outerVar;
    
    // Member inner class
    class InnerClass {
        void method() {
            // Can access outer class private members
            System.out.println(outerVar);
        }
    }
    
    // Method to create inner class instance
    void createInner() {
        InnerClass inner = new InnerClass();
    }
}

// Creating instance from outside
OuterClass outer = new OuterClass();
OuterClass.InnerClass inner = outer.new InnerClass();
```

**Static Nested Class:**
```java
class OuterClass {
    private static int staticVar;
    
    // Static nested class
    static class NestedClass {
        void method() {
            // Can only access static members of outer class
            System.out.println(staticVar);
        }
    }
}

// Creating instance from outside
OuterClass.NestedClass nested = new OuterClass.NestedClass();
```

**Local Inner Class:**
```java
class OuterClass {
    void method() {
        final int localVar = 10;
        
        // Local inner class
        class LocalInner {
            void display() {
                // Can access final local variables
                System.out.println(localVar);
            }
        }
        
        // Using the local class
        LocalInner inner = new LocalInner();
        inner.display();
    }
}
```

**Anonymous Inner Class:**
```java
interface Greeting {
    void greet();
}

class Demo {
    void displayGreeting() {
        // Anonymous inner class implementing Greeting
        Greeting greeting = new Greeting() {
            @Override
            public void greet() {
                System.out.println("Hello, World!");
            }
        };
        
        greeting.greet();
    }
}
```

### Examples

**Example 1: Different Types of Inner Classes**
```java
public class OuterClass {
    private int outerField = 10;
    private static int staticOuterField = 20;
    
    // Member inner class
    public class MemberInner {
        public void display() {
            System.out.println("Member Inner Class");
            System.out.println("Outer field value: " + outerField);
        }
    }
    
    // Static nested class
    public static class StaticNested {
        public void display() {
            System.out.println("Static Nested Class");
            // Can't access non-static outerField
            System.out.println("Static outer field value: " + staticOuterField);
        }
    }
    
    // Method with local inner class
    public void displayLocal() {
        final int localVar = 30;
        
        // Local inner class
        class LocalInner {
            public void display() {
                System.out.println("Local Inner Class");
                System.out.println("Outer field value: " + outerField);
                System.out.println("Local variable value: " + localVar);
            }
        }
        
        // Using local inner class
        LocalInner local = new LocalInner();
        local.display();
    }
    
    // Method using anonymous inner class
    public void displayAnonymous() {
        // Anonymous inner class implementing Runnable interface
        Runnable runner = new Runnable() {
            @Override
            public void run() {
                System.out.println("Anonymous Inner Class");
                System.out.println("Outer field value: " + outerField);
            }
        };
        
        // Using anonymous inner class
        runner.run();
    }
}

// Testing inner classes
public class Main {
    public static void main(String[] args) {
        OuterClass outer = new OuterClass();
        
        // Using member inner class
        OuterClass.MemberInner member = outer.new MemberInner();
        member.display();
        
        // Using static nested class
        OuterClass.StaticNested staticNested = new OuterClass.StaticNested();
        staticNested.display();
        
        // Using local inner class (indirectly)
        outer.displayLocal();
        
        // Using anonymous inner class (indirectly)
        outer.displayAnonymous();
    }
}
```

**Example 2: Practical Use of Inner Classes in a LinkedList Implementation**
```java
public class LinkedList<T> {
    // Node class as private inner class
    private class Node {
        T data;
        Node next;
        
        public Node(T data) {
            this.data = data;
            this.next = null;
        }
    }
    
    // LinkedList fields
    private Node head;
    private int size;
    
    // Constructor
    public LinkedList() {
        head = null;
        size = 0;
    }
    
    // Add element to the end of the list
    public void add(T element) {
        Node newNode = new Node(element);
        
        if (head == null) {
            head = newNode;
        } else {
            Node current = head;
            while (current.next != null) {
                current = current.next;
            }
            current.next = newNode;
        }
        
        size++;
    }
    
    // Get element at specified index
    public T get(int index) {
        if (index < 0 || index >= size) {
            throw new IndexOutOfBoundsException("Index: " + index + ", Size: " + size);
        }
        
        Node current = head;
        for (int i = 0; i < index; i++) {
            current = current.next;
        }
        
        return current.data;
    }
    
    // Remove element at specified index
    public T remove(int index) {
        if (index < 0 || index >= size) {
            throw new IndexOutOfBoundsException("Index: " + index + ", Size: " + size);
        }
        
        T removedData;
        
        if (index == 0) {
            removedData = head.data;
            head = head.next;
        } else {
            Node current = head;
            for (int i = 0; i < index - 1; i++) {
                current = current.next;
            }
            
            removedData = current.next.data;
            current.next = current.next.next;
        }
        
        size--;
        return removedData;
    }
    
    // Get size of list
    public int size() {
        return size;
    }
    
    // Print all elements
    public void printList() {
        Node current = head;
        while (current != null) {
            System.out.print(current.data + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }
    
    // Iterator as inner class
    public class ListIterator {
        private Node current;
        
        public ListIterator() {
            current = head;
        }
        
        public boolean hasNext() {
            return current != null;
        }
        
        public T next() {
            if (!hasNext()) {
                throw new java.util.NoSuchElementException();
            }
            
            T data = current.data;
            current = current.next;
            return data;
        }
    }
    
    // Create and return an iterator
    public ListIterator iterator() {
        return new ListIterator();
    }
}

// Testing LinkedList with inner classes
public class Main {
    public static void main(String[] args) {
        LinkedList<String> list = new LinkedList<>();
        
        list.add("Apple");
        list.add("Banana");
        list.add("Cherry");
        list.add("Date");
        
        System.out.println("LinkedList elements:");
        list.printList();
        
        System.out.println("\nElement at index 2: " + list.get(2));
        
        System.out.println("\nRemoved element: " + list.remove(1));
        System.out.println("LinkedList after removal:");
        list.printList();
        
        System.out.println("\nUsing iterator:");
        LinkedList<String>.ListIterator iterator = list.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
    }
}
```

### Practice Questions

1. Create a class `Library` with an inner class `Book`. Implement methods to add books, remove books, and display all books in the library using the inner class.

2. Design a `Bank` class with a static nested class `Account`. Create different types of accounts (savings, checking) using this structure.

3. Implement a `ShoppingCart` class with a private inner class `Item`. Add methods to add items, remove items, and calculate the total price of the cart.

4. Create a class that demonstrates the use of anonymous inner classes to implement different event handlers for a button click.

5. Design a `Tree` class with an inner class `Node` for the tree structure. Implement methods to add nodes, find nodes, and perform a simple traversal of the tree.

# Abstraction in Java

## What is Abstraction?
Abstraction is one of the core concepts of Object-Oriented Programming (OOP) in Java. It is the process of hiding implementation details and showing only the necessary features of an object.

## Why use Abstraction?
- Reduces code complexity by hiding implementation details.
- Increases code reusability and maintainability.
- Enhances security by restricting access to certain parts of the code.
- Encourages modular design, making it easier to modify and extend.

## Where is Abstraction used?
- **Software development frameworks**: Many frameworks use abstract classes and interfaces to provide reusable structures.
- **Database connectivity**: JDBC (Java Database Connectivity) uses abstraction to allow different database implementations.
- **Device drivers**: Abstract classes define behaviors while specific implementations are provided by different hardware vendors.

## Syntax
In Java, abstraction is achieved using **abstract classes** and **interfaces**.

### Abstract Class Example
```java
abstract class Vehicle {
    abstract void start(); // Abstract method (no implementation)
    
    void stop() { // Concrete method (has implementation)
        System.out.println("Vehicle is stopping...");
    }
}

class Car extends Vehicle {
    void start() {
        System.out.println("Car is starting...");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle myCar = new Car();
        myCar.start();
        myCar.stop();
    }
}
```

### Interface Example
```java
interface Animal {
    void makeSound(); // Abstract method
}

class Dog implements Animal {
    public void makeSound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myDog = new Dog();
        myDog.makeSound();
    }
}
```

## Practice Questions
1. What is abstraction in Java, and how is it different from encapsulation?
2. Explain the difference between abstract classes and interfaces.
3. Write a Java program that demonstrates abstraction using an abstract class named `Shape`.
4. How does Java achieve abstraction? Provide an example.
5. Can an abstract class have a constructor? Justify your answer with an example.

