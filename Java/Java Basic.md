# **Java**

## Feature

- **Cross-platform:** Java is cross-platform because the program's source code is compiled into bytecode. Compiled once and then can run on multiple system platforms. (**JVM**)
- **Object-Oriented Programming (OOP):** 
  - Encapsulation: Specify an abstract class to a specific object, and make its attributes private. Meanwhile, provides some methods to access the private attributes.
  - Inheritance: Based on an existing class, establish a new class and add some new data or methods. This class can reuse the parent class method and reduce the overlay code.
  - Polymorphism: It means that there is one reference variable. The concrete type it points to and the method calls this reference variable makes. During the running of the program, it is not determined. The program can distinguish by itself when it running. There are two methods to implement polymorphism. One is inheritance and the other is through the interface.

## Introduction of JDK,  JRE and JVM

- JDK: Java Development Kit. Provides the Java Application Interface (API).
- JRE: Java Runtime Environment (JRE) is **software that Java programs require to run correctly**. It runs on top of the OS and provides the ***class libraries*** and other resources that a specific Java program needs to run.
- JVM: Java Virtual Machine. **It enables a computer to run Java Programs as well as programs written in other languages that are also compiled to Java bytecode.**
- JDBC: Java Database Connectivity. An API for Java defines **how the clients access a database**. Provides **the method to query and update the database**.

## JVM

JVM is a hypothetical computer that can run Java code, including a set of bytecode instructions, a set of registers, a stack, a garbage collector, the heap and a storage method field. 
JVM is based on the Operating System, with no direct interaction with hardware.

JVM can be divided into three parts:

1. **Java Code Execution**
   - Compile code to the class using the javac command
   - Load class files using ClassLoader
   - Execute class:
     - Interpretation: Translate the compiled bytecode line by line into machine code for execution.
     - Compilation: In the unit of the method, the bytecode is translated into machine code at one time and then executed.
       - client compiler
       - server compiler
2. **Memory Management**
   - **Memory Space**
     - **Method Area:** A part of the heap memory which is shared among all threads. It creates when the JVM starts up. To store class structure, superclass name, interface name and constructors.
     - **Heap Area:** Stores the actual objects. It creates when JVM starts up. For each JVM, only one existing heap.
     - **Stack Area:** Generates when a thread creates. The stack memory is allocated per thread. It is used to store data and partial results. It contains references to heap objects.
     - **Native Method Stack:** A stack for native code written in a language other than Java.
     - **PC Registers:** Each thread has a Program Counter 'PC' register associated with it. PC register stores the return address or a native pointer. It also contains the address of the JVM instructions currently being executed.
   - **Memory Allocation**
     - **Heap Allocation:**
     - **TLAB Allocation:**
     - **Stack Allocation:**
   - **Memory Recycle**
     - **Algorithm:**
       - Copy:
       - Mark-Sweep:
       - Mark-Compact:
     - **Sun JDK:**
       - **Generational Collection (GC)**
         - GC available to the young generation
           - Serial Copying
           - Parallel Collection Copying
           - Parallel Copying
         - Trigger Mechanism and Log format of Minor GC
         - GC available to the old generation
           - Serial Mark-Sweep-Compact
           - Parallel Compacting
           - Concurrent Mark-Sweep
         - Trigger Mechanism and Log format of Full GC
       - **GC Parameter**
       - **G1**
   - **Analysis of Memory Condition**
     - jconsole
     - visualvm
     - jstat
     - jmap
     - MAT
3. **Thread Resource Synchronization and Interaction Mechanism**



## Basic

- **What is the keyword of instanceof?**

  *instanceof* can be strictly regarded as a binary operator, to judge whether an object is an instance of a class.

  ```java
  boolean result obj instanceof Class
  ```

  The compiler can check whether obj can transfer to the right class. If can't, an error report directly. If obj is null, return false directly.

- **What is the difference between == and equals?**

  - "==":

    When comparing the basic types: Compare the value.

    When comparing the reference type: Compare the reference.

    ```java
    String x = "string";
    String y = "string";
    String z = new String("string");
    System.out.println(x==y); // true
    System.out.println(x==z); // false
    System.out.println(x.equals(y)); // true
    System.out.println(x.equals(z)); // true
    ```

  - equals:

    ***equals is essentially "=="***

    String and Integer rewrite the equals function to make it compare the value.

    If there is no rewriting, equals is the same as "==" [Default]

- **What is java serialization? How to implement it? What is the serialization effect?**

