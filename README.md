# java11

## WORKING WITH JAVA DATA TYPES

## Primitive Types in Java
```java
public class PrimitiveTypesExample {

    // Primitive data types
    private byte byteValue = 127; // 8-bit integer
    private short shortValue = 32000; // 16-bit integer
    private int intValue = 2147483647; // 32-bit integer
    private long longValue = 9223372036854775807L; // 64-bit integer

    private float floatValue = 3.14f; // 32-bit floating-point
    private double doubleValue = 3.141592653589793; // 64-bit floating-point

    private char charValue = 'A'; // 16-bit Unicode character
    private boolean booleanValue = true; // true or false

    public void printValues() {
        System.out.println("byteValue: " + byteValue);
        System.out.println("shortValue: " + shortValue);
        System.out.println("intValue: " + intValue);
        System.out.println("longValue: " + longValue);
        System.out.println("floatValue: " + floatValue);
        System.out.println("doubleValue: " + doubleValue);
        System.out.println("charValue: " + charValue);
        System.out.println("booleanValue: " + booleanValue);
    }

    public static void main(String[] args) {
        PrimitiveTypesExample example = new PrimitiveTypesExample();
        example.printValues();
    }
}
```

### Underscores

In Java, underscores (_) can be used as separators in numeric literals to improve readability, especially for large numbers.
```java
int million = 1_000_000; // Same as 1000000
System.out.println(million); // Output: 1000000
```

### var type
In Java, the var keyword is used for local variable type inference, introduced in Java 10. It allows the compiler to infer the type of a local variable based on the value assigned to it. This makes the code more concise and readable while retaining type safety.

```java
    var number = 10; // int
    var name = "Java"; // String
```

### varargs
To define a varargs parameter, use an ellipsis (...) after the type in the method parameter list. A method can only have one varargs parameter, and it must be the last parameter in the method signature.

```java
returnType methodName(type... parameterName)
```

```java
public class VarargsExample {
    public static void printNumbers(String label, int... numbers) {
        System.out.println(label + ":");
        for (int number : numbers) {
            System.out.println(number);
        }
    }

    public static void main(String[] args) {
        printNumbers("Set 1", 1, 2, 3); // Passing multiple arguments
        printNumbers("Set 2", 10, 20);  // Passing fewer arguments
        printNumbers("Empty Set");      // No arguments passed
    }
}
```

### LocalDateTime (aka DateTime in  c#)
Represents a date and time without a timezone (e.g., 2024-11-15T14:30:00).
```java
import java.time.LocalDateTime;

public class LocalDateTimeExample {
    public static void main(String[] args) {
        LocalDateTime now = LocalDateTime.now(); // Current date and time
        LocalDateTime specificDateTime = LocalDateTime.of(2023, 12, 25, 14, 30); // Dec 25, 2023, 2:30 PM
        LocalDateTime parsedDateTime = LocalDateTime.parse("2024-11-15T14:30:00"); // Parsing a string

        System.out.println("Now: " + now);
        System.out.println("Specific DateTime: " + specificDateTime);
        System.out.println("Parsed DateTime: " + parsedDateTime);
    }
}
```

### LocalDate - Represents a date without time (e.g., 2024-11-15).
```java
import java.time.LocalDate;

public class LocalDateExample {
    public static void main(String[] args) {
        LocalDate today = LocalDate.now(); // Current date
        LocalDate specificDate = LocalDate.of(2023, 12, 25); // Christmas 2023
        LocalDate parsedDate = LocalDate.parse("2024-11-15"); // Parsing a string

        System.out.println("Today: " + today);
        System.out.println("Specific Date: " + specificDate);
        System.out.println("Parsed Date: " + parsedDate);
    }
}
```

### LocalTime - Represents time without a date (e.g., 15:30:45).
```java
import java.time.LocalTime;

public class LocalTimeExample {
    public static void main(String[] args) {
        LocalTime now = LocalTime.now(); // Current time
        LocalTime specificTime = LocalTime.of(14, 30, 15); // 2:30:15 PM
        LocalTime parsedTime = LocalTime.parse("09:45:00"); // Parsing a string

        System.out.println("Current Time: " + now);
        System.out.println("Specific Time: " + specificTime);
        System.out.println("Parsed Time: " + parsedTime);
    }
}
```

### ZonedDateTime
Represents a date and time with a timezone (e.g., 2024-11-15T14:30:00+01:00[Europe/Paris]).

### Instant
Represents a point in time (e.g., 2024-11-15T13:45:30Z). Useful for timestamps.
```java
import java.time.Instant;

public class InstantExample {
    public static void main(String[] args) {
        Instant now = Instant.now(); // Current timestamp
        Instant epoch = Instant.ofEpochSecond(0); // Unix epoch (1970-01-01T00:00:00Z)

        System.out.println("Now: " + now);
        System.out.println("Epoch: " + epoch);
    }
}
```

### Duration
Represents a time-based amount (e.g., hours, minutes, seconds).
```java
import java.time.Duration;
import java.time.LocalTime;

public class DurationExample {
    public static void main(String[] args) {
        LocalTime startTime = LocalTime.of(8, 30);
        LocalTime endTime = LocalTime.of(14, 45);

        Duration duration = Duration.between(startTime, endTime);

        System.out.println("Hours: " + duration.toHours());
        System.out.println("Minutes: " + duration.toMinutes());
    }
}
```

## PROGRAM FLOW

### For...Each
Syntax:
```java
for (Type item : collection) {
    // Code block to execute for each item
}
```

List:
```java
import java.util.List;

public class ForEachListExample {
    public static void main(String[] args) {
        List<String> fruits = List.of("Apple", "Banana", "Cherry");

        System.out.println("Fruits:");
        for (String fruit : fruits) {
            System.out.println(fruit);
        }
    }
}
```

Map:
```java
import java.util.Map;

public class ForEachMapExample {
    public static void main(String[] args) {
        Map<String, Integer> items = Map.of(
            "Apples", 5,
            "Oranges", 10,
            "Bananas", 7
        );

        System.out.println("Items and Quantities:");
        for (Map.Entry<String, Integer> entry : items.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
    }
}
```

## OOPS

### Package
In Java, the package keyword is used to define a namespace for organizing related classes and interfaces. It helps group similar types of classes together to avoid name conflicts, improve code readability, and manage the project structure more effectively.

```java
package com.example.utilities;

public class MathUtils {
    public static int add(int a, int b) {
        return a + b;
    }
}
```

The above class is part of the com.example.utilities package.<br>
The folder structure for the package would be:
```bash
com/example/utilities/MathUtils.java
```

- Importing a specific class: import com.example.utilities.MathUtils;
- Importing All Classes from a Package: import com.example.utilities.*;

Important Notes:
- The directory structure of the project must match the package structure.
- If no package statement is specified, the class is part of the default package, which is discouraged for large projects.
- The package declaration must be the first statement (excluding comments) in a Java file:

### Constructors/Destructors
In Java, you can define constructors to initialize objects when they are created. However, destructors do not exist in Java like they do in languages such as C++. Instead, Java uses the finalize() method (deprecated as of Java 9 and removed in Java 18) and garbage collection to clean up resources.

#### Modern Alternative to finalize(): Using AutoCloseable
If the class deals with resources, you can implement the AutoCloseable interface for automatic cleanup.

```java
public class Example implements AutoCloseable {
    private String name;

    // Constructor
    public Example(String name) {
        this.name = name;
        System.out.println("Constructor called: Object created for " + name);
    }

    // Overriding close() for cleanup
    @Override
    public void close() {
        System.out.println("Close called: Resources released for " + name);
    }

    public static void main(String[] args) {
        try (Example obj = new Example("Sample1")) {
            System.out.println("Using the object...");
        } // close() is automatically called here
    }
}
```

output:
```sql
Constructor called: Object created for Sample1
Using the object...
Close called: Resources released for Sample1
```

The try-with-resources construct introduced in Java 7 is a safer and more deterministic way to manage resources.<br>
Implementing the AutoCloseable or Closeable interfaces allows resources to be explicitly cleaned up, ensuring better control.

Example:
```java
try (FileInputStream fis = new FileInputStream("example.txt")) {
    // Use the resource
} // The file input stream is automatically closed here
```
 
### this()
In Java, this() is used to call another constructor of the same class from within a constructor. This is known as constructor chaining and is useful when multiple constructors need to initialize the object with different levels of detail while reusing the initialization logic.

Key Rules for Using this():
- Must Be the First Statement: The call to this() must appear as the first statement in the constructor; otherwise, a compilation error occurs.
- Cannot Create Loops: Constructor chaining cannot form a circular chain, i.e., one constructor calling itself directly or indirectly.

```java
public class Employee {
    private String name;
    private int age;
    private String department;

    // Constructor 1: Default values
    public Employee() {
        this("Unknown", 0, "General"); // Calls Constructor 3
        System.out.println("Default constructor called");
    }

    // Constructor 2: Two parameters
    public Employee(String name, int age) {
        this(name, age, "General"); // Calls Constructor 3
        System.out.println("Two-parameter constructor called");
    }

    // Constructor 3: All parameters
    public Employee(String name, int age, String department) {
        this.name = name;
        this.age = age;
        this.department = department;
        System.out.println("Three-parameter constructor called");
    }

    public void display() {
        System.out.println("Name: " + name + ", Age: " + age + ", Department: " + department);
    }

    public static void main(String[] args) {
        Employee emp1 = new Employee();
        emp1.display();

        Employee emp2 = new Employee("Alice", 30);
        emp2.display();

        Employee emp3 = new Employee("Bob", 35, "IT");
        emp3.display();
    }
}
```

Output:
```sql
Three-parameter constructor called
Default constructor called
Name: Unknown, Age: 0, Department: General
Three-parameter constructor called
Two-parameter constructor called
Name: Alice, Age: 30, Department: General
Three-parameter constructor called
Name: Bob, Age: 35, Department: IT
```
