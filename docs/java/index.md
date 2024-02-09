---
title: Java
hide:
  - tags

tags:
- Java
---


# Java


---

Java is a general-purpose, class-based, object-oriented programming language designed for having lesser implementation dependencies. It is a computing platform for application development. Java is fast, secure, and reliable, therefore. It is widely used for developing Java applications in laptops, data centers, game consoles, scientific supercomputers, cell phones, etc.

---

## Java Features

Here are some important Java features:

- It is one of the easy-to-use programming languages to learn.
- Write code once and run it on almost any computing platform.
- Java is platform-independent. Some programs developed in one machine can be executed in another machine.
- It is designed for building object-oriented applications.
- It is a multithreaded language with automatic memory management.
- It is created for the distributed environment of the Internet.
- Facilitates distributed computing as its network-centric.

---

## Components Of Java

A Java Programmer writes a program in a human-readable language called Source Code. Therefore, the CPU or Chips never understand the source code written in any programming language.

###  Java Development kit (JDK)

JDK is a software development environment used for making applets and Java applications. The full form of JDK is Java Development Kit. Java developers can use it on Windows, macOS, Solaris, and Linux. JDK helps them to code and run Java programs. It is possible to install more than one JDK version on the same computer.

**Why use JDK?**

Here are the main reasons for using JDK:


JDK contains tools required to write Java programs and JRE to execute them.
It includes a compiler, Java application launcher, Appletviewer, etc.
Compiler converts code written in Java into byte code.
Java application launcher opens a JRE, loads the necessary class, and executes its main method.

###  Java Virtual Machine (JVM)
Java Virtual Machine (JVM) is an engine that provides a runtime environment to drive the Java Code or applications. It converts Java bytecode into machine language. JVM is a part of the Java Run Environment (JRE). In other programming languages, the compiler produces machine code for a particular system. However, the Java compiler produces code for a Virtual Machine known as Java Virtual Machine.

**Why JVM?**

Here are the important reasons of using JVM:

JVM provides a platform-independent way of executing Java source code.
It has numerous libraries, tools, and frameworks.
Once you run a Java program, you can run on any platform and save lots of time.
JVM comes with JIT (Just-in-Time) compiler that converts Java source code into low-level machine language. Hence, it runs faster than a regular application.

###  Java Runtime Environment (JRE)
JRE is a piece of software that is designed to run other software. It contains the class libraries, loader class, and JVM. In simple terms, if you want to run a Java program, you need JRE. If you are not a programmer, you don’t need to install JDK, but just JRE to run Java programs.

**Why use JRE?**

Here are the main reasons of using JRE:

JRE contains class libraries, JVM, and other supporting files. It does not include any tool for Java development like a debugger, compiler, etc.
It uses important package classes like math, swing, util, lang, awt, and runtime libraries.
If you have to run Java applets, then JRE must be installed in your system.

---



## Java performance troubleshooting

Java performance troubleshooting is the process of identifying and resolving performance issues in Java applications. Here are a few steps that can be taken to troubleshoot performance issues in Java:

### Profiling

Use a profiler to identify performance bottlenecks in the application. Profilers can provide detailed information about the performance of the application, including information about CPU usage, memory usage, and thread activity. Popular profilers for Java include VisualVM, JProfiler, and YourKit.

### Logging

Add logging statements to the application to track the flow of execution. This can help identify where the application is spending most of its time and can help identify the source of performance issues.

### Monitoring

Use monitoring tools to track the performance of the application in production. These tools can provide information about resource usage, response times, and errors. Popular monitoring tools for Java include JMX, JConsole, and JavaMelody.

### Thread dump

Thread dump is a snapshot of all threads that are running in a java process. Thread dump can be captured using jstack command in linux or jcmd command in windows. Thread dump analysis can help to identify the blocked threads, deadlock, resource contention and more.

### Memory dump

Memory dump is a snapshot of the heap memory of a java process. Memory dump can be captured using jmap command in linux or jcmd command in windows. Memory dump analysis can help to identify memory leaks, object retention, and more.

### Code review

Review the application's code to identify any potential performance issues. Look for common performance anti-patterns such as poor caching strategy, unnecessary object creation, and inefficient algorithms.

### Testing

Test the application under different load conditions to identify performance issues that may not be visible in normal usage. Use load testing tools like Apache JMeter or Gatling to simulate different levels of traffic and usage patterns. This can help identify bottlenecks and scalability issues that may not be visible during normal usage.

### Configuration review

Review the application's configuration to ensure that it is optimized for performance. This includes reviewing settings such as JVM heap size, GC settings, thread pool sizes, and connection pool sizes.

### Data Analysis

Look for patterns in your data that could be causing performance issues. Use SQL profiler to identify slow queries and indexes that could be improved. Analyze the data to identify any data issues that could be impacting performance.

### Network

Network issues can also cause performance problems. Check for network bottlenecks, dropped packets, and other network-related problems.

It's important to note that performance troubleshooting can be a complex process, and it may be necessary to use multiple techniques to fully identify and resolve a performance issue. It's also important to have a clear understanding of the requirements of the application, as well as the expected usage patterns, to effectively troubleshoot performance issues.


---




## Exceptions

Exception is an error event that can happen during the execution of a program and disrupts its normal flow.

Types of Java Exceptions

###  Checked Exception
The classes which directly inherit Throwable class except RuntimeException and Error are known as checked exceptions e.g. IOException, SQLException etc. Checked exceptions are checked at compile-time.

###  Unchecked Exception
The classes which inherit RuntimeException are known as unchecked exceptions e.g. ArithmeticException, NullPointerException, ArrayIndexOutOfBoundsException etc. Unchecked exceptions are not checked at compile-time, but they are checked at runtime.

###  Error
Error is irrecoverable e.g. OutOfMemoryError, VirtualMachineError, AssertionError etc.


###  Hierarchy of Java Exception classes


<img src="java/images/Exceptions.png" width="900"  />

###  Error vs Exception

|BASIS FOR COMPARISON	|ERROR                                    |EXCEPTION                               |
|-----------------------|-----------------------------------------|----------------------------------------|
|Basic	               |An error is caused due to lack of system resources.|An exception is caused because of the code.|
|Recovery	            |An error is irrecoverable.	            |An exception is recoverable.|
|Keywords	            |There is no means to handle an error by the program code.|	Exceptions are handled using three keywords "try", "catch", and "throw".|
|Consequences           |As the error is detected the program will terminated abnormally.|As an exception is detected, it is thrown and caught by the "throw" and "catch" keywords correspondingly.|
|Types	               |Errors are classified as unchecked type.|Exceptions are classified as checked or unchecked type.|
|Package	               |In Java, errors are defined "java.lang.Error" package.|In Java, an exceptions are defined in"java.lang.Exception".|
|Example	               |OutOfMemory, StackOverFlow.|Checked Exceptions: NoSuchMethod, ClassNotFound.Unchecked Exceptions: NullPointer, IndexOutOfBounds.|


### Custom exception

we can create our own exceptions that are derived classes of the Exception class. Creating our own Exception is known as custom exception or user-defined exception.

**Why we need for custom exceptions?**

- To catch and provide specific treatment to a subset of existing Java exceptions.
- `Business logic exceptions`: These are the exceptions related to business logic and workflow. It is useful for the application users or the developers to understand the exact problem.

---

###  Exception Propagation

An exception is first thrown from the top of the stack and if it is not caught, it drops down the call stack to the previous method, If not caught there, the exception again drops down to the previous method, and so on until they are caught or until they reach the very bottom of the call stack. This is called exception propagation.

```java
class TestExceptionPropagation {

  void m() {  
    int data = 50/0;  
  }  
  void n() {  
    m();  
  }  
  void p() {  
      try {  
         n();  
      } catch(Exception e) { 
         System.out.println("exception handled");
      }  
  }  
  public static void main(String args[]) {  
   TestExceptionPropagation obj = new TestExceptionPropagation();  
   obj.p();  
   System.out.println("Normal Flow...");  
  }  
}  
```

---

## Classloader

The Java ClassLoader is a part of the Java Runtime Environment that dynamically loads Java classes into the Java Virtual Machine. Java code is compiled into class file by javac compiler and JVM executes Java program, by executing byte codes written in class file. ClassLoader is responsible for loading class files from file system, network or any other source.

Types of ClassLoader

###  Bootstrap Class Loader
It loads standard JDK class files from rt.jar and other core classes. It loads class files from jre/lib/rt.jar. For example, java.lang package class.

###  Extensions Class Loader
It loads classes from the JDK extensions directly usually JAVA_HOME/lib/ext directory or any other directory as java.ext.dirs.

###  System Class Loader
It loads application specific classes from the CLASSPATH environment variable. It can be set while invoking program using -cp or classpath command line options.

---

## Types of memory areas are allocated by JVM

JVM is a program which takes Java bytecode and converts the byte code (line by line) into machine understandable code. JVM perform some particular types of operations:

Loading of code
Verification of code
Executing the code
It provide run-time environment to the users
Types of Memory areas allocated by the JVM:

1. **Classloader**: Classloader is a subsystem of JVM that is used to load class files.
2. **Class(Method) Area**: Class(Method) Area stores per-class structures such as the runtime constant pool, field and method data, the code for methods.
3. **Heap**: It is the runtime data area in which objects are allocated.
4. **Stack**: Java Stack stores frames.It holds local variables and partial results, and plays a part in method invocation and return. Each thread has a private JVM stack, created at the same time as thread.
5. **Program Counter Register**: PC (program counter) register. It contains the address of the Java virtual machine instruction currently being executed.
6. **Native Method Stack**: It contains all the native methods used in the application.


---

## Java Reflection API

Java Reflection is the process of analyzing and modifying all the capabilities of a class at runtime. Reflection API in Java is used to manipulate class and its members which include fields, methods, constructor, etc. at runtime. The **java.lang.Class** class provides many methods that can be used to get metadata, examine and change the run time behavior of a class.

There are 3 ways to get the instance of Class class. They are as follows:

* forName() method of Class class
* getClass() method of Object class
* the .class syntax

**1. forName() method of Class class**

* is used to load the class dynamically.
* returns the instance of Class class.
* It should be used if you know the fully qualified name of class.This cannot be used for primitive types.

```java
class Simple{}  
  
class Test {  
   public static void main(String args[]) {  
      Class c = Class.forName("Simple");  
      System.out.println(c.getName());  
   }  
}  
```

Output

```
Simple
```

**2. getClass() method of Object class**

It returns the instance of Class class. It should be used if you know the type. Moreover, it can be used with primitives.

```java
class Simple{}  
  
class Test {  
  void printName(Object obj) {  
    Class c=obj.getClass();    
    System.out.println(c.getName());  
  }  
  public static void main(String args[]) {  
    Simple s=new Simple();  
    Test t=new Test();  
    t.printName(s);  
  }  
}  
```

Output
```
Simple
```
**3. The .class syntax**

If a type is available but there is no instance then it is possible to obtain a Class by appending ".class" to the name of the type.It can be used for primitive data type also.

```java
class Test {  
  public static void main(String args[]) {  
   Class c = boolean.class;   
   System.out.println(c.getName());  
  
   Class c2 = Test.class;   
   System.out.println(c2.getName());  
 }  
}  
```

Output

```
boolean
Test
```


---

## Misc Questions

###  Can you declare the main method as final?

Yes. We can declare main method as final. But, In inheritance concept we cannot declare main method as final in parent class. It give compile time error. The main method has to be public because it has to be called by JVM which is outside the scope of the package and hence would need the access specifier-public.

```java
public class Test {
	public final static void main(String[] args) throws Exception {
		System.out.println("This is Test Class");
	}
}
 
class Child extends Test {
	public static void main(String[] args) throws Exception {
		System.out.println("This is Child Class");
	}
}
```

Output
```
Cannot override the final method from Test.
```

###  What is the difference between abstract class and interface?

Abstract class and interface both are used to achieve abstraction where we can declare the abstract methods. Abstract class and interface both can't be instantiated.

|Sl.No|Abstract Class	            |Interface                        |
|-----|-----------------------------|---------------------------------|
| 01. |Abstract class can have abstract and non-abstract methods.|	Interface can have only abstract methods. Since Java 8, it can have default and static methods also.|
| 02. |Abstract class doesn't support multiple inheritance.|	Interface supports multiple inheritance.|
| 03. |Abstract class can have final, non-final, static and non-static variables.	|Interface has only static and final variables.|
| 04. |Abstract class can provide the implementation of interface.|Interface can't provide the implementation of abstract class.|
| 05. |The abstract keyword is used to declare abstract class.|The interface keyword is used to declare interface.|
| 06. |An abstract class can extend another Java class and implement multiple Java interfaces.|An interface can extend another Java interface only.|
| 07. |An abstract class can be extended using keyword "extends".|An interface can be implemented using keyword "implements".|
| 08. |A Java abstract class can have class members like private, protected, etc.|Members of a Java interface are public by default.|


###  What are Wrapper classes?

The wrapper class in Java provides the mechanism to convert primitive into object and object into primitive.

**Use of Wrapper classes in Java**

* **Change the value in Method**: Java supports only call by value. So, if we pass a primitive value, it will not change the original value. But, if we convert the primitive value in an object, it will change the original value.
* **Serialization**: We need to convert the objects into streams to perform the serialization. If we have a primitive value, we can convert it in objects through the wrapper classes.
* **Synchronization**: Java synchronization works with objects in Multithreading.
* **java.util package**: The java.util package provides the utility classes to deal with objects.
* **Collection Framework**: Java collection framework works with objects only. All classes of the collection framework (ArrayList, LinkedList, Vector, HashSet, LinkedHashSet, TreeSet, PriorityQueue, ArrayDeque, etc.) deal with objects only.

| Sl.No|Primitive Type  |	Wrapper class       |
|------|----------------|----------------------|
| 01.  |boolean	      |Boolean|
| 02.  |char	         |Character|
| 03.  |byte	         |Byte|
| 04.  |short	         |Short|
| 05.  |int	            |Integer|
| 06.  |long	         |Long|
| 07.  |float	         |Float|
| 08.  |double	         |Double|

Example: Primitive to Wrapper

```java
//Java program to convert primitive into objects  
//Autoboxing example of int to Integer  
class WrapperExample {  
  public static void main(String args[]){  
      //Converting int into Integer  
      int a=20;  
      Integer i = Integer.valueOf(a);//converting int into Integer explicitly  
      Integer j = a; //autoboxing, now compiler will write Integer.valueOf(a) internally  
  
   System.out.println(a+" "+i+" "+j);  
  }
}  
```
Output
```
20 20 20
```


###  What are the restrictions that are applied to the Java static methods? 
If a method is declared as static, it is a member of a class rather than belonging to the object of the class. It can be called without creating an object of the class. A static method also has the power to access static data members of the class.

* There are a few restrictions imposed on a static method
* The static method cannot use non-static data member or invoke non-static method directly.
* The `this` and `super` cannot be used in static context.
* The static method can access only static type data (static type instance variable).
* There is no need to create an object of the class to invoke the static method.
* A static method cannot be overridden in a subclass

```java
class Parent {
   static void display() {
      System.out.println("Super class");    
   }
}
public class Example extends Parent {
   void display()  // trying to override display() {
      System.out.println("Sub class");  
   }
   public static void main(String[] args) {
      Parent obj = new Example();
      obj.display();
   }
}
```
This generates a compile time error. The output is as follows −

```
Example.java:10: error: display() in Example cannot override display() in Parent
void display()  // trying to override display()
     ^
overridden method is static

1 error
```


###  What is the difference between Serializable and Externalizable interface?

|Sl.No |SERIALIZABLE |	EXTERNALIZABLE        |
|----|----------------|-----------------------|
| 01.|Serializable is a marker interface i.e. does not contain any method.|	Externalizable interface contains two methods writeExternal() and readExternal() which implementing classes MUST override.|
| 02.|Serializable interface pass the responsibility of serialization to JVM and it’s default algorithm.|	Externalizable provides control of serialization logic to programmer – to write custom logic.|
| 03.|Mostly, default serialization is easy to implement, but has higher performance cost.|Serialization done using Externalizable, add more responsibility to programmer but often result in better performance.|
| 04.|It’s hard to analyze and modify class structure because any change may break the serialization.|	It’s more easy to analyze and modify class structure because of complete control over serialization logic.|
| 05.|Default serialization does not call any class constructor.|A public no-arg constructor is required while using Externalizable interface. |



###  What are the ways to instantiate the Class class? 

####  1. Using new keyword 

```java
MyObject object = new MyObject();
```

####  2. Using Class.forName() 

```java
MyObject object = (MyObject) Class.forName("subin.rnd.MyObject").newInstance();
```

####  3. Using clone() 

```java
MyObject anotherObject = new MyObject();
MyObject object = (MyObject) anotherObject.clone();
```

####  4. Using object deserialization 

```java
ObjectInputStream inStream = new ObjectInputStream(anInputStream );
MyObject object = (MyObject) inStream.readObject();
```



###  What is the difference between creating String as new() and literal?
When you create String object using `new()` operator, it always create a new object in heap memory. On the other hand, if you create object using String literal syntax e.g. "Java", it may return an existing object from String pool (a cache of String object in Perm gen space, which is now moved to heap space in recent Java release), if it's already exists. Otherwise it will create a new string object and put in string pool for future re-use.

```java
String a = "abc"; 
String b = "abc";
System.out.println(a == b);  // true

String c = new String("abc");
String d = new String("abc");
System.out.println(c == d);  // false
```


###  What is difference between String, StringBuffer and StringBuilder?

####  Mutability Difference
`String` is **immutable**, if you try to alter their values, another object gets created, whereas `StringBuffer` and `StringBuilder` are **mutable** so they can change their values.

####  Thread-Safety Difference
The difference between `StringBuffer` and `StringBuilder` is that StringBuffer is thread-safe. So when the application needs to be run only in a single thread then it is better to use StringBuilder. StringBuilder is more efficient than StringBuffer.

Example: StringBuffer

```java
public class BufferTest{  
   public static void main(String[] args){  
        StringBuffer buffer=new StringBuffer("Hello");  
        buffer.append(" World");  
        System.out.println(buffer);  
   }  
}  
```

Example: StringBuilder

```java
public class BuilderTest{  
    public static void main(String[] args){  
        StringBuilder builder=new StringBuilder("Hello");  
        builder.append(" World");  
        System.out.println(builder);  
    }  
}  
```




## For more information

1. [Java, J2EE, JSP, Servlet, Hibernate Interview Questions](https://github.com/learning-zone/java-interview-questions)

