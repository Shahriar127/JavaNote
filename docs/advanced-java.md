# Advanced Java

To make your content more structured, readable, and visually appealing for documentation (using a tool like MkDocs), I will break it into sections with clear headings, subheadings, and code blocks. I will also format the content in a more organized manner for clarity.

---

## **Advanced Java Concepts**

### **Abstract Keyword**

The `abstract` keyword is used to declare a class or method as abstract. An abstract class cannot be instantiated and may contain abstract methods (methods without a body). These abstract methods must be implemented by subclasses.

#### **Abstract Class Example**
```java
public abstract class Car {
    // Abstract methods
    public abstract void drive();
    public abstract void fly();

    // Regular method
    public void playMusic() {
        System.out.println("Play music");
    }
}

abstract class WagnoR extends Car {
    // Implementation of drive() method
    public void drive() {
        System.out.println("Driving...");
    }
}

class UpdateWagnoR extends WagnoR {   // Concrete class
    // Implementation of fly() method
    public void fly() {
        System.out.println("Flying...");
    }
}

public class Demo {
    public static void main(String[] args) {
        // Car obj = new Car();   // Cannot instantiate abstract class
        // Car obj = new WagnoR();   // Cannot instantiate abstract class
        Car obj = new UpdateWagnoR();   // Creating object of concrete class
        obj.drive();
        obj.playMusic();
    }
}
```

---

### **Inner Class**

An **inner class** is a class defined within another class. It helps in logically grouping classes and increases encapsulation. Types of inner classes include non-static (regular), static, local, and anonymous inner classes.

#### **Example of Static Inner Class**
```java
class A {
    int age;

    public void show() {
        System.out.println("In show");
    }

    // Static inner class
    static class B {
        public void config() {
            System.out.println("In config");
        }
    }
}

public class Demo {
    public static void main(String[] args) {
        A obj = new A();
        obj.show();

        A.B obj1 = new A.B();   // Accessing static inner class
        obj1.config();
    }
}
```

---

### **Anonymous Inner Class**

An **anonymous inner class** is a class without a name, declared and instantiated in a single expression. It is often used for one-time use or when implementing interfaces or extending classes.

#### **Example of Anonymous Inner Class**
```java
class A {
    public void show() {
        System.out.println("In A show");
    }
}

public class Demo {
    public static void main(String[] args) {
        A obj = new A() {  // Anonymous inner class
            public void show() {
                System.out.println("In new show");
            }
        };
        obj.show();
    }
}
```

---

### **Abstract and Anonymous Inner Class**

An abstract class can be implemented anonymously using an anonymous inner class. This is particularly useful when only one instance is needed with customized method implementations.

#### **Example: Abstract Class with Anonymous Inner Class**
```java
abstract class A {
    public abstract void show();
    public abstract void config();
}

public class Demo {
    public static void main(String[] args) {
        A obj = new A() {  // Anonymous inner class implementing abstract class
            public void show() {
                System.out.println("In new show");
            }
            public void config() {
                System.out.println("In config");
            }
        };
        obj.show();
    }
}
```

---

### **What is an Interface?**

An **interface** is a blueprint for a class. It contains abstract methods and constants. A class that implements an interface must provide implementations for all its methods.

- **Methods** in interfaces are public and abstract by default.
- **Variables** in interfaces are `public`, `static`, and `final` by default.

#### **Example of Interface Implementation**
```java
interface Computer {
    void code();
}

class Laptop implements Computer {
    public void code() {
        System.out.println("Code, compile, run");
    }
}

class Desktop implements Computer {
    public void code() {
        System.out.println("Code, compile, faster");
    }
}

class Developer {
    public void devApp(Computer comp) {
        comp.code();
    }
}

public class Demo {
    public static void main(String[] args) {
        Computer lap = new Laptop();
        Computer desk = new Desktop();

        Developer dev = new Developer();
        dev.devApp(lap);
        dev.devApp(desk);
    }
}
```

---

### **Enum in Java**

An **enum** is a special Java type used to define collections of constants. Enums are more powerful than regular constants because they can have fields, methods, and constructors.

#### **Basic Enum Example**
```java
enum Status {
    Running, Failed, Pending, Success;
}

public class Demo {
    public static void main(String[] args) {
        Status[] ss = Status.values();
        for (Status s : ss) {
            System.out.println(s + " : " + s.ordinal());
        }
    }
}
```

#### **Using Enums in Switch-Case**
Enums can be used in switch-case statements for cleaner control flow.

```java
enum Status {
    Running, Failed, Pending, Success;
}

public class Demo {
    public static void main(String[] args) {
        Status s = Status.Pending;

        switch (s) {
            case Running:
                System.out.println("All Good");
                break;
            case Failed:
                System.out.println("Try Again");
                break;
            case Pending:
                System.out.println("Please Wait");
                break;
            default:
                System.out.println("Done");
                break;
        }
    }
}
```

---

### **Enum Class with Methods**

Enums in Java are full-fledged classes, and they can contain fields, constructors, and methods.

#### **Enum with Methods Example**
```java
enum Laptop {
    Mackbook(2000), XPS(2200), Surface(1500), ThinkPad(1800);

    private int price;

    private Laptop(int price) {
        this.price = price;
    }

    public int getPrice() {
        return price;
    }
}

public class Demo {
    public static void main(String[] args) {
        for (Laptop lap : Laptop.values()) {
            System.out.println(lap + " : " + lap.getPrice());
        }
    }
}
```

---

### **Lambda Expressions**

Introduced in Java 8, **lambda expressions** provide a clear and concise way to implement functional interfaces. They are used to pass behavior as arguments to methods or to create a small function.

#### **Lambda Expression Example**
```java
@FunctionalInterface
interface A {
    void show(int i);
}

public class Demo {
    public static void main(String[] args) {
        A obj = (int i) -> System.out.println("In show " + i);
        obj.show(5);
    }
}
```

---

### **Exception Handling in Java**

An **exception** is an event that disrupts the normal flow of the program. Exception handling in Java allows you to handle errors gracefully.

#### **Try-Catch Block Example**
```java
public class Demo {
    public static void main(String[] args) {
        int i = 0;
        int j = 0;

        try {
            j = 18 / i;  // Potential divide by zero error
        } catch (Exception e) {
            System.out.println("Something went wrong: " + e);
        }
        System.out.println("Value of j: " + j);
    }
}
```

#### **Throw Keyword Example**
The `throw` keyword is used to manually throw an exception.

```java
public class Demo {
    public static void main(String[] args) {
        int i = 0;
        int j = 0;

        try {
            if (i == 0) {
                throw new ArithmeticException("Cannot divide by zero");
            }
        } catch (ArithmeticException e) {
            System.out.println("Exception: " + e.getMessage());
        }
    }
}
```

Here is the complete and formatted version of your Java concepts, organized for better readability and understanding. You can use this for your documentation.

---

### 88. **Custom Exception**
Custom exceptions allow you to define your own exception classes by extending either `Exception` or `RuntimeException`.

```java
class NavinException extends Exception {
   public NavinException(String string) {
       super(string);
   }
}

public class Demo {
   public static void main(String[] args) {
       int i = 20;
       int j = 0;

       try {
           j = 18 / i;
           if (j == 0)
               throw new NavinException("I don't want to do print zero");
       } catch (ArithmeticException e) {
           j = 18 / i;
           System.out.println("Default output: " + e);
       } catch (Exception e) {
           System.out.println("Something went wrong: " + e);
       }
       System.out.println(j);
       System.out.println("Bye");
   }
}
```

---

### 89. **Ducking Exception using `throws`**
The `throws` keyword is used to indicate that a method might throw an exception.

```java
class NavinException extends Exception {
   public NavinException(String string) {
       super(string);
   }
}

class A {
   public void show() throws ClassNotFoundException {
       Class.forName("Calc");
   }
}

public class Demo {
   static {
       System.out.println("Class Loader");
   }

   public static void main(String[] args) {
       A obj = new A();
       try {
           obj.show();
       } catch (ClassNotFoundException e) {
           e.printStackTrace();
       }
   }
}
```

---

### 90. **User Input using `BufferedReader` and `Scanner`**
- `BufferedReader` is faster and used for reading strings.
- `Scanner` is easier for reading different data types.

```java
// Using Scanner
Scanner sc = new Scanner(System.in);
int num = sc.nextInt();

// Using BufferedReader
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
String input = br.readLine();
```

---

### 91. **Try with Resources**
Automatically closes resources like files or streams once the block of code is finished.

```java
try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
    String line = br.readLine();
}
```

---

### 92. **Threads in Java**
Threads allow concurrent execution. You can create a thread by extending the `Thread` class or implementing the `Runnable` interface.

---

### 93. **Multiple Threads**
You can run multiple threads simultaneously.

```java
Thread t1 = new MyThread();
t1.start();
```

---

### 94. **Thread Priority and Sleep**
- `setPriority()`: Sets the priority of a thread.
- `sleep(ms)`: Pauses a thread for a specified number of milliseconds.

```java
Thread.sleep(1000); // Sleep for 1 second
```

---

### 95. **Runnable vs Thread**
- `Runnable`: Interface, better for reusability.
- `Thread`: Class, but can't extend other classes if extended.

---

### 96. **Race Condition**
Occurs when multiple threads access and modify shared data at the same time, leading to unpredictable results.

---

### 97. **Thread States**
Thread states include:
- New
- Runnable
- Blocked
- Waiting
- Timed Waiting
- Terminated

---

### 98. **Collection API**
The Collection API is a framework used to store and manipulate groups of objects. It includes different data structures such as `List`, `Set`, `Map`, etc.

---

### 99. **ArrayList**
An `ArrayList` is a resizable array that implements the `List` interface.

```java
List<Integer> nums = new ArrayList<>();
nums.add(6);
nums.add(5);
nums.add(8);
nums.add(2);
System.out.println(nums.get(2));
System.out.println(nums.indexOf(2));
```

---

### 100. **Set**
A `Set` is a collection that does not allow duplicate elements. Common implementations include `HashSet` and `TreeSet`.

```java
Set<Integer> nums = new HashSet<>();
nums.add(6);
nums.add(5);
nums.add(8);
nums.add(2);
System.out.println(nums);
```

---

### 101. **Map**
A `Map` stores data as key-value pairs. Common implementations include `HashMap` and `Hashtable`.

```java
Map<String, Integer> students = new Hashtable<>();
students.put("Navin", 56);
students.put("Harsh", 23);
students.put("Sushil", 67);
students.put("Kiran", 92);
students.put("Harsh", 45);
System.out.println(students.keySet());
```

---

### 102. **Comparator vs Comparable**
- `Comparable`: Used for natural ordering (`compareTo()` method).
- `Comparator`: Used for custom ordering (`compare()` method).

```java
class Student {
    int age;
    String name;
    public Student(int age, String name) {
        this.age = age;
        this.name = name;
    }

    @Override
    public String toString() {
        return "Student [age=" + age + ", name=" + name + "]";
    }
}

Comparator<Student> com = (i, j) -> i.age > j.age ? 1 : -1;

List<Student> studs = new ArrayList<>();
studs.add(new Student(21, "Navin"));
studs.add(new Student(12, "John"));
studs.add(new Student(18, "Parul"));
studs.add(new Student(20, "Kiran"));

Collections.sort(studs);
for (Student s : studs) {
    System.out.println(s);
}
```

---

### 103. **Need of Stream API**
The Stream API provides a functional approach to process collections, making code more readable and concise.

---

### 104. **forEach Method**
Used to iterate through a collection.

```java
list.forEach(item -> System.out.println(item));
```

---

### 105. **Stream API**
Streams allow data to be processed in a pipeline using methods like `filter`, `map`, and `reduce`.

```java
list.stream().filter(x -> x > 10).collect(Collectors.toList());
```

---

### 106. **Map, Filter, Reduce, Sorted**
- `map()`: Transforms elements.
- `filter()`: Selects elements.
- `reduce()`: Reduces to a single value.
- `sorted()`: Sorts the stream.

---

### 107. **ParallelStream in Java**
Processes elements in parallel, utilizing multi-core processors.

```java
list.parallelStream().forEach(System.out::println);
```

---

### 108. **Optional Class in Java**
An `Optional` is a container object used to avoid null checks.

```java
Optional<String> name = Optional.ofNullable(null);
name.orElse("Default");
```

---

### 109. **Method Reference**
A shorthand for lambda expressions that call a method.

```java
list.forEach(System.out::println);
```

---

### 110. **Constructor Reference**
Used to reference a constructor.

```java
Supplier<List<String>> listSupplier = ArrayList::new;
```

---

This breakdown is now ready for documentation or for any usage that requires clarity and a structured format.

---

### **Final Thoughts**

These concepts lay the foundation for understanding some of the more advanced features in Java. Whether you are working with abstraction, interfaces, lambda expressions, or exception handling, mastering these will help you write more efficient and readable Java code.

