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
