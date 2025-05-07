# ☕ Core Java

---

## 📌 Data Types

Java supports two categories:

### 🔹 Primitive Data Types (Predefined)

| Type    | Size              |
|---------|-------------------|
| byte    | 8-bit integer      |
| short   | 16-bit integer     |
| int     | 32-bit integer     |
| long    | 64-bit integer     |
| float   | 32-bit floating-point |
| double  | 64-bit floating-point |
| char    | 16-bit Unicode character |
| boolean | true or false      |

### 🔹 Non-Primitive Data Types (User-defined)

Examples: `String`, `Arrays`, `Classes`, `Interfaces`

---

## 🔤 Literals

Literals represent fixed values assigned to variables.

- **Integer Literals:** `100`, `0xFF`, `0b1010`
- **Floating-point Literals:** `3.14`, `2.5e2`
- **Character Literals:** `'A'`, `'\n'`
- **String Literals:** `"Hello"`
- **Boolean Literals:** `true`, `false`

### Example:

```java
public class HelloWorld {
    public static void main(String[] args) {
        int num1 = 0b101;
        int num2 = 0x7E;
        int num3 = 10_00_00_000;
        float num4 = 56;
        double num5 = 56;
        double num6 = 12e10;
        char c1 = 'a';
        c1++;

        System.out.println(num1);
        System.out.println(num2);
        System.out.println(num3);
        System.out.println(num4);
        System.out.println(num5);
        System.out.println(num6);
        System.out.println(c1);
    }
}
```

---

## 🔁 Type Conversion

Allows assigning a value of one type to another.

- ✅ **Widening (Implicit):** Automatically converts smaller to larger type.  
  Example: `int → long`

- ⚠️ **Narrowing (Explicit):** Manually converts larger to smaller using casting.  
  Example:

```java
int i = (int) 3.14;
```

---

## ➗ Arithmetic Operators

| Operator | Meaning        |
|----------|----------------|
| `+`      | Addition        |
| `-`      | Subtraction     |
| `*`      | Multiplication  |
| `/`      | Division        |
| `%`      | Modulus         |

---

## 🔍 Relational Operators

| Operator | Meaning                  |
|----------|---------------------------|
| `==`     | Equal to                  |
| `!=`     | Not equal                 |
| `>`      | Greater than              |
| `<`      | Less than                 |
| `>=`     | Greater than or equal to  |
| `<=`     | Less than or equal to     |

Example:

```java
if (a > b) {
    // do something
}
```

---

## 🔗 Logical Operators

| Operator | Meaning |
|----------|---------|
| `&&`     | AND     |
| `||`     | OR      |
| `!`      | NOT     |

Example:

```java
if (a > b && b > c) {
    // do something
}
```

---

## 🔀 If-Else Statements

### Basic If-Else:

```java
if (condition) {
    // true block
} else {
    // false block
}
```

### If-Else If:

```java
if (cond1) {
    // ...
} else if (cond2) {
    // ...
} else {
    // ...
}
```

---

## ❓ Ternary Operator

Short-hand if-else:

```java
variable = (condition) ? value1 : value2;
```

Example:

```java
int max = (a > b) ? a : b;
```

---

## 🔄 Switch Statement

```java
switch (expression) {
    case value1:
        // code
        break;
    case value2:
        // code
        break;
    default:
        // code
}
```
✅ Works with: `byte`, `short`, `char`, `int`, `String`, `enum`

---

## 🔃 Loops

### While Loop:

```java
while (condition) {
    // loop body
}
```

### Do-While Loop:

```java
do {
    // loop body
} while (condition);
```

### For Loop:

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

**When to use:**

- `for`: known count
- `while`: unknown count
- `do-while`: run at least once

---

## 🧱 Class & Object Theory

**Class** - Blueprint for creating objects.

Example:

```java
class Car {
    String color;

    void drive() {
        System.out.println("Driving...");
    }
}
```

**Object** - Instance of a class.

---

## 🛠️ Class & Object Practical

```java
class Student {
    String name;
    int age;

    void display() {
        System.out.println(name + " " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();
        s1.name = "Alex";
        s1.age = 21;
        s1.display();
    }
}
```

---

## ☕ JVM, JRE, JDK

| Term | Description |
|------|-------------|
| JDK  | Java Development Kit — tools + JVM |
| JRE  | Java Runtime Environment — libraries + JVM |
| JVM  | Java Virtual Machine — runs bytecode |

---

## 📦 Methods

**Method Syntax:**

```java
returnType methodName(parameters) {
    // code
}
```

**Method Overloading:**

Same method name, different parameters.

```java
class Calculator {
    public int add(int n1, int n2) {
        return n1 + n2;
    }

    public int add(int n1, int n2, int n3) {
        return n1 + n2 + n3;
    }

    public double add(double n1, int n2) {
        return n1 + n2;
    }
}

public class Demo {
    public static void main(String[] args) {
        Calculator obj = new Calculator();
        int r1 = obj.add(3, 4);
        System.out.println(r1);
    }
}
```

---

## 🧠 Stack vs Heap

| Stack | Heap |
|-------|------|
| Stores method calls, local variables | Stores objects, instance data |

Example:

```java
ClassName obj = new ClassName(); // stored in heap
```

---

## 📚 Arrays

**1D Array:**

```java
int[] nums = new int[5];
```

**2D Array:**

```java
int[][] nums = new int[3][4];
```

**Filling a 2D Array with Random Numbers:**

```java
import java.util.Random;

public class Demo {
    public static void main(String[] args) {
        int[][] nums = new int[3][4];
        Random random = new Random();

        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 4; j++) {
                nums[i][j] = random.nextInt(100);
                System.out.print(nums[i][j] + " ");
            }
            System.out.println();
        }

        System.out.println("\nUsing Enhanced For Loop:");
        for (int[] row : nums) {
            for (int val : row) {
                System.out.print(val + " ");
            }
            System.out.println();
        }
    }
}


### Jagged and 3D Array
- **Jagged Array**: An array of arrays where each sub-array can have different lengths.
  
  Example:
  ```java
  int[][] jagged = new int[3][];
  jagged[0] = new int[2];
  jagged[1] = new int[3];
  jagged[2] = new int[1];
  ```

- **3D Array**: An array of arrays of arrays, useful for representing 3D data structures.

---

### Drawbacks of Array
- **Fixed size**: Cannot change the size once declared.
- **Homogeneous data**: Can store only elements of the same data type.
- **Lack of built-in methods** for dynamic operations like insertion or deletion.

---

### Array of Objects
Arrays can store objects, allowing the management of multiple instances efficiently.

Example:
```java
Student[] students = new Student[3];
students[0] = new Student("Alice");
students[1] = new Student("Bob");
students[2] = new Student("Charlie");
```

---

### Enhanced For Loop
Simplifies iteration over arrays or collections.

Syntax:
```java
for (dataType item : array) {
    // use item
}
```

---

### What is String
- A **String** is a sequence of characters. In Java, strings are objects of the `String` class and are immutable.
- **Why "S" of String is capital?**: It’s a class, not a primitive data type.
- In the String constant pool, if the same value exists, it won’t store a new scope; it simply refers to the existing data.
- **String is Immutable** because it cannot be changed directly. Operations like concatenation create new strings.

---

### Mutable vs Immutable String
- **Immutable**: String objects cannot be changed once created. Any modification results in a new object.
- **Mutable**: `StringBuilder` and `StringBuffer` allow modifications without creating new objects.

---

### StringBuffer and StringBuilder
- **StringBuffer**: Thread-safe, synchronized, suitable for multi-threaded environments.
- **StringBuilder**: Not synchronized, faster, suitable for single-threaded environments.

Example:
```java
class Demo {
   public static void main(String[] args) {
       StringBuffer sb = new StringBuffer("Navin");
       sb.append("Reddy");
       System.out.println(sb);
       sb.ensureCapacity(100);
       System.out.println(sb);
   }
}
```

---

### Static Variable
A variable shared among all instances of a class. Declared using the `static` keyword.

Example:
```java
class Mobile {
   String brand;
   int price;
   static String name;

   public void show() {
       System.out.println(brand + " : " + price + " : " + name);
   }
}
public class Demo {
   public static void main(String[] args) {
       Mobile obj1 = new Mobile();
       obj1.brand = "Apple";
       obj1.price = 1500;
       Mobile.name = "SmartPhone";

       Mobile obj2 = new Mobile();
       obj2.brand = "Samsung";
       obj2.price = 1700;
       Mobile.name = "SmartPhone";

       obj1.show();
       obj2.show();
   }
}
```

---

### Static Method
A method that belongs to the class rather than any object. Can be called without creating an instance.

Example:
```java
class Mobile {
   static String name;
   public static void show1(Mobile obj) {
       System.out.println(obj.brand + " : " + obj.price + " : " + obj.name);
   }
}

public class Demo {
   public static void main(String[] args) {
       Mobile obj1 = new Mobile();
       obj1.brand = "Apple";
       obj1.price = 1500;
       Mobile.name = "SmartPhone";

       Mobile obj2 = new Mobile();
       obj2.brand = "Samsung";
       obj2.price = 1700;
       Mobile.name = "SmartPhone";

       obj1.show1(obj1);
   }
}
```

---

### Why we use `static` in `main` method?
- The `main` method is the entry point of a Java application. Using `static` allows the JVM to call this method without needing an instance of the class.
- **Summary**: We use `static` so the JVM can call `main()` without needing an instance.

---

### Static Block
A block of code that runs once when the class is loaded. Used for static initializations.

Example:
```java
class Mobile {
   static String name;

   static {
       name = "Phone";
       System.out.println("in static block");
   }

   public Mobile() {
       System.out.println("in constructor");
   }
}

public class Demo {
   public static void main(String[] args) {
       try {
           Class.forName("Mobile");
       } catch (ClassNotFoundException e) {
           e.printStackTrace();
       }
   }
}
```

---

### Encapsulation
Wrapping data (variables) and code (methods) together as a single unit. Achieved by making variables private and providing public getter and setter methods.

Example:
```java
class Human {
   private int age;
   private String name;

   public int getAge() {
       return age;
   }

   public void setAge(int age) {
       this.age = age;
   }

   public String getName() {
       return name;
   }

   public void setName(String name) {
       this.name = name;
   }
}

public class Demo {
   public static void main(String[] args) {
       Human obj = new Human();
       obj.setAge(30);
       obj.setName("Reddy");
       System.out.println(obj.getName() + " : " + obj.getAge());
   }
}
```

---

### `This` Keyword
Refers to the current instance of the class. Used to differentiate between class attributes and parameters with the same name.

Example:
```java
class Human {
   private int age;
   private String name;

   public void setAge(int age, Human obj) {
       obj.age = age;
   }

   public String getName() {
       return name;
   }

   public void setName(String name) {
       this.name = name;
   }
}

public class Demo {
   public static void main(String[] args) {
       Human obj = new Human();
       obj.setAge(30, obj);
       obj.setName("Reddy");
       System.out.println(obj.getName() + " : " + obj.getAge());
   }
}
```

---

### Constructor
- A **constructor** is a special method used to initialize objects. It has the same name as the class and no return type.

Example:
```java
class Human {
   private int age;
   private String name;

   public Human() {
       age = 12;
       name = "John";
   }

   public int getAge() {
       return age;
   }

   public void setAge(int age) {
       this.age = age;
   }

   public String getName() {
       return name;
   }

   public void setName(String name) {
       this.name = name;
   }
}

public class Demo {
   public static void main(String[] args) {
       Human obj = new Human();
       System.out.println(obj.getName() + " : " + obj.getAge());
   }
}
```

---

### Default vs Parameterized Constructor
- **Default Constructor**: Takes no parameters.
- **Parameterized Constructor**: Takes arguments to initialize variables.

Example:
```java
class Student {
   String name;
   int age;

   // Parameterized constructor
   Student(String name, int age) {
       this.name = name;
       this.age = age;
   }
}
```

---

### Naming Conventions
- **Class names**: PascalCase → `StudentDetails`
- **Variables & methods**: camelCase → `studentName`, `getName()`
- **Constants**: UPPER_CASE → `MAX_LIMIT`

---

### Anonymous Object
An object without a reference variable. Used when an object is only needed once.

Example:
```java
new A();  // anonymous object
new A().show();  // anonymous object calling a method
```

---

### Inheritance
- **Inheritance** allows one class to acquire properties and behaviors of another, promoting code reuse.

Example:
```java
class Calc {
   public int add(int n1, int n2) {
       return n1 + n2;
   }
}

class AdvCalc extends Calc {
   public int multi(int n1, int n2) {
       return n1 * n2;
   }
}
```

---

### Single and Multilevel Inheritance
- **Single Inheritance**: One class inherits from one parent class.
- **Multilevel Inheritance**: A class inherits from a child class, which in turn inherits from a parent class.

Example:
```java
class Calc {
   public int add(int n1, int n2) {
       return n1 + n2;
   }
}

class AdvCalc extends Calc {
   public int multi(int n1, int n2) {
       return n1 * n2;
   }
}

class VeryAdvCalc extends AdvCalc {
   public double power(int n1, int n2) {
       return Math.pow(n1, n2);
   }
}
```

---

### Multiple Inheritance (with Interfaces)
- Java doesn't support multiple inheritance with classes, but supports it via interfaces.
  
Example:
```java
interface A { }
interface B { }

class C implements A, B { }
```
### `this` and `super` Keyword

- **`this`:** Refers to the current instance of the class. It is used to refer to the current object, especially when there is a need to differentiate between instance variables and method parameters.
- **`super`:** Refers to the parent class. It is used to call methods or access fields of the parent class.

**Example:**
```java
class Parent {
    String name = "Parent Name";

    public void display() {
        System.out.println("Parent class display");
    }
}

class Child extends Parent {
    String name = "Child Name";

    public void show() {
        // Using 'this' to refer to the current class instance variable
        System.out.println("This name: " + this.name); 
        // Using 'super' to refer to the parent class instance variable
        System.out.println("Super name: " + super.name); 
    }

    @Override
    public void display() {
        // Calling the parent class method
        super.display();  
        System.out.println("Child class display");
    }
}

public class Demo {
    public static void main(String[] args) {
        Child c = new Child();
        c.show(); // Demonstrating 'this' and 'super'
        c.display(); // Demonstrating method overriding
    }
}
```

### Method Overriding
- **Method Overriding** allows a subclass to provide a specific implementation for a method that is already provided by its superclass. This helps in achieving **runtime polymorphism**.

**Example:**
```java
class Calc {
    public int add(int n1, int n2) {
        return n1 + n2;
    }
}

class AdvCalc extends Calc {
    @Override
    public int add(int n1, int n2) {
        return n1 + n2 + 1; // Overriding the add method
    }
}

public class Demo {
    public static void main(String[] args) {
        AdvCalc obj = new AdvCalc();
        int result = obj.add(3, 4);  // Calls the overridden add method
        System.out.println(result);  // Output: 8
    }
}
```

### Packages
- **Packages** are used to group related classes, interfaces, and sub-packages. They help prevent name conflicts and provide access protection.

**Example:**
```java
// File: mypackage/MyClass.java
package mypackage;

public class MyClass {
    public void display() {
        System.out.println("Hello from MyClass!");
    }
}

// File: Demo.java
import mypackage.MyClass;

public class Demo {
    public static void main(String[] args) {
        MyClass obj = new MyClass();
        obj.display();
    }
}
```

### Access Modifiers
- **Public:** Accessible everywhere.
- **Protected:** Accessible within the same package and subclasses.
- **Default (no modifier):** Accessible within the same package.
- **Private:** Accessible only within the class.

### Polymorphism
Polymorphism allows objects of different classes to be treated as objects of a common superclass. It can be categorized into two types:
1. **Compile-time polymorphism (Method Overloading):**
   - Same method name but different parameter types or number of parameters.
   
   **Example:**
   ```java
   class Calc {
       public int add(int a, int b) {
           return a + b;
       }
       
       public int add(int a, int b, int c) {
           return a + b + c;
       }
   }
   ```

2. **Runtime polymorphism (Method Overriding):**
   - The method call is resolved at runtime.
   
   **Example:**
   ```java
   class A {
       public void show() {
           System.out.println("In A");
       }
   }

   class B extends A {
       @Override
       public void show() {
           System.out.println("In B");
       }
   }

   public class Demo {
       public static void main(String[] args) {
           A obj = new B();  // Upcasting
           obj.show();  // Output: In B
       }
   }
   ```

### Dynamic Method Dispatch
- It refers to the process of calling an overridden method at runtime based on the object type.

**Example:**
```java
class A {
    public void show() {
        System.out.println("In A show");
    }
}

class B extends A {
    @Override
    public void show() {
        System.out.println("In B show");
    }
}

public class Demo {
    public static void main(String[] args) {
        A obj = new B();  // Reference type A, object type B
        obj.show();  // Output: In B show
    }
}
```

### `final` Keyword
- **`final` Variable:** The value cannot be changed after initialization.
- **`final` Method:** The method cannot be overridden.
- **`final` Class:** The class cannot be subclassed.

**Example:**
```java
final class FinalClass {
    // This class cannot be inherited
}

class SubClass { 
    // Uncommenting the next line would result in a compilation error
    // class SubClass extends FinalClass { } 
}
```

### Object Class Methods (`equals()`, `toString()`, `hashCode()`)

- **`equals()`** compares the content of two objects.
- **`toString()`** returns a string representation of the object.
- **`hashCode()`** returns a hash code value for the object.

**Example:**
```java
class Laptop {
    String model;
    int price;

    @Override
    public String toString() {
        return model + " : " + price;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Laptop laptop = (Laptop) obj;
        return price == laptop.price && model.equals(laptop.model);
    }

    @Override
    public int hashCode() {
        return 31 * model.hashCode() + price;
    }
}

public class Demo {
    public static void main(String[] args) {
        Laptop obj1 = new Laptop();
        obj1.model = "Lenovo Yoga";
        obj1.price = 1000;

        Laptop obj2 = new Laptop();
        obj2.model = "Lenovo Yoga";
        obj2.price = 1000;

        System.out.println(obj1.equals(obj2));  // true
        System.out.println(obj1.toString());    // Lenovo Yoga : 1000
    }
}
```

### Upcasting and Downcasting
- **Upcasting:** Referring a subclass object by a superclass reference.
- **Downcasting:** Casting a superclass reference to a subclass reference.

**Example:**
```java
class Animal {}
class Dog extends Animal {}

public class Demo {
    public static void main(String[] args) {
        Animal a = new Dog();  // Upcasting
        Dog d = (Dog) a;  // Downcasting
    }
}
```

### Wrapper Class
- **Wrapper classes** convert primitive types to objects for use in collections.

**Example:**
```java
Integer obj = Integer.valueOf(10);  // Converts int to Integer object
int x = obj.intValue();  // Converts Integer object back to int
```
```

---

# 🎉 End of Java Quick Notes

---

> **Tip:**  
For an even **more beautiful MkDocs** experience, consider using **Material for MkDocs** theme. It supports emoji, collapsible sections, code highlighting, search, and more!

---

Would you also like me to give you a **better sidebar navigation** (`mkdocs.yml`) for this content? 🚀  
(Like "Basics", "Operators", "OOP", "Arrays", etc organized nicely?) 🎯