## ✅ **Java Classes and Objects — Answer Key**

---

### **Core OOP Principles**

**1. Inheritance, Polymorphism, Encapsulation, and Abstraction**

* **Inheritance:** Allows one class (child/subclass) to acquire the properties and methods of another (parent/superclass).
* **Polymorphism:** The ability for the same method or behavior to take different forms depending on the object that calls it.
* **Encapsulation:** Bundling of data (fields) and methods that operate on that data into a single unit (class), and restricting access using access modifiers.
* **Abstraction:** Hiding complex implementation details and showing only the necessary features of an object.

---

**2. Single Responsibility Principle (SRP)**
Each class should have only **one responsibility or reason to change** — it should do **one thing well**.

---

**3. Difference between a Class and an Object**

* **Class:** A blueprint or template defining properties and behaviors.
* **Object:** A specific instance of a class created in memory.

---

**4. Accessor/Getter**
A method that retrieves or “gets” the value of a private field.
Example:

```java
public String getName() { return name; }
```

---

**5. Mutator/Setter**
A method that updates or “sets” the value of a private field.
Example:

```java
public void setName(String name) { this.name = name; }
```

---

**6. Constructor**
A special method used to initialize new objects. It has the same name as the class and no return type.

---

**7. Shadowing (not best practice)**
Occurs when a local variable (or parameter) has the same name as a class field, hiding the field within that scope.

---

### **Access Control & Static Concepts**

**8. Public, Private, and Protected**

* **public:** Accessible from anywhere.
* **private:** Accessible only within the same class.
* **protected:** Accessible within the same package and by subclasses.

---

**9. Static vs Non-Static**

* **static:** Belongs to the class (shared among all instances).
* **non-static:** Belongs to a specific object instance.

---

**10. abstract Keyword and Classes**

* Declares a class or method that **cannot be instantiated** and **must be implemented by subclasses**.
* Used to define a base class with incomplete behavior.

---

### **Classes and Collections**

**11. Collection Class Usage**
The `Collection` interface provides a framework for storing and manipulating groups of objects (e.g., Lists, Sets, Maps).

---

**12. Cohesive Class**
A class is **cohesive** if all its methods and fields work toward a single, well-defined purpose.

---

**13. Local Class**
A class defined **inside a method**. It’s visible only within that method.

---

**14. Access Level of Static Nested Class**
A static nested class **cannot access instance variables** or methods of the outer class directly — only static members.

---

**15. Local Class Variable Access**
A local class can access **final or effectively final variables** from the enclosing method.

---

### **Code Examples**

**16. Car Constructor Example**

```java
public class Car {
    String action;
    String reaction;

    public Car(String action, String reaction) {
        this.action = action;
        this.reaction = reaction;
    }
}
```

---

**17. Dog Getters and Setters**

```java
public class Dog {
    private String name;
    private int age;

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public int getAge() { return age; }
    public void setAge(int age) { this.age = age; }
}
```

---

**18. Example of an Interface**

```java
public interface Animal {
    void eat();
    void sleep();
}
```

---

**19. Airplane Interface and AirBus787 Implementation**

```java
public interface AirplaneOperations {
    void turnLeft();
    void climb();
    void descend();
}

public class AirBus787 implements AirplaneOperations {
    public void turnLeft() { System.out.println("Turning left"); }
    public void climb() { System.out.println("Climbing"); }
    public void descend() { System.out.println("Descending"); }
}
```

---

**20. Can You Instantiate an Interface?**
No — you can only implement it through a class or use an **anonymous class** or **lambda expression**.

---

**21. extends vs implements**

* **extends:** Used for class inheritance (one class to another).
* **implements:** Used for implementing one or more interfaces.

---

**22. Class Using Two Other Classes**

```java
public class ContactInfo {
    private Phone phone;
    private Address address;
}
```

---

**23. Default Access Modifier**
If no modifier is specified, it defaults to **package-private**, meaning it’s accessible only within the same package.

---

**24. Base Class of All Classes**
`java.lang.Object`

---

### **Collections**

**25. List vs ArrayList**

* **List:** Interface defining ordered collection behavior.
* **ArrayList:** A resizable array implementation of the List interface.

---

**26. Set vs HashSet**

* **Set:** Collection of unique elements (no duplicates).
* **HashSet:** Implementation of Set using hashing for fast lookup.

---

**27. Map vs HashMap**

* **Map:** Key-value pair collection.
* **HashMap:** Implements Map using hashing for fast retrieval.

---

**28. Derived vs Extended Classes**
Both mean subclassing — a **derived/extended** class inherits from another class. “Extended” is Java’s keyword. The difference here is terminology, not functionality.

---

**29. Inheritance and Polymorphism**
Inheritance allows subclasses to **override methods** from the parent, enabling **runtime polymorphism** (same method, different behavior).

---

**30. Abstract Base Class**
A class declared `abstract` that provides partial implementation for subclasses to extend and complete.

---

**31. Superclass**
The parent class that is inherited from.

---

**32. Subclass**
The child class that inherits from the superclass.

---

### **File I/O and Coupling**

**33. Read from a File**

```java
Scanner sc = new Scanner(new File("input.txt"));
while (sc.hasNextLine()) {
    System.out.println(sc.nextLine());
}
sc.close();
```

---

**34. Write to a File**

```java
FileWriter fw = new FileWriter("output.txt");
fw.write("Hello World");
fw.close();
```

---

**35. Loosely Coupled**
Classes are independent and interact through interfaces or abstractions — reduces dependencies and increases flexibility.

---

**36. Why Split Applications into Layers**
Encourages separation of concerns, easier maintenance, testing, and scalability.

---

**37. MVC Design Pattern**

* **Model:** Handles data and business logic.
* **View:** Handles UI/display.
* **Controller:** Handles input, routes actions between Model and View.

---

**38. Categorizing Files into MVC:**

| File                                                | MVC Category |
| --------------------------------------------------- | ------------ |
| Supplier class                                      | Model        |
| Game class                                          | Model        |
| Class that maps URLs to actions                     | Controller   |
| List of actions you can do with the data            | Controller   |
| Implementation of those actions you use in your app | Controller   |
| Data you use inside of your app                     | Model        |
| Business rules of your app                          | Model        |

---

### **Development and Error Handling**

**39. Waterfall vs Agile**

* **Waterfall:** Linear, sequential phases; changes are difficult mid-process.
* **Agile:** Iterative and flexible, with frequent feedback and adaptation.

---

**40. Syntax vs Logical vs Runtime Errors**

* **Syntax:** Violations of language grammar (won’t compile).
* **Logical:** Code runs but produces wrong results.
* **Runtime:** Errors that occur while program executes (e.g., divide by zero).

---

**41. Checked vs Unchecked Exceptions**

* **Checked:** Must be handled or declared (e.g., IOException).
* **Unchecked:** Runtime exceptions not required to be declared (e.g., NullPointerException).

---

**42. try/catch/finally**

* **try:** Code that may throw an exception.
* **catch:** Handles specific exceptions.
* **finally:** Always executes (cleanup, closing files, etc.).

---

**43. throws Keyword**
Used in a method signature to indicate it might throw an exception that must be handled by the calling method.
Example:

```java
public void readFile() throws IOException { ... }
```

---
