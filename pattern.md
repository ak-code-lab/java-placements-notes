# Java Pattern Printing Guide

Pattern printing is a common programming exercise that helps strengthen your understanding of loops, control statements, and logical thinking in Java. This guide covers 15 different pattern printing examples with complete code.

## What is Pattern Printing?
Pattern printing refers to the technique of displaying characters (like asterisks, numbers, or letters) in a specific arrangement using loops and control structures. These patterns can be triangles, squares, diamonds, and other shapes.

## Why Use Pattern Printing?
- Strengthens your understanding of nested loops
- Improves logical thinking and problem-solving skills
- Helps in mastering control flow statements
- Commonly asked in interviews and programming assessments
- Builds foundation for more complex algorithm implementation

## Where to Use Pattern Printing?
- Coding interviews and placement tests
- Academic programming assignments
- Building text-based user interfaces
- Creating ASCII art
- Understanding the fundamentals of 2D matrix manipulation

## Basic Syntax for Pattern Printing

The general approach involves:
1. Outer loop to control rows
2. Inner loop(s) to control columns and characters in each row
3. Print statements to display the pattern

```java
public class PatternExample {
    public static void main(String[] args) {
        int n = 5; // Number of rows
        
        // Outer loop for rows
        for (int i = 0; i < n; i++) {
            // Inner loop for columns
            for (int j = 0; j < someCondition; j++) {
                System.out.print("*"); // Print character
            }
            System.out.println(); // Move to next line after each row
        }
    }
}
```

Now, let's dive into the 15 different patterns with complete code examples.

## Pattern 1: Simple Right Triangle

```java
public class Pattern1 {
    public static void main(String[] args) {
        int n = 5;
        
        for (int i = 0; i < n; i++) {
            for (int j = 0; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

Output:
```
* 
* * 
* * * 
* * * * 
* * * * * 
```

## Pattern 2: Inverted Right Triangle

```java
public class Pattern2 {
    public static void main(String[] args) {
        int n = 5;
        
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

Output:
```
* * * * * 
* * * * 
* * * 
* * 
* 
```

## Pattern 3: Pyramid Pattern

```java
public class Pattern3 {
    public static void main(String[] args) {
        int n = 5;
        
        for (int i = 0; i < n; i++) {
            // Print spaces
            for (int j = n - i - 1; j > 0; j--) {
                System.out.print(" ");
            }
            
            // Print stars
            for (int j = 0; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

Output:
```
    * 
   * * 
  * * * 
 * * * * 
* * * * * 
```

## Pattern 4: Number Pattern - Increasing Row Numbers

```java
public class Pattern4 {
    public static void main(String[] args) {
        int n = 5;
        
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print(i + " ");
            }
            System.out.println();
        }
    }
}
```

Output:
```
1 
2 2 
3 3 3 
4 4 4 4 
5 5 5 5 5 
```

## Pattern 5: Number Pattern - Increasing Column Numbers

```java
public class Pattern5 {
    public static void main(String[] args) {
        int n = 5;
        
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print(j + " ");
            }
            System.out.println();
        }
    }
}
```

Output:
```
1 
1 2 
1 2 3 
1 2 3 4 
1 2 3 4 5 
```

## Pattern 6: Hollow Rectangle

```java
public class Pattern6 {
    public static void main(String[] args) {
        int rows = 5;
        int cols = 10;
        
        for (int i = 1; i <= rows; i++) {
            for (int j = 1; j <= cols; j++) {
                // Print star only at borders
                if (i == 1 || i == rows || j == 1 || j == cols) {
                    System.out.print("*");
                } else {
                    System.out.print(" ");
                }
            }
            System.out.println();
        }
    }
}
```

Output:
```
**********
*        *
*        *
*        *
**********
```

## Pattern 7: Diamond Pattern

```java
public class Pattern7 {
    public static void main(String[] args) {
        int n = 5;
        
        // Upper half of the diamond
        for (int i = 1; i <= n; i++) {
            // Print spaces
            for (int j = 1; j <= n - i; j++) {
                System.out.print(" ");
            }
            
            // Print stars
            for (int j = 1; j <= 2 * i - 1; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
        
        // Lower half of the diamond
        for (int i = n - 1; i >= 1; i--) {
            // Print spaces
            for (int j = 1; j <= n - i; j++) {
                System.out.print(" ");
            }
            
            // Print stars
            for (int j = 1; j <= 2 * i - 1; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```

Output:
```
    *
   ***
  *****
 *******
*********
 *******
  *****
   ***
    *
```

## Pattern 8: Hollow Triangle

```java
public class Pattern8 {
    public static void main(String[] args) {
        int n = 5;
        
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= i; j++) {
                // Print star only at the border
                if (j == 1 || j == i || i == n) {
                    System.out.print("* ");
                } else {
                    System.out.print("  ");
                }
            }
            System.out.println();
        }
    }
}
```

Output:
```
* 
* * 
*   * 
*     * 
* * * * * 
```

## Pattern 9: Floyd's Triangle

```java
public class Pattern9 {
    public static void main(String[] args) {
        int n = 5;
        int number = 1;
        
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print(number + " ");
                number++;
            }
            System.out.println();
        }
    }
}
```

Output:
```
1 
2 3 
4 5 6 
7 8 9 10 
11 12 13 14 15 
```

## Pattern 10: Butterfly Pattern

```java
public class Pattern10 {
    public static void main(String[] args) {
        int n = 4;
        
        // Upper half
        for (int i = 1; i <= n; i++) {
            // Left stars
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            
            // Spaces
            int spaces = 2 * (n - i);
            for (int j = 1; j <= spaces; j++) {
                System.out.print(" ");
            }
            
            // Right stars
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
        
        // Lower half
        for (int i = n; i >= 1; i--) {
            // Left stars
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            
            // Spaces
            int spaces = 2 * (n - i);
            for (int j = 1; j <= spaces; j++) {
                System.out.print(" ");
            }
            
            // Right stars
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```

Output:
```
*      *
**    **
***  ***
********
********
***  ***
**    **
*      *
```

## Pattern 11: Character Triangle

```java
public class Pattern11 {
    public static void main(String[] args) {
        int n = 5;
        
        for (int i = 0; i < n; i++) {
            char ch = 'A';
            for (int j = 0; j <= i; j++) {
                System.out.print(ch + " ");
                ch++;
            }
            System.out.println();
        }
    }
}
```

Output:
```
A 
A B 
A B C 
A B C D 
A B C D E 
```

## Pattern 12: Palindrome Triangle

```java
public class Pattern12 {
    public static void main(String[] args) {
        int n = 5;
        
        for (int i = 1; i <= n; i++) {
            // Print spaces
            for (int j = 1; j <= n - i; j++) {
                System.out.print("  ");
            }
            
            // Print first half numbers
            for (int j = i; j >= 1; j--) {
                System.out.print(j + " ");
            }
            
            // Print second half numbers
            for (int j = 2; j <= i; j++) {
                System.out.print(j + " ");
            }
            
            System.out.println();
        }
    }
}
```

Output:
```
        1 
      2 1 2 
    3 2 1 2 3 
  4 3 2 1 2 3 4 
5 4 3 2 1 2 3 4 5 
```

## Pattern 13: Spiral Pattern

```java
public class Pattern13 {
    public static void main(String[] args) {
        int n = 4; // Size of the matrix
        int[][] matrix = new int[n][n];
        
        int value = 1;
        int minRow = 0, maxRow = n - 1;
        int minCol = 0, maxCol = n - 1;
        
        while (value <= n * n) {
            // Fill top row
            for (int i = minCol; i <= maxCol; i++) {
                matrix[minRow][i] = value++;
            }
            minRow++;
            
            // Fill right column
            for (int i = minRow; i <= maxRow; i++) {
                matrix[i][maxCol] = value++;
            }
            maxCol--;
            
            // Fill bottom row
            for (int i = maxCol; i >= minCol; i--) {
                matrix[maxRow][i] = value++;
            }
            maxRow--;
            
            // Fill left column
            for (int i = maxRow; i >= minRow; i--) {
                matrix[i][minCol] = value++;
            }
            minCol++;
        }
        
        // Print the matrix
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                System.out.print(matrix[i][j] + "\t");
            }
            System.out.println();
        }
    }
}
```

Output:
```
1	2	3	4	
12	13	14	5	
11	16	15	6	
10	9	8	7	
```

## Pattern 14: Zig-Zag Pattern

```java
public class Pattern14 {
    public static void main(String[] args) {
        int n = 9; // Number of columns
        
        for (int i = 1; i <= 3; i++) {
            for (int j = 1; j <= n; j++) {
                // Condition for printing stars
                if ((i + j) % 4 == 0 || (i == 2 && j % 4 == 0)) {
                    System.out.print("* ");
                } else {
                    System.out.print("  ");
                }
            }
            System.out.println();
        }
    }
}
```

Output:
```
*       *       * 
  *   *   *   *   
    *       *     
```

## Pattern 15: Hourglass Pattern

```java
public class Pattern15 {
    public static void main(String[] args) {
        int n = 5;
        
        // Upper part
        for (int i = 1; i <= n; i++) {
            // Print spaces
            for (int j = 1; j < i; j++) {
                System.out.print(" ");
            }
            
            // Print stars
            for (int j = i; j <= 2 * n - i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
        
        // Lower part
        for (int i = n - 1; i >= 1; i--) {
            // Print spaces
            for (int j = 1; j < i; j++) {
                System.out.print(" ");
            }
            
            // Print stars
            for (int j = i; j <= 2 * n - i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```

Output:
```
*********
 *******
  *****
   ***
    *
   ***
  *****
 *******
*********
```

## Practice Questions

1. **Question:** Write a Java program to create a pattern of a rhombus made of stars.

2. **Question:** Create a pattern that displays a right arrow made of asterisks.

3. **Question:** Write a Java program to print Pascal's Triangle up to n rows.

4. **Question:** Create a pattern of a hollow diamond with stars.

5. **Question:** Write a Java program to print a number pattern where each row contains numbers equal to the row number, but in descending order. For example:
```
1
21
321
4321
54321
```

Good luck with your Java placement preparations! These pattern printing exercises will help strengthen your understanding of loops and control structures, which are fundamental concepts in programming.