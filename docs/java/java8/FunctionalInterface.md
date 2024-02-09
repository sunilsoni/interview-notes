---
title: Functional Interface
hide:
  - tags

tags:
- Functional Interface
- Predicate
- Consumer
- Function
- Supplier
- UnaryOperator

---

# Functional Interface




Functional interfaces in Java 8 are a foundation for lambda expressions and method references, which allow you to write more concise and readable code. A functional interface is an interface that contains exactly one abstract method, although it may also contain any number of default and static methods. These interfaces are annotated with `@FunctionalInterface`, which is not mandatory but helps in checking at compile-time whether the interface meets the criteria.

### Examples of Functional Interfaces

Here are some built-in functional interfaces in Java 8:

- **`Predicate<T>`**: Takes an argument of type `T` and returns a boolean. Useful for filtering data.
- **`Consumer<T>`**: Accepts an argument of type `T` and returns no result. Useful for performing operations on an object.
- **`Function<T,R>`**: Takes an argument of type `T` and returns a result of type `R`. Useful for transforming data.
- **`Supplier<T>`**: Requires no argument and returns a result of type `T`.
- **`UnaryOperator<T>`**: A specialization of `Function` where both the argument and result are of the same type.

### Practical Examples


### Example of a Functional Interface

Let's create a simple example to illustrate the concept of functional interfaces. We'll start by defining a functional interface called `Calculator`, which has a single abstract method `calculate`:

```java
@FunctionalInterface
interface Calculator {
    int calculate(int a, int b);
}
```

In this example:

- `@FunctionalInterface` annotation is used to indicate that `Calculator` is a functional interface. While this annotation is not strictly required, it helps convey the intent of the interface.

Now, we can use this `Calculator` functional interface to create instances of it using lambda expressions. For instance, we can define two different implementations for addition and subtraction:

```java
public class Main {
    public static void main(String[] args) {
        // Lambda expression for addition
        Calculator addition = (a, b) -> a + b;
        
        // Lambda expression for subtraction
        Calculator subtraction = (a, b) -> a - b;
        
        int result1 = addition.calculate(5, 3);
        int result2 = subtraction.calculate(8, 2);
        
        System.out.println("Result of addition: " + result1);
        System.out.println("Result of subtraction: " + result2);
    }
}
```

In this code:

- We create instances of the `Calculator` functional interface using lambda expressions, providing implementations for the `calculate` method.
- We then use these instances to perform addition and subtraction operations.


#### Using Predicate

```java
Predicate<String> isLongerThan5 = s -> s.length() > 5;
System.out.println(isLongerThan5.test("Hello"));  // Output: false
System.out.println(isLongerThan5.test("Hello, World!"));  // Output: true
```

#### Using Consumer

```java
Consumer<String> print = s -> System.out.println(s);
print.accept("Hello, World!");  // Output: Hello, World!
```

#### Using Function

```java
Function<String, Integer> toLength = s -> s.length();
System.out.println(toLength.apply("Hello"));  // Output: 5
```

#### Using Supplier

```java
Supplier<Double> randomSupplier = () -> Math.random();
System.out.println(randomSupplier.get());  // Output: Random double value
```

#### Using UnaryOperator

```java
UnaryOperator<String> toUpperCase = s -> s.toUpperCase();
System.out.println(toUpperCase.apply("hello"));  // Output: HELLO
```

### Creating Your Own Functional Interface

You can also create your own functional interface. Here's how to create a simple functional interface for a custom operation:

```java
@FunctionalInterface
interface MathOperation {
    int operation(int a, int b);
}

// Using the interface
public class Test {
    public static void main(String[] args) {
        MathOperation addition = (a, b) -> a + b;
        MathOperation subtraction = (a, b) -> a - b;

        System.out.println("10 + 5 = " + addition.operation(10, 5));  // Output: 10 + 5 = 15
        System.out.println("10 - 5 = " + subtraction.operation(10, 5));  // Output: 10 - 5 = 5
    }
}
```

### Advanced Usage of Functional Interfaces

Beyond the basic examples, functional interfaces can be used in more complex scenarios such as combining predicates, chaining functions, or working with streams. These advanced uses further demonstrate the power and flexibility of functional programming in Java 8.

#### Combining Predicates

Java 8 allows you to use methods like `and()`, `or()`, and `negate()` to combine `Predicate` instances in more complex logical expressions:

```java
Predicate<String> startsWithA = s -> s.startsWith("A");
Predicate<String> endsWithX = s -> s.endsWith("x");

Predicate<String> startsWithAAndEndsWithX = startsWithA.and(endsWithX);

System.out.println(startsWithAAndEndsWithX.test("Aardvax"));  // Output: true
System.out.println(startsWithAAndEndsWithX.test("Ajax"));  // Output: true
System.out.println(startsWithAAndEndsWithX.test("Apex"));  // Output: false
```

#### Chaining Functions

The `Function` interface provides methods like `compose()` and `andThen()` that allow you to chain multiple functions together:

```java
Function<Integer, Integer> times2 = e -> e * 2;
Function<Integer, Integer> squared = e -> e * e;

// Applies squared first and then times2
Function<Integer, Integer> squaredThenTimes2 = times2.compose(squared);
System.out.println(squaredThenTimes2.apply(4));  // Output: 32

// Applies times2 first and then squared
Function<Integer, Integer> times2ThenSquared = times2.andThen(squared);
System.out.println(times2ThenSquared.apply(4));  // Output: 64
```

#### Working with Streams

Functional interfaces are integral to working with streams, which are a key feature of Java 8 for processing collections of objects in a functional style:

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "Dave");

names.stream()
    .filter(s -> s.startsWith("A"))
    .map(String::toUpperCase)
    .forEach(System.out::println);  // Output: ALICE
```

In this example, `filter()` uses a `Predicate`, `map()` uses a `Function`, and `forEach()` uses a `Consumer`. This showcases how seamlessly functional interfaces integrate with streams.

#### Custom Functional Interfaces for Complex Scenarios

Sometimes the built-in functional interfaces are not sufficient for your needs. For example, if you need a functional interface that throws a checked exception or accepts more than two parameters, you may need to define your own:

```java
@FunctionalInterface
interface TriFunction<A, B, C, R> {
    R apply(A a, B b, C c);
}

// Using the custom interface
TriFunction<Integer, Integer, Integer, Integer> sum = (a, b, c) -> a + b + c;
System.out.println(sum.apply(1, 2, 3));  // Output: 6
```

This `TriFunction` interface extends the concept of `Function` to three arguments, demonstrating how you can tailor functional interfaces to your specific requirements.



### `java.util.function` Package

While you can create your own functional interfaces as demonstrated earlier, Java 8 introduced a standard set of functional interfaces in the `java.util.function` package. These predefined functional interfaces cover common use cases and make it easier to work with functions in a consistent way.

Here are some of the most commonly used functional interfaces from the `java.util.function` package:

####  **`Function<T, R>`**:
Represents a function that takes an argument of type `T` and returns a result of type `R`. For example, it can be used for mapping operations.

```java
    Function<Integer, String> intToString = (num) -> Integer.toString(num);
```

####  **`Predicate<T>`**:
Represents a function that takes an argument of type `T` and returns a boolean. It is often used for filtering operations.

```java
    Predicate<String> isLong = (str) -> str.length() > 5;
```

####  **`Consumer<T>`**:
Represents a function that takes an argument of type `T` and performs an action, typically with a side-effect.

```java
    Consumer<String> printUpperCase = (str) -> System.out.println(str.toUpperCase());
```

####  **`Supplier<T>`**:
Represents a function that supplies a value of type `T`. It is typically used when you need to generate or provide data.

```java
    Supplier<Double> randomDouble = () -> Math.random();
```

Using these predefined functional interfaces, you can write more expressive and concise code for various functional programming tasks.

### Lambda Expressions and Method References

Lambda expressions are a natural fit for working with functional interfaces. They allow you to define inline implementations of the functional interface's abstract method.

Method references provide another way to use functional interfaces when you want to reference an existing method. There are different types of method references, including:

- **Static Method Reference**: Reference to a static method.

```java
    Function<String, Integer> stringToLength = String::length;
```

- **Instance Method Reference**: Reference to an instance method of a particular object.

```java
    List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
    names.forEach(System.out::println);
```

- **Constructor Reference**: Reference to a constructor.

```java
    Supplier<List<String>> listSupplier = ArrayList::new;
```



Functional interfaces in Java 8 and the associated lambda expressions and method references have revolutionized the way Java developers write code. They bring functional programming concepts into the language, making it more expressive and concise.


### Real-World Use Cases

To further illustrate the significance of functional interfaces and how they are used in real-world scenarios, let's explore a couple of practical examples:

### Example 1: List Filtering

Imagine you have a list of employees, and you want to filter out those who earn more than a certain salary threshold. You can use the `Predicate` functional interface for this task:

```java
List<Employee> employees = // your list of employees
double salaryThreshold = 50000.0;

Predicate<Employee> highEarners = (employee) -> employee.getSalary() > salaryThreshold;
List<Employee> filteredEmployees = employees.stream()
                                           .filter(highEarners)
                                           .collect(Collectors.toList());
```

Here, the `Predicate` functional interface is used to define the condition for filtering. The `filter` method then applies this condition to create a new list of high earners.

### Example 2: Data Transformation

Suppose you have a list of student objects, and you want to transform it into a list of their names. You can use the `Function` functional interface:

```java
List<Student> students = // your list of students

Function<Student, String> nameExtractor = (student) -> student.getName();
List<String> studentNames = students.stream()
                                    .map(nameExtractor)
                                    .collect(Collectors.toList());
```

In this case, the `Function` functional interface is employed to extract the name from each student object and create a list of names.

### Benefit of Functional Interfaces

Functional interfaces provide a level of abstraction that allows you to focus on the "what" (the behavior you want) rather than the "how" (how to implement that behavior). They promote clean, readable, and modular code by encapsulating behavior within functions.

Moreover, functional interfaces, in combination with lambda expressions and method references, enable concise and expressive code. They are particularly useful when working with collections, streams, and various functional programming paradigms.

In your journey as a developer, understanding and using functional interfaces effectively will empower you to write more elegant and maintainable code in Java, harnessing the power of functional programming principles.




