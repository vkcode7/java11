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

### static
Here’s an example of a Java class demonstrating a static field, a static method, and a static nested class:

```java
public class StaticDemo {

    // Static field
    private static int count = 0;

    // Static method
    public static void incrementCount() {
        count++;
    }

    public static int getCount() {
        return count;
    }

    // Static nested class
    public static class Nested {
        public void displayMessage() {
            System.out.println("Hello from the static nested class!");
        }

        public void displayCount() {
            System.out.println("Current count (from static nested class): " + StaticDemo.getCount());
        }
    }

    public static void main(String[] args) {
        // Access static field and method
        System.out.println("Initial count: " + StaticDemo.getCount());
        StaticDemo.incrementCount();
        StaticDemo.incrementCount();
        System.out.println("Updated count: " + StaticDemo.getCount());

        // Access static nested class
        StaticDemo.Nested nested = new StaticDemo.Nested();
        nested.displayMessage();
        nested.displayCount();
    }
}
```
### Access Levels for class
In Java, access modifiers at the class level determine the visibility and accessibility of a class to other classes or packages. 

There are two valid access modifiers for top-level classes:
- public - accessible from anywhere in the application, provided it is in the classpath
- default (no access modifier is specified) - only within the same package

For nested classes, all four access modifiers (public, private, protected, and default`) can be used.


At the nested class level, private and protected access modifiers control how the nested class interacts with its enclosing class and the rest of the code. Here's how they work:

<img width="728" alt="image" src="https://github.com/user-attachments/assets/6e329554-26d2-4f1f-928d-e7efa4db35df">

### Access Level Table for members:
<img width="729" alt="image" src="https://github.com/user-attachments/assets/9209a8c3-7cd4-407e-88e0-f986e3a00149">

### inheritance - extends
super() is used to call base class ctor

```java
// Base class (Parent)
class Animal {
    private String name;

    // Base class constructor
    public Animal(String name) {
        this.name = name;
        System.out.println("Animal constructor called: " + name);
    }

    // Method in the base class
    public void display() {
        System.out.println("I am an Animal. My name is: " + name);
    }
}

// Derived class (Child)
class Dog extends Animal {
    private String breed;

    // Derived class constructor
    public Dog(String name, String breed) {
        super(name); // Call to base class constructor
        this.breed = breed;
        System.out.println("Dog constructor called. Breed: " + breed);
    }

    // Method in the derived class
    public void bark() {
        System.out.println("Woof! I am a " + breed);
    }
}

// Main class
public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog("Buddy", "Golden Retriever");
        dog.display(); // Method from the base class
        dog.bark();    // Method from the derived class
    }
}
```

### Summary of class specifiers
<img width="736" alt="image" src="https://github.com/user-attachments/assets/f1a8c58b-92da-4ba5-a50c-22a38dcd73c0">

#### sealed vs final:
Key Differences:
- final: Prevents any subclassing at all.
- sealed: Allows subclassing, but only by specific classes you define (using permits), providing more controlled flexibility than final.

```java
public sealed class SealedClass permits SubClassA, SubClassB {
    // Only SubClassA and SubClassB can extend SealedClass
}

class SubClassA extends SealedClass { // Valid
}

class SubClassB extends SealedClass { // Valid
}

class SubClassC extends SealedClass {  // Compile-time error: Cannot extend sealed class 'SealedClass'
    // Error: Cannot extend from a sealed class that doesn't permit this class
}
```

Note: Java, a class cannot extend more than one class. This is due to Java's single inheritance model for classes. A class can only inherit from one superclass. This design decision helps avoid complexities like the Diamond Problem, where a subclass might inherit conflicting behaviors from multiple parent classes. Use interfaces for multiple inheritance.

### Interfaces
In Java, an interface is a reference type, similar to a class, that can contain only abstract methods, default methods, static methods, and constants (fields). Interfaces define a contract for what a class can do, without specifying how it does it.

```java
interface MyInterface {
    // Constant declaration
    int MAX_VALUE = 100;

    // Abstract method (without body)
    void abstractMethod();

    // Default method (with body)
    default void defaultMethod() {
        System.out.println("This is a default method.");
    }

    // Static method (with body)
    static void staticMethod() {
        System.out.println("This is a static method in the interface.");
    }
}
```

#### Multiple inheritance using interfaces:
```java
interface Animal {
    void sound();
}

interface Mammal {
    void feed();
}

class Dog implements Animal, Mammal {
    @Override
    public void sound() {
        System.out.println("Bark");
    }

    @Override
    public void feed() {
        System.out.println("Feeding the dog.");
    }
}
```

#### Interface Inheritance: 
An interface can extend another interface. The implementing class must then implement all methods from both interfaces.

```java
interface Animal {
    void sound();
}

interface Mammal extends Animal {
    void feed();
}
```

#### Functional interface
A functional interface in Java is an interface that has exactly one abstract method. These interfaces can have multiple default methods and static methods, but they can only have one abstract method. Functional interfaces are primarily used as the basis for lambda expressions and method references, enabling a functional programming style in Java.

Key Characteristics of Functional Interfaces:
Exactly One Abstract Method:

A functional interface must contain only one abstract method.
It can contain multiple default methods or static methods, but the key requirement is that there must be only one abstract method.
Used with Lambda Expressions:

Functional interfaces are often used with lambda expressions to provide the implementation of the abstract method in a concise way.
@FunctionalInterface Annotation (Optional but recommended):

Java 8 introduced the @FunctionalInterface annotation, which is not required but provides compile-time checking to ensure that the interface is indeed a functional interface. It will throw an error if the interface has more than one abstract method.

<strong>Syntax of a Functional Interface:</strong>
```java
@FunctionalInterface
interface MyFunctionalInterface {
    // Abstract method (must be implemented by the class or lambda expression)
    void myMethod();

    // Default method (can be provided with implementation)
    default void defaultMethod() {
        System.out.println("This is a default method.");
    }

    // Static method (can be provided with implementation)
    static void staticMethod() {
        System.out.println("This is a static method.");
    }
}
```

<strong>Example of a Functional Interface with Lambda Expression:</strong>
```java
@FunctionalInterface
interface Greeting {
    void sayHello(String name); // Abstract method
}

public class Main {
    public static void main(String[] args) {
        // Lambda expression providing implementation for the sayHello method
        Greeting greeting = (name) -> System.out.println("Hello, " + name);

        // Call the method
        greeting.sayHello("Alice");
    }
}

Output:
Hello, Alice
```

<strong>Functional Interface and Lambda Expressions:</strong>
Functional interfaces are closely tied to lambda expressions. The lambda expression provides a concise way to implement the abstract method of a functional interface.

<strong>Example using a functional interface with a lambda expression:</strong>

```java
@FunctionalInterface
interface MathOperation {
    int operate(int a, int b); // Abstract method for operation
}

public class Calculator {
    public static void main(String[] args) {
        // Lambda expression for addition operation
        MathOperation add = (a, b) -> a + b;
        System.out.println("Addition: " + add.operate(5, 3)); // Output: 8

        // Lambda expression for subtraction operation
        MathOperation subtract = (a, b) -> a - b;
        System.out.println("Subtraction: " + subtract.operate(5, 3)); // Output: 2
    }
}
Output:
Addition: 8
Subtraction: 2
```

#### Common Built-in Functional Interfaces in Java:
Java 8 introduced several functional interfaces in the java.util.function package, which are commonly used with lambda expressions:

#### Predicate<T>:
- Represents a function that takes an argument and returns a boolean.
- Used for filtering or matching.
```java
Predicate<Integer> isEven = (n) -> n % 2 == 0;
System.out.println(isEven.test(4)); // Output: true
```

#### Function<T, R>:
Represents a function that takes an argument of type T and returns a result of type R.
```java
Function<Integer, Integer> square = (n) -> n * n;
System.out.println(square.apply(5)); // Output: 25
```

#### Consumer<T>:
Represents a function that takes an argument of type T and returns void. It is used for performing actions.
```java
Consumer<String> print = (str) -> System.out.println(str);
print.accept("Hello, World!"); // Output: Hello, World!
```

#### Supplier<T>:
Represents a function that takes no arguments and returns a result of type T.
```java
Copy code
Supplier<Double> randomValue = () -> Math.random();
System.out.println(randomValue.get()); // Output: Random double value
```

#### BiFunction<T, U, R>:
Represents a function that takes two arguments of types T and U, and returns a result of type R.
```java
BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;
System.out.println(add.apply(2, 3)); // Output: 5
```

### Enums 
#### Key Characteristics of Enums in Java:
- Enum Constants: The values defined in the enum type.
- Type Safety: Enums provide compile-time checking, ensuring that only valid constants are used.
- Can Have Fields and Methods: Enums can have fields, methods, and constructors.
- Extends java.lang.Enum: Every enum type implicitly extends java.lang.Enum, which provides common methods like ordinal(), values(), and valueOf().

```java
enum Day {
    SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY;
}

public class Main {
    public static void main(String[] args) {
        Day today = Day.MONDAY;  // Assigning an enum value to a variable
        System.out.println("Today is: " + today);  // Output: Today is: MONDAY
    }
}
```

Enums with field and methods
```java
enum Day {
    SUNDAY("Relaxing"), MONDAY("Busy"), TUESDAY("Productive"),
    WEDNESDAY("Mid-week"), THURSDAY("Busy"), FRIDAY("Excited"), SATURDAY("Fun");

    private String description;

    // Constructor for enum
    Day(String description) {
        this.description = description;
    }

    // Method to get description
    public String getDescription() {
        return description;
    }

    @Override
    public String toString() {
        return "Day: " + this.name();
    }
}

public class Main {
    public static void main(String[] args) {
        // Accessing enum with methods
        Day today = Day.MONDAY;
        System.out.println(today + ": " + today.getDescription());
        System.out.println(Day.MONDAY);  // Output: Day: MONDAY
    }
}

Output:
MONDAY: Busy
Day: MONDAY
```

Enum Methods: Enums can have useful methods such as ordinal(), valueOf(), and values():
- ordinal(): Returns the position of the constant in the enum (0-based index). - Day.MONDAY.ordinal()
- valueOf(): Returns the enum constant for a string value.
- values(): Returns an array of all the enum constants.
```java
    public static void main(String[] args) {
        // Using ordinal() method
        System.out.println("Ordinal of MONDAY: " + Day.MONDAY.ordinal());  // Output: 1

        // Using values() method
        for (Day day : Day.values()) {
            System.out.println(day);  // Outputs all the days
        }

        // Using valueOf() method
        Day day = Day.valueOf("FRIDAY");
        System.out.println("The day is: " + day);  // Output: The day is: FRIDAY
    }
```
Output:
```yaml
Ordinal of MONDAY: 1
SUNDAY
MONDAY
TUESDAY
WEDNESDAY
THURSDAY
FRIDAY
SATURDAY
The day is: FRIDAY
```




