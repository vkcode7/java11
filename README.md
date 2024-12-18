# Java SE 11 Developer Certification (1Z0-819)

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

#### Enum with Interfaces:
An enum can implement interfaces as well. This is useful when you want to add common behavior to all constants of the enum.

```java
interface Describable {
    String getDescription();
}

enum Day implements Describable {
    SUNDAY("Relaxing"), MONDAY("Busy"), TUESDAY("Productive");

    private String description;

    Day(String description) {
        this.description = description;
    }

    @Override
    public String getDescription() {
        return description;
    }
}

public class Main {
    public static void main(String[] args) {
        System.out.println(Day.SUNDAY.getDescription());  // Output: Relaxing
    }
}

Output:
Relaxing
```

#### Local classes: a class defined within a method or a block of code.
```java
class OuterClass {
    void someMethod() {
        // Local class defined inside the method
        class LocalClass {
            void display() {
                System.out.println("Hello from Local Class!");
            }
        }

        LocalClass localClass = new LocalClass();  // Creating an instance of the local class
        localClass.display();  // Output: Hello from Local Class!
    }
}
```

<strong>Anonymous Local Class:</strong>
Local classes can also be anonymous (without a name), often used when the class is only needed for a short, one-time use, like implementing an interface or extending a class in a method.

```java
class Outer {
    void outerMethod() {
        // Anonymous inner class (local class without a name)
        Runnable r = new Runnable() {
            @Override
            public void run() {
                System.out.println("Running in the anonymous local class!");
            }
        };

        r.run();  // Output: Running in the anonymous local class!
    }
}

public class Main {
    public static void main(String[] args) {
        Outer outer = new Outer();
        outer.outerMethod();
    }
}
```

## EXCEPTIONS
### Java Exception Keywords:
- try: Defines a block of code that will be tested for exceptions.
- catch: Defines a block of code to handle a specific exception.
- finally: Defines a block of code that will execute after the try block, regardless of whether an exception occurred.
- throw: Used to explicitly throw an exception. - throw new IllegalArgumentException("Age must be at least 18.");
- throws: Declares that a method may throw an exception. public void methodName() throws ExceptionType {...}
  
```java
public class Main {
    public static void main(String[] args) {
        try {
            String str = null;
            int length = str.length();  // NullPointerException
        } catch (NullPointerException e) {
            System.out.println("Null Pointer Exception occurred.");
        } catch (Exception e) {
            System.out.println("An unknown exception occurred.");
        } finally {
            // Cleanup code
        }
    }
}
```


### Types of Common Exceptions:
**Checked Exceptions:** These are exceptions that are checked at compile-time. 
- IOException
- SQLException
- ClassNotFoundException
- FileNotFoundException

**Unchecked Exceptions:** These are runtime exceptions
- NullPointerException
- ArrayIndexOutOfBoundsException
- ArithmeticException
- IllegalArgumentException

### Custom Exceptions
You can define your own exception classes by extending the Exception class or RuntimeException class. These custom exceptions can provide more meaningful error handling specific to your application.

Example:
```java
class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);
    }
}

public class Main {
    public static void main(String[] args) {
        try {
            validateAge(15);
        } catch (InvalidAgeException e) {
            System.out.println("Caught: " + e.getMessage());
        }
    }

    static void validateAge(int age) throws InvalidAgeException {
        if (age < 18) {
            throw new InvalidAgeException("Age must be at least 18.");
        }
    }
}
```

### try-with-resources
In Java, try-with-resources is a feature introduced in Java 7 to simplify the management of resources that need to be closed after use (e.g., files, sockets, database connections). It ensures that resources are closed automatically at the end of the try block, even if an exception is thrown, preventing resource leaks and improving code safety.

The try-with-resources statement is used with resources that implement the AutoCloseable interface (or its more specific subclass java.io.Closeable). Classes like FileInputStream, BufferedReader, Connection, etc., implement this interface and can be used in a try-with-resources block.

```java
try (ResourceType1 resource1 = new ResourceType1();
     ResourceType2 resource2 = new ResourceType2()) {
    // Use the resources
} catch (ExceptionType e) {
    // Handle exception
}
```

**Example: Custom Resource (Implementing AutoCloseable)**
You can create your own custom resource class that implements the AutoCloseable interface.

```java
class MyResource implements AutoCloseable {
    public MyResource() {
        System.out.println("Resource created!");
    }

    public void doSomething() {
        System.out.println("Doing something with the resource...");
    }

    @Override
    public void close() {
        System.out.println("Resource closed!");
    }
}

public class Main {
    public static void main(String[] args) {
        try (MyResource resource = new MyResource()) {
            resource.doSomething();
        } catch (Exception e) {
            System.out.println("Exception: " + e.getMessage());
        }
    }
}
```

Output:
```csharp
Resource created!
Doing something with the resource...
Resource closed!
```

## STREAMS and LAMBDA Exp

### Lambda Expression Syntax

(parameters) -> expression
(parameter1, parameter2) -> expression
() -> expression
(parameters) -> {
    // multiple statements
}


```java

//(parameters) -> expression
// A lambda expression that takes one argument and returns its square
Function<Integer, Integer> square = (x) -> x * x;
System.out.println(square.apply(5));  // Output: 25

// A lambda expression where type is inferred from the context
Function<Integer, Integer> square = x -> x * x;
System.out.println(square.apply(5));  // Output: 25

//(parameter1, parameter2) -> expression
// A lambda expression that adds two integers
BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;
System.out.println(add.apply(5, 3));  // Output: 8

//() -> expression
// A lambda expression that returns a constant value
Supplier<String> getHello = () -> "Hello, World!";
System.out.println(getHello.get());  // Output: Hello, World!

/*
(parameters) -> {
    // multiple statements
}
*/
// A lambda expression that checks if a number is even
Predicate<Integer> isEven = (n) -> {
    if (n % 2 == 0) {
        return true;
    } else {
        return false;
    }
};
System.out.println(isEven.test(4));  // Output: true
```

### Lambda Expressions with Functional Interfaces
A functional interface is an interface that has exactly one **abstract** method. It can have other non abstract methods though. Lambda expressions are often used to provide the implementation of the abstract method of a functional interface.
```java
@FunctionalInterface //<== This annotation is necessary but if applied, compiler will ensure that only 1 abstract method is there
interface Runnable {
    void run();
}
```

**Common Functional Interfaces in Java:**
```java
//1. Runnable: A functional interface with no parameters and no return value.
Runnable r = () -> System.out.println("Running...");
r.run();  // Output: Running...

//2. Predicate<T>: A functional interface that takes a single argument and returns a boolean value.
Predicate<Integer> isEven = x -> x % 2 == 0;
System.out.println(isEven.test(4));  // Output: true

//3. Function<T, R>: A functional interface that takes one argument of type T and produces a result of type R.
Function<String, Integer> length = s -> s.length();
System.out.println(length.apply("Hello"));  // Output: 5

//4. Consumer<T>: A functional interface that takes one argument and performs an action without returning any result.
Consumer<String> print = s -> System.out.println(s);
print.accept("Hello");  // Output: Hello

//5. Supplier<T>: A functional interface that supplies a value without taking any arguments.
Supplier<Double> random = () -> Math.random();
System.out.println(random.get());

//6. BiFunction<T, U, R>: A functional interface that takes two arguments and produces a result.
BiFunction<Integer, Integer, Integer> multiply = (a, b) -> a * b;
System.out.println(multiply.apply(2, 3));  // Output: 6
```

Points to remembers:
- Function<T,R> one input and one output
- Consumer<T>: one input and no output
- Supplier<R>: No input but one output
- Predicate<T>: one input and boolean output
- BiFunction<T,U,R>: 2 inputs, one output
- BiConsumer<T,U>: 2 inputs and no output
- BiPredicaate<T,U>: 2 inputs and one bollean output
- BInaryOPerator<T>: 2 inputs of type T and output of type T


### Example Usage in Java Collections
Lambda expressions are commonly used with Java's Streams API and Collections.

Example: Using forEach with a List
```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("Apple", "Banana", "Cherry");

        // Using forEach with a lambda expression
        list.forEach(item -> System.out.println(item));
    }
}
```

Example: Sorting a List with a Lambda Expression
```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("Banana", "Apple", "Cherry");

        // Sorting a list using a lambda expression
        Collections.sort(list, (a, b) -> a.compareTo(b));
        System.out.println(list);  // Output: [Apple, Banana, Cherry]
    }
}
```
Example: Predicate
```java
@FunctionalInterface
public interface Predicate<T> {
    boolean test(T t);
}
```

```java
import java.util.Arrays;
import java.util.List;
import java.util.function.Predicate;
import java.util.stream.Collectors;

public class PredicateExample {
    public static void main(String[] args) {
        // List of numbers
        List<Integer> numbers = Arrays.asList(10, 15, 20, 25, 30);

        // Predicate to check if a number is even
        Predicate<Integer> isEven = n -> n % 2 == 0;

        // Filter numbers using the predicate
        List<Integer> evenNumbers = numbers.stream()
                                           .filter(isEven)
                                           .collect(Collectors.toList());

        System.out.println("Even numbers: " + evenNumbers); // Output: [10, 20, 30]
    }
}
```

### Streams:
In Java, streams are a part of the Stream API introduced in Java 8, which provides a functional programming approach to process sequences of data. Streams allow operations on collections (like List, Set, Map, etc.) in a declarative, pipeline-based manner.

Key Features of Streams:
- Declarative Style: Use functional-style operations (e.g., map, filter) instead of imperative loops.
- Lazy Evaluation: Intermediate operations (e.g., filter, map) are only executed when a terminal operation (e.g., collect, forEach) is invoked.
- Parallel Processing: Streams can be easily processed in parallel for performance optimization.
- Immutable: Streams do not modify the original data source.

#### Stream Pipeline:
A stream pipeline consists of three main parts:

- Source: A data source such as a collection, array, or I/O channel.
- Intermediate Operations: Transformations applied to the stream (e.g., filter, map, sorted).
- Terminal Operations: The final operation that produces a result or a side effect (e.g., collect, forEach).

Example 1: Filter and Map
```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "David");

        // Stream to filter names starting with 'A' and convert to uppercase
        List<String> filteredNames = names.stream()
                                          .filter(name -> name.startsWith("A")) // Intermediate operation
                                          .map(String::toUpperCase)             // Intermediate operation
                                          .collect(Collectors.toList());        // Terminal operation

        System.out.println(filteredNames); // Output: [ALICE]
    }
}
```

Example 2: Reduce: The reduce operation aggregates stream elements into a single value.
```java
import java.util.Arrays;
import java.util.List;

public class StreamReduceExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

        // Sum of all numbers
        int sum = numbers.stream()
                         .reduce(0, Integer::sum); // Identity = 0, BinaryOperator = Integer::sum

        System.out.println("Sum: " + sum); // Output: Sum: 15
    }
}
```

Example 3: Parallel Streams: Streams can be processed in parallel for better performance on large datasets.
```java
import java.util.stream.IntStream;

public class ParallelStreamExample {
    public static void main(String[] args) {
        // Sum of numbers from 1 to 1,000,000 using parallel stream
        long sum = IntStream.rangeClosed(1, 1_000_000)
                            .parallel()
                            .sum();

        System.out.println("Sum: " + sum); // Output: Sum: 500000500000
    }
}
```

Advantages of Streams:
- Readable Code: Streams provide a concise and readable way to process data.
- Parallelism: Easily process data in parallel to utilize multi-core systems.
- Less Boilerplate: Avoid writing explicit loops and conditionals.

![image](https://github.com/user-attachments/assets/69457990-4942-47a8-bc9c-bf13ea83053c)


### The Stream class
The Stream class in Java is part of the java.util.stream package and represents a sequence of elements supporting functional-style operations. It is a central component of the Stream API

Stream Creation:
```java
//From Collections:
List<Integer> list = Arrays.asList(1, 2, 3, 4);
Stream<Integer> stream = list.stream();

//From Arrays:
String[] array = {"a", "b", "c"};
Stream<String> stream = Arrays.stream(array);

//From Static Methods:
Stream<Integer> stream = Stream.of(1, 2, 3, 4, 5);
Stream<String> infiniteStream = Stream.generate(() -> "Hello").limit(10);

//From Files (Java NIO):
Stream<String> lines = Files.lines(Paths.get("file.txt"));
```

![image](https://github.com/user-attachments/assets/86fc342b-76b9-4e67-8981-da91c1803ee7)

**Terminal Operations:** These operations trigger the computation of the stream pipeline and produce a result or a side effect.

- collect(Collector<T, A, R>): Collects elements into a collection (e.g., List, Set).
- forEach(Consumer<T>): Performs an action for each element.
- reduce(BinaryOperator<T>): Reduces elements into a single result.
- count(): Counts the elements.
- findFirst(): Returns the first element.
- findAny(): Returns any element (useful for parallel streams).
- allMatch, anyMatch, noneMatch: Tests whether elements match a given predicate.

Example:
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
int sum = numbers.stream()
                 .reduce(0, Integer::sum); // Sum all numbers
System.out.println("Sum: " + sum); // Output: Sum: 15
```

## THREADS
In Java, there are several ways to create and manage threads. 
#### 1. By Extending the Thread Class
The simplest way to create a thread is by extending the Thread class and overriding its run() method. The run() method contains the code that will be executed when the thread starts.

Example:
```java
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Thread is running");
    }
}

public class ThreadExample {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        t1.start();  // Start the thread
    }
}
```
start() initiates the thread and invokes the run() method.

#### 2. By Implementing the Runnable Interface
Another way to create a thread is by implementing the Runnable interface. This approach is preferred over extending the Thread class because it allows you to extend other classes as well (since Java supports single inheritance). The run() method is implemented in the Runnable interface, and an instance of Runnable is passed to a Thread object.

Example:
```java
class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("Runnable thread is running");
    }
}

public class ThreadExample {
    public static void main(String[] args) {
        MyRunnable runnable = new MyRunnable();
        Thread t1 = new Thread(runnable);  // Create thread using Runnable
        t1.start();  // Start the thread
    }
}
```

#### 3. Using ExecutorService (Thread Pool)
For better thread management, especially when dealing with multiple threads, you can use an ExecutorService. This is part of the java.util.concurrent package and provides thread pooling, which helps manage a pool of worker threads for executing tasks. ExecutorService also handles thread creation, scheduling, and shutdown.

Example (Using ExecutorService):
```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class ExecutorServiceExample {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(2);  // Creates a thread pool with 2 threads

        Runnable task = () -> System.out.println("Thread from ExecutorService is running");
        executor.submit(task);  // Submit the task to be executed

        executor.shutdown();  // Shut down the executor
    }
}
```

- Executors.newFixedThreadPool(int n): Creates a pool of n threads.
- executor.submit(task): Submits a task for execution by a thread from the pool.
- executor.shutdown(): Initiates an orderly shutdown of the executor.

#### 4. Using Callable and Future
Similar to Runnable, but Callable can return a result or throw an exception. You can submit Callable tasks to an ExecutorService and retrieve their result using a Future object.

Example (Using Callable):
```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class CallableExample {
    public static void main(String[] args) throws Exception {
        ExecutorService executor = Executors.newSingleThreadExecutor();

        Callable<Integer> task = () -> {
            Thread.sleep(1000);  // Simulating long task
            return 123;  // Return value
        };

        Future<Integer> result = executor.submit(task);  // Submit the task
        System.out.println("Task result: " + result.get());  // Get the result of the task

        executor.shutdown();  // Shut down the executor
    }
}
```
Callable.call(): Returns a result (or throws an exception).
Future.get(): Retrieves the result of the task once it completes.

#### 5. Using ForkJoinPool
The ForkJoinPool is designed for tasks that can be recursively divided into smaller tasks (forked) and later combined (joined). It is useful for parallel processing of tasks like divide-and-conquer algorithms.

Example (Using ForkJoinPool):
```java
import java.util.concurrent.RecursiveTask;
import java.util.concurrent.ForkJoinPool;

public class ForkJoinExample {
    static class SumTask extends RecursiveTask<Integer> {
        private final int start;
        private final int end;

        public SumTask(int start, int end) {
            this.start = start;
            this.end = end;
        }

        @Override
        protected Integer compute() {
            if (end - start <= 2) {
                return start + end;  // Base case
            }
            int mid = (start + end) / 2;
            SumTask left = new SumTask(start, mid);
            SumTask right = new SumTask(mid + 1, end);

            left.fork();  // Fork left task
            right.fork(); // Fork right task

            return left.join() + right.join();  // Join results from left and right tasks
        }
    }

    public static void main(String[] args) {
        ForkJoinPool pool = new ForkJoinPool();
        SumTask task = new SumTask(1, 10);
        int result = pool.invoke(task);  // Invoke the task
        System.out.println("Sum result: " + result);  // Output: Sum result: 55
    }
}
```

Each method has its use case:

- Thread and Runnable are typically used for simpler tasks or when you need to extend a class.
- ExecutorService is ideal for managing a pool of threads and handling tasks asynchronously.
- Callable is used when you need the thread to return a result.
- ForkJoinPool is used for parallel tasks that can be divided into smaller tasks.

### Concurrency Tools in Java
Java provides several tools and APIs to handle concurrency effectively:

#### 1. Synchronization
Synchronization ensures that only one thread can access a shared resource at a time, preventing race conditions.

Synchronized Methods:
java
```
public synchronized void method() {
    // Critical section
}
```
Synchronized Blocks:
```java
synchronized (lockObject) {
    // Critical section
}
```
#### 2. Lock Framework
The java.util.concurrent.locks package provides locks for more flexible thread synchronization.

java
```
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

public class Main {
    private final Lock lock = new ReentrantLock();

    public void method() {
        lock.lock();
        try {
            // Critical section
        } finally {
            lock.unlock();
        }
    }
}
```

#### 3. Concurrent Collections
Thread-safe collections like ConcurrentHashMap, CopyOnWriteArrayList, and BlockingQueue in the java.util.concurrent package are designed for concurrent access.

#### 4. Atomic Variables
The java.util.concurrent.atomic package provides atomic classes (AtomicInteger, AtomicLong, etc.) to perform atomic operations without explicit synchronization.

```java
AtomicInteger count = new AtomicInteger(0);
count.incrementAndGet();
```

### Concurrency Design Patterns
Producer-Consumer: One thread produces data while another consumes it.
Read-Write Lock: Multiple threads can read simultaneously, but only one can write at a time.
Future Pattern: Asynchronous computation results that can be retrieved later.

## LOCALIZATION / INTERNATIONALIZATION

### Locale Class
The Locale class in Java represents a specific geographical, cultural, or political region. It is used to tailor information to the user's regional preferences, such as language, country, or variant. The class is part of the java.util package and plays a critical role in internationalization (i18n).

Creating Locales
```java
import java.util.Locale;

public class LocaleExample {
    public static void main(String[] args) {
        // Locale with language only
        Locale locale1 = new Locale("en");
        
        // Locale with language and country
        Locale locale2 = new Locale("fr", "FR");
        
        // Locale with language, country, and variant
        Locale locale3 = new Locale("en", "US", "WIN");

        // Using factory method
        Locale locale4 = Locale.forLanguageTag("en-GB");

        System.out.println(locale1); // Output: en
        System.out.println(locale2); // Output: fr_FR
        System.out.println(locale3); // Output: en_US_WIN
        System.out.println(locale4); // Output: en_GB
    }
}
```

Using LOcales for formatting
```java
import java.text.NumberFormat;
import java.util.Locale;

public class LocaleFormattingExample {
    public static void main(String[] args) {
        double amount = 1234567.89;

        // US locale
        Locale usLocale = Locale.US;
        NumberFormat usFormat = NumberFormat.getCurrencyInstance(usLocale);
        System.out.println("US: " + usFormat.format(amount)); // Output: US: $1,234,567.89

        // French locale
        Locale frLocale = Locale.FRANCE;
        NumberFormat frFormat = NumberFormat.getCurrencyInstance(frLocale);
        System.out.println("France: " + frFormat.format(amount)); // Output: France: 1 234 567,89 €
    }
}
```

### Use Cases
- Formatting: Dates, times, numbers, and currencies based on locale.
- Resource Bundles: Load locale-specific text and data from ResourceBundle.
- Internationalization (i18n): Applications designed for global audiences use Locale for regional preferences.

### ResourceBundle
A ResourceBundle in Java is used to store locale-specific text and data, allowing developers to internationalize their applications. It enables loading localized content (e.g., strings, messages) based on the current or specified Locale.

Structure of ResourceBundle: A ResourceBundle typically consists of property files with the .properties extension. Each file corresponds to a specific Locale and contains key-value pairs.

### Example Files
Messages_en.properties (default for English)

```properties
greeting=Hello
farewell=Goodbye
inquiry=How are you?
```

Messages_fr.properties (French locale)
```properties
greeting=Bonjour
farewell=Au revoir
inquiry=Comment ça va?
```

Messages_es.properties (Spanish locale)
```properties
Copy code
greeting=Hola
farewell=Adiós
inquiry=¿Cómo estás?
```

Loading and Using ResourceBundle
```java
import java.util.Locale;
import java.util.ResourceBundle;

public class ResourceBundleExample {
    public static void main(String[] args) {
        // Default Locale
        Locale defaultLocale = Locale.getDefault();

        // French Locale
        Locale frenchLocale = new Locale("fr", "FR");

        // Spanish Locale
        Locale spanishLocale = new Locale("es", "ES");

        // Load ResourceBundle for the default Locale
        ResourceBundle bundleDefault = ResourceBundle.getBundle("Messages", defaultLocale);

        // Load ResourceBundle for French
        ResourceBundle bundleFrench = ResourceBundle.getBundle("Messages", frenchLocale);

        // Load ResourceBundle for Spanish
        ResourceBundle bundleSpanish = ResourceBundle.getBundle("Messages", spanishLocale);

        // Print messages for different locales
        System.out.println("Default Locale - Greeting: " + bundleDefault.getString("greeting"));
        System.out.println("French Locale - Greeting: " + bundleFrench.getString("greeting"));
        System.out.println("Spanish Locale - Greeting: " + bundleSpanish.getString("greeting"));
    }
}
```
Output: Assuming your default locale is English:
```yaml
Default Locale - Greeting: Hello
French Locale - Greeting: Bonjour
Spanish Locale - Greeting: Hola
```

### Bi-directional text: LTR <-> RTL
Key Classes in Java for BiDi Text:
- 1. java.text.Bidi
The Bidi class supports bidirectional text analysis. It determines the embedding levels of text and whether characters should be rendered in LTR or RTL order.
- 2. java.awt.font.TextLayout
Used for rendering text with complex layouts, including BiDi. Can process mixed-direction text for graphical display.

#### Using the Bidi Class
The Bidi class analyzes a string for its directionality and reorders characters for proper display.

Example: Detecting and Reordering Text
```java
import java.text.Bidi;

public class BidiExample {
    public static void main(String[] args) {
        // A string with mixed LTR and RTL text
        String text = "This is English text \u0627\u0644\u0646\u0635 \u0627\u0644\u0639\u0631\u0628\u064A (Arabic text)";

        // Analyze the text for directionality
        Bidi bidi = new Bidi(text, Bidi.DIRECTION_DEFAULT_LEFT_TO_RIGHT);

        // Check if the text is mixed-direction
        if (bidi.isMixed()) {
            System.out.println("The text has mixed directions.");
        }

        // Get reordered text
        String reorderedText = bidi.writeReordered(Bidi.DIRECTION_LEFT_TO_RIGHT);
        System.out.println("Reordered text: " + reorderedText);
    }
}
```
Output:
```yaml
The text has mixed directions.
Reordered text: This is English text (Arabic text) النص العربي
```

**Summary**
- Bidi: For analyzing and reordering bidirectional text.
- TextLayout: For rendering complex bidirectional layouts.
- Built-in support in Swing and JavaFX simplifies handling BiDi in GUI applications.
- BiDi features integrate well with Java's internationalization framework.

#### Locale and Currency
Here is an example of how to use Locale and NumberFormat to format currency values based on a specific locale in Java:
```java
import java.text.NumberFormat;
import java.util.Locale;

public class CurrencyLocaleExample {
    public static void main(String[] args) {
        double amount = 12345.67;

        // Locale for US
        Locale usLocale = Locale.US;
        NumberFormat usCurrencyFormat = NumberFormat.getCurrencyInstance(usLocale);
        System.out.println("US: " + usCurrencyFormat.format(amount));

        // Locale for France
        Locale franceLocale = Locale.FRANCE;
        NumberFormat franceCurrencyFormat = NumberFormat.getCurrencyInstance(franceLocale);
        System.out.println("France: " + franceCurrencyFormat.format(amount));

        // Locale for Japan
        Locale japanLocale = Locale.JAPAN;
        NumberFormat japanCurrencyFormat = NumberFormat.getCurrencyInstance(japanLocale);
        System.out.println("Japan: " + japanCurrencyFormat.format(amount));

        // Locale for India (custom locale with INR symbol)
        Locale indiaLocale = new Locale("en", "IN");
        NumberFormat indiaCurrencyFormat = NumberFormat.getCurrencyInstance(indiaLocale);
        System.out.println("India: " + indiaCurrencyFormat.format(amount));
    }
}
```
Output:
```makefile
US: $12,345.67
France: 12 345,67 €
Japan: ¥12,346
India: ₹12,345.67
```

The Currency class in Java, part of the java.util package, represents ISO 4217 currency codes and provides information about a specific currency, such as its symbol or default fractional digits.

You can use the Currency class in conjunction with the Locale class to retrieve currency-related information or format amounts.
```java
import java.util.Currency;
import java.util.Locale;

public class CurrencyExample {
    public static void main(String[] args) {
        // Locale for US
        Locale usLocale = Locale.US;
        Currency usCurrency = Currency.getInstance(usLocale);
        System.out.println("Currency for US:");
        System.out.println("Code: " + usCurrency.getCurrencyCode());
        System.out.println("Symbol: " + usCurrency.getSymbol());
        System.out.println("Default Fraction Digits: " + usCurrency.getDefaultFractionDigits());
        
        System.out.println();

        // Locale for Japan
        Locale japanLocale = Locale.JAPAN;
        Currency japanCurrency = Currency.getInstance(japanLocale);
        System.out.println("Currency for Japan:");
        System.out.println("Code: " + japanCurrency.getCurrencyCode());
        System.out.println("Symbol: " + japanCurrency.getSymbol());
        System.out.println("Default Fraction Digits: " + japanCurrency.getDefaultFractionDigits());

        System.out.println();

        // Custom Currency for India
        Locale indiaLocale = new Locale("en", "IN");
        Currency indiaCurrency = Currency.getInstance(indiaLocale);
        System.out.println("Currency for India:");
        System.out.println("Code: " + indiaCurrency.getCurrencyCode());
        System.out.println("Symbol: " + indiaCurrency.getSymbol());
        System.out.println("Default Fraction Digits: " + indiaCurrency.getDefaultFractionDigits());
    }
}
```
Output:
```yaml
Currency for US:
Code: USD
Symbol: $
Default Fraction Digits: 2

Currency for Japan:
Code: JPY
Symbol: ¥
Default Fraction Digits: 0

Currency for India:
Code: INR
Symbol: ₹
Default Fraction Digits: 2
```

**Using Currency with NumberFormat**<br>
The Currency class can also be paired with NumberFormat for formatting:

```java
import java.text.NumberFormat;
import java.util.Currency;
import java.util.Locale;

public class CurrencyFormattingExample {
    public static void main(String[] args) {
        double amount = 12345.67;

        // Locale for UK
        Locale ukLocale = Locale.UK;
        Currency ukCurrency = Currency.getInstance(ukLocale);
        NumberFormat currencyFormat = NumberFormat.getCurrencyInstance(ukLocale);
        currencyFormat.setCurrency(ukCurrency);

        System.out.println("Formatted Amount in UK Locale: " + currencyFormat.format(amount));
    }
}
```
Output:
```yaml
Copy code
Formatted Amount in UK Locale: £12,345.67
```

#### LocalDateTime/LocalTime/DateTimeFormatter classes
```java
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

public class LocalDateTimeExample {
    public static void main(String[] args) {
        // Current Date-Time
        LocalDateTime now = LocalDateTime.now();
        System.out.println("Current Date-Time: " + now);

        // Custom Date-Time
        LocalDateTime customDateTime = LocalDateTime.of(2023, 12, 25, 10, 30);
        System.out.println("Custom Date-Time: " + customDateTime);

        // Adding days and hours
        LocalDateTime futureDateTime = now.plusDays(10).plusHours(2);
        System.out.println("Future Date-Time: " + futureDateTime);

        // Formatting Date-Time
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm");
        System.out.println("Formatted Date-Time: " + now.format(formatter));

        // Parsing a String to LocalDateTime
        String dateTimeString = "2023-12-25 10:30";
        LocalDateTime parsedDateTime = LocalDateTime.parse(dateTimeString, formatter);
        System.out.println("Parsed Date-Time: " + parsedDateTime);
    }
}
```
Output:
```yaml
Current Date-Time: 2024-11-26T20:37:37.450499955
Custom Date-Time: 2023-12-25T10:30
Future Date-Time: 2024-12-06T22:37:37.450499955
Formatted Date-Time: 2024-11-26 20:37
Parsed Date-Time: 2023-12-25T10:30
```

#### NumberFormat/DecimalFormat
The NumberFormat and DecimalFormat classes in Java are used to format numbers for display in a locale-sensitive or custom manner. Both are part of the java.text package.

## ARRAYS and COLLECTIONS
### 1. List
- An ordered collection of elements.
- Allows duplicate elements.
- Common implementations: ArrayList, LinkedList.
- 
Example: Using ArrayList
```java
import java.util.ArrayList;
import java.util.List;

public class ListExample {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();

        // Adding elements
        list.add("Apple");
        list.add("Banana");
        list.add("Cherry");
        list.add("Apple"); // Duplicates allowed

        System.out.println("List: " + list);

        // Access by index
        System.out.println("Element at index 1: " + list.get(1));

        // Remove an element
        list.remove("Banana");
        System.out.println("After removal: " + list);
    }
}
```
Output:
```yaml
List: [Apple, Banana, Cherry, Apple]
Element at index 1: Banana
After removal: [Apple, Cherry, Apple]
```

### 2. Set
- A collection that does not allow duplicate elements.
- No guaranteed order (use LinkedHashSet for insertion order or TreeSet for sorted order).
- Common implementations: HashSet, LinkedHashSet, TreeSet.
  
Example: Using HashSet
```java
import java.util.HashSet;
import java.util.Set;

public class SetExample {
    public static void main(String[] args) {
        Set<String> set = new HashSet<>();

        // Adding elements
        set.add("Apple");
        set.add("Banana");
        set.add("Cherry");
        set.add("Apple"); // Duplicate ignored

        System.out.println("Set: " + set);

        // Check for an element
        System.out.println("Contains 'Banana': " + set.contains("Banana"));

        // Remove an element
        set.remove("Banana");
        System.out.println("After removal: " + set);
    }
}
```
Output:
```yaml
Set: [Banana, Cherry, Apple]
Contains 'Banana': true
After removal: [Cherry, Apple]
```

### 3. Queue
- A collection that follows FIFO (First-In-First-Out) order.
- Common implementations: LinkedList (as a queue), PriorityQueue.
  
Example: Using LinkedList as a Queue
```java
import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {
    public static void main(String[] args) {
        Queue<String> queue = new LinkedList<>();

        // Adding elements
        queue.add("First");
        queue.add("Second");
        queue.add("Third");

        System.out.println("Queue: " + queue);

        // Peek at the front
        System.out.println("Front element: " + queue.peek());

        // Remove the front element
        queue.poll();
        System.out.println("After poll: " + queue);
    }
}
```
Output:

```yaml
Queue: [First, Second, Third]
Front element: First
After poll: [Second, Third]
```

### 4. Map
- A collection of key-value pairs.
- Keys must be unique; values can be duplicated.
- Common implementations: HashMap, LinkedHashMap, TreeMap.

Example: Using HashMap
```java
import java.util.HashMap;
import java.util.Map;

public class MapExample {
    public static void main(String[] args) {
        Map<Integer, String> map = new HashMap<>();

        // Adding key-value pairs
        map.put(1, "Apple");
        map.put(2, "Banana");
        map.put(3, "Cherry");

        System.out.println("Map: " + map);

        // Access by key
        System.out.println("Value for key 2: " + map.get(2));

        // Remove an entry
        map.remove(3);
        System.out.println("After removal: " + map);

        // Iterating over entries
        for (Map.Entry<Integer, String> entry : map.entrySet()) {
            System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
        }
    }
}
```

Output:
```yaml
Map: {1=Apple, 2=Banana, 3=Cherry}
Value for key 2: Banana
After removal: {1=Apple, 2=Banana}
Key: 1, Value: Apple
Key: 2, Value: Banana
```
**Summary of Usage**
![image](https://github.com/user-attachments/assets/6dd18af2-220e-46e8-a18b-ab2880dd4ca8)

Refer https://github.com/dlbunker/Ps-collections-1z0-819 for cheatsheets
## Basic Collection Type Attributes and Characterists
You should be able to answer the following questions about each core Collection type

|     | Elements Ordered?   | Allows Duplicates? | Elements Added/Removed in a Certain Order? | Allows Key/Values? |
|-----|---------------------|--------------------|--------------------------------------------|--------------------|
|List | Yes - Numbered Index| Yes                | No                                         | No                 |
|Set  | No                  | No                 | No                                         | No                 |
|Queue| Yes - Placed Order  | Yes                | Yes                                        | No                 |
|Map  | No                  | Yes - Values only  | No                                         | Yes                |


## Specific Collection Type Attributes and Characterists
You should be able to answer the following questions about each Collection implementation provided by Java

| Java Type| Parent Interface Type | Allows null? | Elements Sorted? | Uses hashCode? | Uses compareTo? |
|----------|-----------------------|--------------|------------------|----------------|-----------------|
|ArrayList | List                  | Yes          | No               | No             | No              |
|LinkedList| List and Queue        | Yes          | No               | No             | No              |
|HashSet   | Set                   | Yes          | No               | Yes            | No              |
|TreeSet   | Set                   | No           | Yes              | No             | Yes             |
|HashMap   | Map                   | Yes          | No               | Yes            | No              |
|TreeMap   | Map                   | No           | Yes              | No             | Yes             |


### Generics
Generics in Java allow you to define classes, interfaces, and methods with type parameters. This provides strong type checking at compile-time, reducing runtime errors and enabling reusable and type-safe code.

Key Benefits of Generics
- Type Safety: Detects type errors during compilation.
- Code Reusability: Enables writing methods or classes that work with any type.
- Eliminates Casting: Reduces boilerplate code for type casting.

Syntax: Generics are specified using angle brackets (<>) with a type parameter.

- T: Type (can represent any type).
- E: Element (used in collections).
- K and V: Key and Value (used in maps).
- ?: Wildcard (unknown type).

Examples of Generics
#### 1. Generic Class
A class with a type parameter that can work with any data type.

```java
public class GenericBox<T> {
    private T item;

    public void setItem(T item) {
        this.item = item;
    }

    public T getItem() {
        return item;
    }

    public static void main(String[] args) {
        // GenericBox for Integer
        GenericBox<Integer> intBox = new GenericBox<>();
        intBox.setItem(123);
        System.out.println("Integer Box: " + intBox.getItem());

        // GenericBox for String
        GenericBox<String> strBox = new GenericBox<>();
        strBox.setItem("Hello");
        System.out.println("String Box: " + strBox.getItem());
    }
}
```
Output:
```mathematica
Integer Box: 123
String Box: Hello
```

#### 2. Generic Method
A method that can accept arguments of any type.

```java
public class GenericMethodExample {
    // Generic method
    public static <T> void printArray(T[] array) {
        for (T element : array) {
            System.out.print(element + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        // Integer array
        Integer[] intArray = {1, 2, 3};
        printArray(intArray);

        // String array
        String[] strArray = {"A", "B", "C"};
        printArray(strArray);
    }
}
```

Output:
```css
Copy code
1 2 3 
A B C
```

### 3. Generic Interface
An interface with type parameters.

```java
interface GenericInterface<T> {
    void display(T item);
}

class GenericClass<T> implements GenericInterface<T> {
    @Override
    public void display(T item) {
        System.out.println("Item: " + item);
    }
}

public class GenericInterfaceExample {
    public static void main(String[] args) {
        GenericInterface<String> strGeneric = new GenericClass<>();
        strGeneric.display("Hello, Generics!");

        GenericInterface<Integer> intGeneric = new GenericClass<>();
        intGeneric.display(42);
    }
}
```

Output:
```makefile
Item: Hello, Generics!
Item: 42
```

#### 4. Wildcards (?)
Used when the exact type is not known.

Upper Bound Wildcard (<? extends Type>): Accepts Type or its subclasses.

```java
import java.util.List;

public class WildcardExample {
    public static void printNumbers(List<? extends Number> list) {
        for (Number number : list) {
            System.out.println(number);
        }
    }

    public static void main(String[] args) {
        List<Integer> intList = List.of(1, 2, 3);
        List<Double> doubleList = List.of(1.1, 2.2, 3.3);

        printNumbers(intList);
        printNumbers(doubleList);
    }
}
```

Lower Bound Wildcard (<? super Type>): Accepts Type or its superclasses.

```java
import java.util.ArrayList;
import java.util.List;

public class LowerBoundExample {
    public static void addNumbers(List<? super Integer> list) {
        list.add(1);
        list.add(2);
    }

    public static void main(String[] args) {
        List<Number> numberList = new ArrayList<>();
        addNumbers(numberList);
        System.out.println(numberList);
    }
}
```

#### 5. Generic Collections
Java collections extensively use generics.

Example: Using a Generic ArrayList
```java
import java.util.ArrayList;

public class GenericCollectionExample {
    public static void main(String[] args) {
        // List of Strings
        ArrayList<String> names = new ArrayList<>();
        names.add("Alice");
        names.add("Bob");

        for (String name : names) {
            System.out.println(name);
        }

        // List of Integers
        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add(10);
        numbers.add(20);

        for (Integer number : numbers) {
            System.out.println(number);
        }
    }
}
```

**Summary of Generics:**
- Type Safety:	Prevents runtime ClassCastException.
- Reusability:	Allows code to work with different types.
- Wildcards:	Used when the exact type is unknown.
- Bounded Types:	Restrict types to a specific range (extends or super).
- Erasure:	Generic types are replaced with Object or bound types during compilation.

## MODULES
A Java module is a grouping of related packages and resources into a single unit, introduced in Java 9 as part of the Java Platform Module System (JPMS). Modules are optional. JAR File is NOT a module.

### Key Features of Java Modules:
#### Encapsulation:
- A module explicitly declares which packages it exposes for external use.
- Packages not explicitly exported remain inaccessible to other modules.

#### Dependency Management:
A module specifies which other modules it depends on.

#### Improved Security and Performance:
- Only required modules are loaded, reducing runtime overhead.
- Encapsulation ensures restricted access to internal APIs.

#### Better Deployment:
Supports creating custom runtimes using jlink with only the required modules.

### Defining a Module
A module is defined using a module-info.java file, which resides in the root of the module directory.

Syntax
```java
module <module-name> {
    // Declare dependencies
    requires <module-name>;
    
    // Export packages
    exports <package-name>;
    
    // Use services
    uses <interface-name>;
    
    // Provide implementations for services
    provides <interface-name> with <class-name>;
}
```

#### Example: Module Definition
- Consider a module named com.example.app:

```java
// module-info.java
module com.example.app {
    requires java.base; // Automatically required; optional to specify
    requires com.example.util;

    exports com.example.app.api;
}
```

Structure
```arduino
src
 ├── com.example.app
 │   ├── module-info.java
 │   ├── com
 │       └── example
 │           └── app
 │               ├── api
 │               │    └── HelloWorld.java
 │               └── internal
 │                    └── AppHelper.java
 └── com.example.util
     ├── module-info.java
     ├── com
         └── example
             └── util
                 └── Utility.java
```

#### Exporting and Using Packages
- com.example.app module exports com.example.app.api but keeps com.example.app.internal hidden.
- Other modules can use only the exported com.example.app.api package.

#### Consuming a Module
Another module, say com.example.main, can depend on com.example.app:

```java
// module-info.java in com.example.main
module com.example.main {
    requires com.example.app;
}
```

### Core Directives in module-info.java
Directive:	Purpose
- requires:	Declares dependency on another module.
- exports:	Makes a package accessible to other modules.
- opens:	Allows reflection-based access to a package (e.g., for frameworks like Spring).
- provides:	Declares that the module provides an implementation of a service.
- uses:	Declares that the module consumes a service.
- transitive:	Ensures that modules requiring this module implicitly require its dependencies (requires transitive).

### Built-in Java Modules
Java provides several predefined modules, such as:

- java.base	Core classes like java.lang, java.util (automatically included).
- java.sql	JDBC API for database access.
- java.xml	XML processing.
- java.desktop	GUI libraries like Swing and AWT.

### Custom Runtime Using Modules
The jlink tool can create a custom runtime with only the required modules, reducing size and improving performance:

```bash
jlink --module-path <path_to_modules> --add-modules com.example.main --output custom-runtime
```

### Services

In Java, services are part of the Service Provider Framework introduced in Java 9 to work seamlessly with the module system. They allow modules to provide implementations of a service (an interface or abstract class) and let other modules consume these services without knowing the exact implementation.

This decoupling enhances modularity, making applications more extensible and easier to maintain.

#### Key Components of the Service Framework
- Service Interface: Defines the functionality that service providers implement.
- Service Provider: A class that implements the service interface.
- Service Consumer: A module or class that uses the service.
- ServiceLoader: A utility class to load service implementations at runtime.

#### How Services Work in Modules
The module system uses the provides and uses directives in module-info.java for service-based programming.

- provides: Declares that a module provides an implementation of a service.
- uses: Declares that a module consumes a service.

#### Example 
1. Defining a Service Interface
```java
// src/com.example.service/Service.java
package com.example.service;

public interface Service {
    void execute();
}
```

2. Creating a Service Provider
```java
// src/com.example.provider/Provider.java
package com.example.provider;

import com.example.service.Service;

public class Provider implements Service {
    @Override
    public void execute() {
        System.out.println("Service executed by Provider");
    }
}
```

module-info.java for the Provider Module:
```java
module com.example.provider {
    requires com.example.service; // Depends on the service interface
    provides com.example.service.Service with com.example.provider.Provider; // Provides implementation
}
```

3. Using the Service in a Consumer Module
```java
// src/com.example.consumer/Main.java
package com.example.consumer;

import com.example.service.Service;
import java.util.ServiceLoader;

public class Main {
    public static void main(String[] args) {
        ServiceLoader<Service> loader = ServiceLoader.load(Service.class);
        for (Service service : loader) {
            service.execute(); // Dynamically loads and executes the service
        }
    }
}
```

module-info.java for the Consumer Module:
```java
module com.example.consumer {
    requires com.example.service; // Depends on the service interface
    uses com.example.service.Service; // Declares that it uses the service
}
```

Structure
```arduino
src
 ├── com.example.service
 │   ├── module-info.java
 │   └── com.example.service.Service.java
 ├── com.example.provider
 │   ├── module-info.java
 │   └── com.example.provider.Provider.java
 └── com.example.consumer
     ├── module-info.java
     └── com.example.consumer.Main.java
```

#### Key Points
- Service Declaration: A module providing a service uses the provides directive.
- Service Consumption: A module consuming a service uses the uses directive.
- Dynamic Loading: ServiceLoader dynamically loads available implementations at runtime.
- Encapsulation: Consumers do not need to know the details of the service providers.

#### Benefits of Using Services in Modules
- Decoupling: Consumers depend on the service interface, not on specific implementations.
- Extensibility: New implementations can be added without changing the consumer module.
- Dynamic Behavior: Services can be loaded at runtime, making the application more flexible.
- Enhanced Maintainability: Clear boundaries between service providers and consumers.


### How Java Finds and Loads Modules
Java finds and loads modules using the module path, a mechanism introduced with the Java Platform Module System (JPMS) in Java 9. The module path is a sequence of directories or .jar files where the Java runtime searches for modules. It acts similarly to the classpath, but it is specifically designed for modular applications.

**Location of Modules:**

Modules are placed in directories or .jar files that are part of the module path.
The module path is specified using the --module-path option when running or compiling Java applications.

**Module Discovery:**

When a module is required, the Java runtime searches the specified module path for a module-info.class file in the compiled .jar or directory.
This file declares the name of the module and its dependencies.

**Module Resolution:**

The Java runtime or compiler resolves the module graph based on:
- Direct dependencies declared using requires in module-info.java.
- Transitive dependencies declared using requires transitive.
- If any required module is missing or there is a cyclic dependency, the application fails to run.
Loading Modules:

Once resolved, the runtime loads the bytecode from the modules' module-info.class and other .class files.

![image](https://github.com/user-attachments/assets/61ebbe78-ce5a-427c-925e-6d0caf973eb4)


**System Modules:**

The Java runtime includes several built-in modules, such as java.base, java.sql, and java.desktop.
These are located in the JDK's module repository ($JAVA_HOME/lib/modules).

**Custom Modules:**

Developers provide modules via the --module-path.
```bash
# compiling
javac --module-path custom_modules -d output_dir src/com.example.module/module-info.java src/com.example.module/Main.java

# running
java --module-path custom_modules:other_modules --module com.example.module/com.example.module.Main
```

## I/O

### Working with Files

In Java, the File class (part of the java.io package) represents a file or directory path in an abstract manner. It provides methods to create, delete, and inspect file properties but does not directly handle file content (e.g., reading or writing). The File object represents the path to a file or directory, not the actual content. It can refer to a file or directory that may or may not exist.

#### Commonly Used Constructors:
- File(String pathname): Creates a File object using a specified path.<br>
- File(String parent, String child): Constructs a File object from parent and child pathnames.<br>
- File(File parent, String child): Uses a File object as the parent and a string for the child.<br>

#### Key Methods:
Existence:
exists(): Checks if the file or directory exists.

Attributes:
- isFile(): Checks if it’s a file.
- isDirectory(): Checks if it’s a directory.
- length(): Returns the file size in bytes.

Operations:
- createNewFile(): Creates a new file.
- mkdir(): Creates a new directory.
- mkdirs(): Creates directory along with any necessary but nonexistent parent directories.
- delete(): Deletes the file or directory.

Path Information:
- getName(): Returns the name of the file/directory.
- getAbsolutePath(): Returns the absolute pathname.
- getParent(): Returns the parent directory.

Listing Contents:
- list(): Returns an array of filenames in a directory.
- listFiles(): Returns an array of File objects in a directory.

Usage Example:

```java
import java.io.File;
import java.io.IOException;

public class FileExample {
    public static void main(String[] args) {
        try {
            // Creating a File object
            File file = new File("example.txt");

            // Check if the file exists
            if (!file.exists()) {
                // Create a new file
                file.createNewFile();
                System.out.println("File created: " + file.getName());
            } else {
                System.out.println("File already exists.");
            }

            // Display file properties
            System.out.println("Absolute Path: " + file.getAbsolutePath());
            System.out.println("Is File: " + file.isFile());
            System.out.println("File Size: " + file.length() + " bytes");
        } catch (IOException e) {
            System.out.println("An error occurred: " + e.getMessage());
        }
    }
}
```

Notes
- The File class only deals with metadata and path operations.
- For reading and writing content, use other classes like FileReader, FileWriter, BufferedReader, BufferedWriter, or newer APIs like Files in java.nio.file.

#### Key Differences between Absolute vs Canonical path
Aspect	        Absolute Path	            Canonical Path
======          ==============              ==============
Symbolic Links	Not resolved	            Resolved
Redundancy	    May contain . or ..	        No . or .., completely resolved
Uniqueness	    May not be unique	        Always unique for the same file/directory
Performance	    Generally faster	        Slightly slower (resolves links)

### Features of Path Class
Abstraction:
- Represents the path to a file or directory, not the file or directory itself.
- Works with both absolute and relative paths.
- Provides powerful methods for path manipulation, path resolution, and file system operations.

```java
import java.nio.file.Path;
import java.nio.file.Paths;
import java.io.IOException;

public class PathExample {
    public static void main(String[] args) {
        // Create a Path object
        Path path = Paths.get("/home/user/docs/file.txt");

        // Path Information
        System.out.println("File Name: " + path.getFileName());
        System.out.println("Parent Path: " + path.getParent());
        System.out.println("Root: " + path.getRoot());

        // Convert to Absolute Path
        System.out.println("Absolute Path: " + path.toAbsolutePath());

        // Normalize the Path
        Path pathWithRedundancy = Paths.get("/home/user/../docs/./file.txt");
        System.out.println("Normalized Path: " + pathWithRedundancy.normalize());

        // Resolve a Subpath
        Path resolvedPath = path.resolve("subfolder/subfile.txt");
        System.out.println("Resolved Path: " + resolvedPath);

        // Relativize Paths
        Path basePath = Paths.get("/home/user");
        Path otherPath = Paths.get("/home/user/docs/file.txt");
        Path relativePath = basePath.relativize(otherPath);
        System.out.println("Relative Path: " + relativePath);

        // Convert to Real Path
        try {
            System.out.println("Canonical Path: " + path.toRealPath());
        } catch (IOException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```
Output
```bash
File Name: file.txt
Parent Path: /home/user/docs
Root: /
Absolute Path: /home/user/docs/file.txt
Normalized Path: /home/docs/file.txt
Resolved Path: /home/user/docs/file.txt/subfolder/subfile.txt
Relative Path: docs/file.txt
Canonical Path: /home/user/docs/file.txt
```

### Reader class
The Reader class in Java is an abstract class in the java.io package. It provides a foundation for reading character streams, as opposed to byte streams (which are handled by classes like InputStream).

Concrete subclasses include FileReader, BufferedReader, StringReader, etc.

**Common Subclasses**
- FileReader: Reads character streams from a file.
- BufferedReader: Reads text efficiently using a buffer, and provides additional methods like readLine() for line-by-line reading.
- InputStreamReader: Bridges byte streams and character streams, allowing you to convert bytes into characters.
- StringReader: Reads characters from a string as a stream.

Code Example: Using FileReader and BufferedReader
```java
import java.io.*;

public class ReaderExample {
    public static void main(String[] args) {
        try {
            // Create a FileReader
            FileReader fileReader = new FileReader("example.txt");

            // Wrap it in a BufferedReader for efficiency
            BufferedReader bufferedReader = new BufferedReader(fileReader);

            // Read and print the file content line by line
            String line;
            while ((line = bufferedReader.readLine()) != null) {
                System.out.println(line);
            }

            // Close the reader
            bufferedReader.close();
        } catch (IOException e) {
            System.out.println("An error occurred: " + e.getMessage());
        }
    }
}
```

#### FileWriter and BufferedWriter
- FileWriter: Used to write characters to a file.
- BufferedWriter: Wraps the FileWriter to provide buffering, which improves performance when writing large amounts of text.
- 
```java
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

public class WriteToFileExample {
    public static void main(String[] args) {
        // File path
        String filePath = "example.txt";

        try {
            // Create FileWriter and wrap it with BufferedWriter for efficiency
            FileWriter fileWriter = new FileWriter(filePath, true); // 'true' enables appending mode
            BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);

            // Write data to the file
            bufferedWriter.write("Hello, World!");
            bufferedWriter.newLine(); // Add a newline
            bufferedWriter.write("Welcome to Java file writing.");

            // Close the writer to release resources
            bufferedWriter.close();

            System.out.println("Data written to file successfully.");
        } catch (IOException e) {
            System.out.println("An error occurred while writing to the file: " + e.getMessage());
        }
    }
}
```
