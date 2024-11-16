# java11

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


