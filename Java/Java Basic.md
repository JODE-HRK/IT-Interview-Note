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

    String and Integer rewrite the equals function to make it only compare the value.

    If there is no rewriting, equals is the same as "==" [Default]

- **What is java serialization? How to implement it? What is the serialization effect?**

  Serialization in Java is a mechanism of writing the state of an object  into a byte stream or from a byte stream restore to an object.

  
  
  To implement serialization, use the **java.io.Serializable** interface. 
  
   1. The **ObjectOutputStream** class contains **writeObject()** method for serializing an Object. 
  
      ```java
      public final void writeObject(Object obj) throws IOException
      ```
  
   2. The **ObjectInputStream** class contains **readObject()** method for deserializing an object. 
  
      ```java
      public final Object readObject() throws IOException, ClassNotFoundException
      ```
  
  Example:
  
  ```java
  FileOutputStream file = new FileOutputStream(filename);
  ObjectOutputStream out = new ObjectOutputStream(file);
  // Method for serialization of object
  out.writeObject(object);
  
  FileInputStream file = new FileInputStream(filename);
  ObjectInputStream in = new ObjectInputStream(file);
  // Method for deserialization of object
  object1 = (Demo)in.readObject();
  ```

- **Hashcode** Effect

  There are two kind of Set in Java.

  1. **List**	Oderly and repeatable
  2. **Set**	Disorder and unrepeatable

  Hashcode function returns the hash value of storage address. In this way, to divide Set storage into several part. Every object can get a hashcode. Divide the hash code to different group.

  Every time add a new value, use hashcode to locate an area. If the position is Null. Then put the new element.

  Two object has same hashcode doesn't mean the two objects equal.

  ```java
  String str1 = "keep";
  String str2 = "brother";
  System. out. println(String. format("str1：%d | str2：%d",  str1. hashCode(),str2. hashCode()));
  System. out. println(str1. equals(str2));
  
  Results:
  str1：1179395 | str2：1179395
  false
  ```

- **Generic**

  Generic type: Generic concept, when executing can be ruled specifically. 
  ArrayList is a generic class. Any type can be stored in ArrayList. Such as Interger, String....

  Using Generic class can reduce code complexity. We no need to define different set because of different element type. One Set is enough to store all types.


## Data 

Java has 8 data types, include:

- Six number types: **byte, short, int, long, float, double**
- One char type: **char**
- One boolean type: **boolean**

### Byte

8 bits, signed, 2's complement interger.
[-128 (-2^7), 127 (2^7 - 1)], default 0

### Short

16 bits, signed, 2's complement interger.
[-32768 (-2^15), 32767 (2^15 - 1)], default 0

### Int

32 bits, signed, 2's complement interger.
[-2147483648 (-2^31), 2147483647 (2^31- 1)], default 0
**Integer variables default to int type**

### Long

64 bits, signed, 2's complement interger.
[-2^63,  2^63- 1], default 0L

### Float

The float data type is single precision, 32 bits
Default 0.0f

### Double

The double data type is double-precision, 64-bit
Default 0.0d

### Char

The char type is a single 16-bit Unicode character
min = \u0000 (0), max = \uffff (65535)

### Boolean

One bit, true and false, default false

=======================================================================================

Java has three kinds of reference data type: Class, Interface and Array

Difference between basic data type and reference data type:

​	In terms of

1. Concept:

   In basic data type: Variable names point to specific values.

   In reference data type: Variable names point to the memory address (hash code) where the data is stored.

2. Memory construction:

   When creating basic data type, there will be a certain amount of memory that save data value in the stack memory.

   When creating reference data type,  a space will be allocated in the stack memory, and then a specific space will be allocated in the heap memory to store the specific information of the data, that is, the hash value, and then the reference in the stack will point to the object address in the heap.

3. Use:

   To judge basic data value, using == and !=.

   To judge reference data type, using equals function.

### Four kinds of reference:

1. Strong References: 

   This is the **default** type/class of Reference Object. **Any object which has an active strong reference are not eligible for garbage collection.** The object is garbage collected only when the variable which was strongly referenced points to null.

   ```java
   MyClass obj = new MyClass ();  // Here is the Strong References. obj is not eligible for garbage collection now.
   obj = null; //'obj' object is no longer referencing to the instance. So the 'MyClass type object is now available for garbage collection.   
   ```

2. Weak References:

   Weak Reference Objects are not the default type/class of Reference Object and they should be explicitly specified while using them.

   - This type of reference is used in WeakHashMap to reference the entry objects.
   - If JVM detects an object with only weak references (i.e. no strong or soft references linked to any object object), this object will be marked for garbage collection.
   - To create such references [java.lang.ref.WeakReference](https://docs.oracle.com/javase/7/docs/api/java/lang/ref/WeakReference.html) class is used.
   - These references are used in real time applications while establishing a DBConnection which might be cleaned up by Garbage Collector when the application using the database gets closed.

   **As long as the JVM garbage collector finds it, it will be recycled.**

   ```java
   //Java Code to illustrate Weak reference
   import java.lang.ref.WeakReference;
   class Gfg
   {
   	public void x()
   	{
   		System.out.println("GeeksforGeeks");
   	}
   }
   public class Example
   {
   	public static void main(String[] args)
   	{
   		// Strong Reference
   		Gfg g = new Gfg();	
   		g.x();
   		// Creating Weak Reference to Gfg-type object to which 'g'
   		// is also pointing.
   		WeakReference<Gfg> weakref = new WeakReference<Gfg>(g);
   		//Now, Gfg-type object to which 'g' was pointing earlier
   		//is available for garbage collection.
   		//But, it will be garbage collected only when JVM needs memory.
   		g = null;
   		// You can retrieve back the object which
   		// has been weakly referenced.
   		// It successfully calls the method.
   		g = weakref.get();
   		g.x();
   	}
   }
   ```

3. Soft Reference:

   In Soft reference, even if the object is free for garbage collection then also its not garbage collected, until JVM is in need of memory badly. The objects gets cleared from the memory when JVM runs out of memory. To create such references [java.lang.ref.SoftReference](https://docs.oracle.com/javase/7/docs/api/java/lang/ref/SoftReference.html)

   **When the program runs out of memory, it will be recycled.**

   Example is same as Weak Reference.

4. Phantom Reference:

   he objects which are being referenced by phantom references are eligible for garbage collection. But, before removing them from the memory, JVM puts them in a queue called ‘reference queue’ . They are put in a reference queue after calling finalize() method on them. To create such references [java.lang.ref.PhantomReference](https://docs.oracle.com/javase/7/docs/api/java/lang/ref/PhantomReference.html) class is used.

   **The recycling mechanism of phantom references is similar to that of weak references, but before it is recycled, it will be put into ReferenceQueue. Note that other references are passed into the *ReferenceQueue* after being recycled by the JVM.**
   
   ```java
   import java.lang.ref.*;
   class Gfg
   {
   	public void x()
   	{
   		System.out.println("GeeksforGeeks");
   	}
   }
   public class Example
   {
   	public static void main(String[] args)
   	{
   		//Strong Reference
   		Gfg g = new Gfg();	
   		g.x();
   		//Creating reference queue
   		ReferenceQueue<Gfg> refQueue = new ReferenceQueue<Gfg>();
   		//Creating Phantom Reference to Gfg-type object to which 'g'
   		//is also pointing.
   		PhantomReference<Gfg> phantomRef = null;
   		phantomRef = new PhantomReference<Gfg>(g,refQueue);
   		//Now, Gfg-type object to which 'g' was pointing
   		//earlier is available for garbage collection.
   		//But, this object is kept in 'refQueue' before
   		//removing it from the memory.
   		g = null;
   		//It always returns null.
   		g = phantomRef.get();
   		//It shows NullPointerException.
   		g.x();
   	}
   }
   ```

### Autoboxing and Unboxing

Boxing: Wrap primitive types with their corresponding reference types;
Unboxing: converting a wrapper type to a primitive data type;

Why use this?
To make the basic type also has the characteristics of the object.

1. Converting a primitive value (an `int`, for example) into an object of the corresponding wrapper class (`Integer`) is called autoboxing. The Java compiler applies autoboxing when a primitive value is:

- Passed as a parameter to a method that expects an object of the corresponding wrapper class.
- Assigned to a variable of the corresponding wrapper class.

2. Converting an object of a wrapper type (`Integer`) to its corresponding primitive (`int`) value is called unboxing. The Java compiler applies to unbox when an object of a wrapper class is:

- Passed as a parameter to a method that expects a value of the corresponding primitive type.
- Assigned to a variable of the corresponding primitive type.

**Common Interview Questions:**

```java
public class Main {
    public static void main(String[] args) {
        Integer i1 = 100;
        Integer i2 = 100;
        Integer i3 = 200;
        Integer i4 = 200;
        System.out.println(i1==i2);
        System.out.println(i3==i4);
    }
}
Results:
true
false
```

```java
public class Main {
    public static void main(String[] args) {
        Double i1 = 100.0;
        Double i2 = 100.0;
        Double i3 = 200.0;
        Double i4 = 200.0;
        System.out.println(i1==i2);
        System.out.println(i3==i4);
    }
}
Results:
false
false
```

Why?

Source Code:

```java
public static Integer valueOf(int i) {
    if(i >= -128 && i <= IntegerCache.high)
        return IntegerCache.cache[i + 128];
    else
        return new Integer(i);
}
private static class IntegerCache {
    static final int high;
    static final Integer cache[];
    static {
        final int low = -128;
        // high value may be configured by property
        int h = 127;
        if (integerCacheHighPropValue != null) {
            // Use Long.decode here to avoid invoking methods that
            // require Integer's autoboxing cache to be initialized
            int i = Long.decode(integerCacheHighPropValue).intValue();
            i = Math.max(i, 127);
            // Maximum array size is Integer.MAX_VALUE
            h = Math.min(i, Integer.MAX_VALUE - -low);
        }
        high = h;
        cache = new Integer[(high - low) + 1];
        int j = low;
        for(int k = 0; k < cache.length; k++)
            cache[k] = new Integer(j++);
    }
    private IntegerCache() {}
}
```

i2 and i1 value is 100, so they will fetch the object reference which has been created in IntegerCache.cache. if Value is [-128, 127], the function will work as that.

However, the double and float is unlimited. So it can't be like this.

### The Difference between a = a + b and a += b

The += operator performs implicit automatic type conversion.

```java
byte a = 127;
byte b = 127;
b = a + b; // Report compilation error: cannot convert from int to byte
b += a; 
```

```java
short s1= 1;
s1 = s1 + 1; // Error, default 1 is integer
s1 += 1; //correct
```

### What if int transfer into byte?

The high 8 bits will be lost.

## Java Common Keywords

### The difference between *public*, *private*, *protected*, and not written (*default*) 

- **default:** Accessible within the same package.
- **private:** Accessible within the same class.
- **public:** Accessible within all classes.
- **protected:** Accessible to classes and all subclasses in the same package

### Final

- **Function:** 
  - **Decorate classes:** The class cannot be inherited.
  - **Decorate class attributes:** The variables can only be assigned once and cannot be modified later.
  - **Decorate class methods:** The method cannot be rewritten.
- **Using:** 
  - When decorating reference variables, **reference cannot be changed**, **but the content it points can be changed.**
  - The method decorated by **final**, JVM will try to inline it to improve efficiency.
  - Constants modified by **final** will be stored in the constant pool during compilation.

### static

- **Using:**
  - **Static variables** and **static methods**. That is, variables/methods modified by static **belong to the static resources of the class and are shared by class instances**.
  - **Static block:** initialization operation
  - **Static inner class:** Specifies to import static resources in a class, and does not need to use the class name, you can use the resource name directly. 
- **Meaning:**
  - Specifies to import static resources in a class, and does not need to use the class name, you can use the resource name directly.
  - Create static blocks to optimize program performance. Because static blocks will only be executed once when the class is loaded.
- **Features:**
  - The static variables and methods only are executed once when the class is loaded.
  - The static variables and methods are allocated memory.
  - The static variables or methods have priority over objects.
- **Tips:**
  - **static** only can access **static**
  - **Non-static** can access **non-static** and static.

### This

- **Using:**
  - point to the current object.
  - refer to the class constructor function.
  - Distinguish the same name. (in the function)

### Super

- **Using:**
  - point to the parent.
  - When the member variable or method in the subclass has the same name as the member variable or method in the parent class, use super to distinguish.
  - refer to the parent class constructor function.

**&, &&, break, continue, return**

## Exception Handling

### Introduction

Java Exception is a consistent mechanism for identifying and responding to errors.
Java Exception can keep exception handling code and normal business code seperately