# Java Arrays - Complete Guide

## What is an Array in Java?

An array in Java is a container object that holds a fixed number of values of a single type. Arrays are used to store multiple values in a single variable, instead of declaring separate variables for each value. Arrays in Java are objects, which means they're created on the heap and can be passed as parameters to methods.

## Why Use Arrays?

- **Efficient Storage**: Arrays provide an efficient way to store and access a collection of similar data types.
- **Performance**: Accessing array elements is very fast as it uses index-based retrieval (constant time operation, O(1)).
- **Memory Management**: Arrays allocate memory in contiguous blocks, making memory management more efficient.
- **Easy Sorting and Searching**: Arrays work well with built-in sorting and searching algorithms.
- **Foundation for Data Structures**: Many advanced data structures like ArrayList, LinkedList, Stack, etc., are implemented using arrays.

## Where to Use Arrays?

- **Collections of Similar Data**: When you need to store multiple values of the same type (e.g., list of student scores, employee IDs).
- **Tabular Data**: For representing matrices or tables using two-dimensional arrays.
- **Algorithm Implementation**: For implementing sorting, searching, and other algorithms.
- **Buffering**: For efficiently handling and processing data in chunks (e.g., reading from files).
- **Fixed-Size Collections**: When you know the exact number of elements in advance.

## Syntax and Declaration

### 1. Declaration

```java
// Method 1: Declaration with size
dataType[] arrayName = new dataType[arraySize];

// Method 2: Declaration and initialization 
dataType[] arrayName = {value1, value2, value3, ...};
```

### 2. Accessing Elements

```java
// Accessing elements using index (zero-based indexing)
arrayName[index];
```

### 3. Modifying Elements

```java
// Modifying an element
arrayName[index] = newValue;
```

### 4. Array Length

```java
// Getting the length of an array
int length = arrayName.length;
```

## Examples

### Example 1: Basic Array Operations

```java
public class ArrayExample1 {
    public static void main(String[] args) {
        // Declare and initialize an array
        int[] numbers = {10, 20, a\30, 40, 50};
        
        // Access and print elements
        System.out.println("First element: " + numbers[0]);
        System.out.println("Third element: " + numbers[2]);
        
        // Modify an element
        numbers[1] = 25;
        System.out.println("Modified second element: " + numbers[1]);
        
        // Array length
        System.out.println("Array length: " + numbers.length);
        
        // Iterate through array
        System.out.println("All elements:");
        for (int i = 0; i < numbers.length; i++) {
            System.out.println("Element at index " + i + ": " + numbers[i]);
        }
        
        // Enhanced for loop (for-each loop)
        System.out.println("Using enhanced for loop:");
        for (int num : numbers) {
            System.out.println(num);
        }
    }
}
```

### Example 2: Two-Dimensional Arrays

```java
public class ArrayExample2 {
    public static void main(String[] args) {
        // Declaration and initialization of 2D array
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        
        // Access elements
        System.out.println("Element at matrix[1][2]: " + matrix[1][2]);
        
        // Modify element
        matrix[0][1] = 10;
        System.out.println("Modified element: " + matrix[0][1]);
        
        // Print all elements of 2D array
        System.out.println("All elements of matrix:");
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println(); // New line after each row
        }
        
        // Using enhanced for loop for 2D array
        System.out.println("Using enhanced for loop:");
        for (int[] row : matrix) {
            for (int element : row) {
                System.out.print(element + " ");
            }
            System.out.println();
        }
    }
}
```

## Common Array Operations

### 1. Copying Arrays

```java
// Method 1: Using System.arraycopy()
int[] source = {1, 2, 3, 4, 5};
int[] destination = new int[source.length];
System.arraycopy(source, 0, destination, 0, source.length);

// Method 2: Using Arrays.copyOf()
import java.util.Arrays;
int[] source = {1, 2, 3, 4, 5};
int[] destination = Arrays.copyOf(source, source.length);

// Method 3: Clone method
int[] source = {1, 2, 3, 4, 5};
int[] destination = source.clone();
```

### 2. Sorting Arrays

```java
import java.util.Arrays;

int[] numbers = {5, 2, 9, 1, 5, 6};
Arrays.sort(numbers);
// numbers is now {1, 2, 5, 5, 6, 9}
```

### 3. Searching in Arrays

```java
import java.util.Arrays;

int[] numbers = {1, 2, 5, 5, 6, 9};
int index = Arrays.binarySearch(numbers, 5);
// index will be the position of 5 in the sorted array
```

### 4. Filling Arrays

```java
import java.util.Arrays;

int[] numbers = new int[5];
Arrays.fill(numbers, 10);
// numbers is now {10, 10, 10, 10, 10}
```

### 5. Comparing Arrays

```java
import java.util.Arrays;

int[] array1 = {1, 2, 3};
int[] array2 = {1, 2, 3};
boolean areEqual = Arrays.equals(array1, array2);
// areEqual is true
```

## Practice Examples

### Question 1
Write a Java program to find the maximum and minimum value in an array.

```java
public class MinMaxArray {
    public static void main(String[] args) {
        int[] numbers = {5, 10, 3, 25, 8, 15};
        int max = numbers[0];
        int min = numbers[0];
        
        for (int i = 1; i < numbers.length; i++) {
            if (numbers[i] > max) {
                max = numbers[i];
            }
            if (numbers[i] < min) {
                min = numbers[i];
            }
        }
        
        System.out.println("Maximum value: " + max);
        System.out.println("Minimum value: " + min);
    }
}
```

### Question 2
Write a Java program to reverse an array without using another array.

```java
import java.util.Arrays;

public class ReverseArray {
    public static void main(String[] args) {
        int[] array = {1, 2, 3, 4, 5};
        
        System.out.println("Original array: " + Arrays.toString(array));
        
        // Reverse the array
        for (int i = 0; i < array.length / 2; i++) {
            // Swap elements
            int temp = array[i];
            array[i] = array[array.length - 1 - i];
            array[array.length - 1 - i] = temp;
        }
        
        System.out.println("Reversed array: " + Arrays.toString(array));
    }
}
```

### Question 3
Write a Java program to find the second largest element in an array.

```java
public class SecondLargest {
    public static void main(String[] args) {
        int[] numbers = {10, 5, 20, 8, 15, 30};
        int largest = Integer.MIN_VALUE;
        int secondLargest = Integer.MIN_VALUE;
        
        for (int num : numbers) {
            if (num > largest) {
                secondLargest = largest;
                largest = num;
            } else if (num > secondLargest && num != largest) {
                secondLargest = num;
            }
        }
        
        System.out.println("The second largest element is: " + secondLargest);
    }
}
```

### Question 4
Write a Java program to find all pairs of elements in an array whose sum is equal to a specified number.

```java
public class PairSum {
    public static void main(String[] args) {
        int[] numbers = {4, 6, 5, 3, 8, 2, 9};
        int targetSum = 10;
        
        System.out.println("Pairs with sum " + targetSum + ":");
        
        for (int i = 0; i < numbers.length; i++) {
            for (int j = i + 1; j < numbers.length; j++) {
                if (numbers[i] + numbers[j] == targetSum) {
                    System.out.println(numbers[i] + " + " + numbers[j] + " = " + targetSum);
                }
            }
        }
    }
}
```

### Question 5
Write a Java program to merge two sorted arrays into a single sorted array.

```java
import java.util.Arrays;

public class MergeSortedArrays {
    public static void main(String[] args) {
        int[] array1 = {1, 3, 5, 7, 9};
        int[] array2 = {2, 4, 6, 8, 10};
        
        int[] mergedArray = new int[array1.length + array2.length];
        
        int i = 0, j = 0, k = 0;
        
        // Merge arrays
        while (i < array1.length && j < array2.length) {
            if (array1[i] < array2[j]) {
                mergedArray[k++] = array1[i++];
            } else {
                mergedArray[k++] = array2[j++];
            }
        }
        
        // Copy remaining elements from array1, if any
        while (i < array1.length) {
            mergedArray[k++] = array1[i++];
        }
        
        // Copy remaining elements from array2, if any
        while (j < array2.length) {
            mergedArray[k++] = array2[j++];
        }
        
        System.out.println("Merged and sorted array: " + Arrays.toString(mergedArray));
    }
}
```

## Common Issues with Arrays in Java

1. **ArrayIndexOutOfBoundsException**: Occurs when you try to access an index that doesn't exist in the array.

2. **Fixed Size**: Once an array is created, its size cannot be changed. To overcome this limitation, you can use ArrayList from Java Collections Framework.

3. **Homogeneous Elements**: Arrays can store only elements of the same type. For mixed types, consider using Object arrays or Collections.

4. **No Built-in Methods**: Unlike Collections, arrays don't have built-in methods for adding/removing elements. You have to handle these operations manually.

5. **Memory Allocation**: Large arrays might cause memory issues if not managed properly, especially in systems with limited resources.

## Advanced Array Concepts

### Jagged Arrays (Arrays of Different Lengths)

```java
int[][] jaggedArray = new int[3][];
jaggedArray[0] = new int[3];
jaggedArray[1] = new int[5];
jaggedArray[2] = new int[2];
```

### Array of Objects

```java
class Student {
    String name;
    int id;
    
    public Student(String name, int id) {
        this.name = name;
        this.id = id;
    }
    
    @Override
    public String toString() {
        return "Student [name=" + name + ", id=" + id + "]";
    }
}

public class ObjectArrayExample {
    public static void main(String[] args) {
        // Create an array of Student objects
        Student[] students = new Student[3];
        
        // Initialize the array
        students[0] = new Student("Alice", 101);
        students[1] = new Student("Bob", 102);
        students[2] = new Student("Charlie", 103);
        
        // Access and print elements
        for (Student student : students) {
            System.out.println(student);
        }
    }
}
```

### Using Arrays with Methods

```java
public class ArrayMethods {
    // Method that takes an array as parameter
    public static double calculateAverage(int[] numbers) {
        int sum = 0;
        for (int num : numbers) {
            sum += num;
        }
        return (double) sum / numbers.length;
    }
    
    // Method that returns an array
    public static int[] generateEvenNumbers(int count) {
        int[] evenNumbers = new int[count];
        for (int i = 0; i < count; i++) {
            evenNumbers[i] = i * 2;
        }
        return evenNumbers;
    }
    
    public static void main(String[] args) {
        int[] scores = {85, 90, 78, 92, 88};
        
        // Using a method that takes an array
        double average = calculateAverage(scores);
        System.out.println("Average score: " + average);
        
        // Using a method that returns an array
        int[] evens = generateEvenNumbers(5);
        System.out.println("Even numbers: " + Arrays.toString(evens));
    }
}
```

With this comprehensive guide, you should have a solid understanding of arrays in Java for your placement preparation. Remember to practice these concepts regularly to gain proficiency.