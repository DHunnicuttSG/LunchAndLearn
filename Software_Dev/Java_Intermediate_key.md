## **Java Intermediate — Key**

---

### **1. What is the role of the Service Layer in MVC architecture?**

The **Service Layer** contains **business logic** — it acts as a bridge between the **Controller (input layer)** and the **Data Access Layer (Model/Repository)**.
It processes data, enforces rules, and ensures separation of concerns.

---

### **2. Differences Between Black Box and Glass Box Testing**

| Type                              | Description                                                               | Tester Knows Internal Code? | Focus                |
| --------------------------------- | ------------------------------------------------------------------------- | --------------------------- | -------------------- |
| **Black Box Testing**             | Tests system behavior from the outside using inputs and expected outputs. | ❌ No                        | Functionality        |
| **Glass Box (White Box) Testing** | Tests the internal structure and logic of the code.                       | ✅ Yes                       | Code paths and logic |

---

### **3. Compare and Contrast Unit, Integration, and User Acceptance Testing**

| Test Type                         | Focus                                     | Performed By       | Purpose                                         |
| --------------------------------- | ----------------------------------------- | ------------------ | ----------------------------------------------- |
| **Unit Testing**                  | Individual methods or components          | Developers         | Verify small, isolated pieces of code           |
| **Integration Testing**           | Interaction between components or systems | Developers/Testers | Verify modules work together                    |
| **User Acceptance Testing (UAT)** | Entire system                             | End Users          | Ensure the software meets business requirements |

---

### **4. Explain the Red, Green, Refactor Model (TDD)**

* **Red:** Write a failing test (code doesn’t yet work).
* **Green:** Write just enough code to make the test pass.
* **Refactor:** Clean up the code while keeping all tests green.

This cycle encourages small, iterative development with constant testing.

---

### **5. Find the Labels Associated with the Following Descriptions (Unit Testing)**

| Description                                                                      | Testing Step |
| -------------------------------------------------------------------------------- | ------------ |
| “Put the code in a known good state and create/arrange all necessary test data.” | **Arrange**  |
| “This test uses the arranged data to execute the code we are testing.”           | **Act**      |
| “Are the results what we expect?”                                                | **Assert**   |

*(Known as the **AAA Pattern** — Arrange, Act, Assert.)*

---

### **6. What @ Annotations Are Used When Creating Unit Tests?**

Common JUnit annotations:

* `@Test` — marks a test method.
* `@BeforeEach` — runs before each test.
* `@AfterEach` — runs after each test.
* `@BeforeAll` — runs once before all tests (must be static).
* `@AfterAll` — runs once after all tests (must be static).

---

### **7. Difference Between Stateful and Stateless Unit Tests**

| Type          | Description                                                                      |
| ------------- | -------------------------------------------------------------------------------- |
| **Stateful**  | Tests rely on data or state left over from previous tests (not ideal).           |
| **Stateless** | Each test runs independently, creating its own setup and data. (✅ Best practice) |

---

### **8. Create an ENUM for the Days of the Week or Months of the Year**

```java
public enum Day {
    SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY;
}
```

or

```java
public enum Month {
    JANUARY, FEBRUARY, MARCH, APRIL, MAY, JUNE,
    JULY, AUGUST, SEPTEMBER, OCTOBER, NOVEMBER, DECEMBER;
}
```

---

### **9. What is the Standard ISO Format for a Date?**

`YYYY-MM-DD` (e.g., `2025-11-11`)

---

### **10. Write Code to Format a Date into the Format 01/01/2022**

```java
LocalDate date = LocalDate.of(2022, 1, 1);
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("MM/dd/yyyy");
String formatted = date.format(formatter);
System.out.println(formatted); // 01/01/2022
```

---

### **11. Advantage of Using BigDecimal Compared to float or double**

* Provides **exact precision** for financial or currency calculations.
* Avoids **rounding errors** common with floating-point numbers.

---

### **12. Syntax to Create a New BigDecimal Number “22.76”**

```java
BigDecimal amount = new BigDecimal("22.76");
```

*(Use a String literal to avoid precision loss.)*

---

### **13. What is a Lambda?**

A **lambda expression** is a short, inline way to define a function or behavior without writing a full method or class.
Example:

```java
(numbers) -> numbers * 2
```

Used heavily in functional programming and stream operations.

---

### **14. What is a Stream (in the Java 8+ Collection API)?**

A **Stream** is a sequence of data elements that supports **functional-style operations** (like map, filter, reduce) on collections.
Streams don’t store data — they process data from collections.

---

### **15. Example of Aggregate Operations**

Operations that **combine or summarize** data:

```java
List<Integer> nums = List.of(1,2,3,4,5);
int sum = nums.stream().reduce(0, Integer::sum);
long count = nums.stream().count();
Optional<Integer> max = nums.stream().max(Integer::compareTo);
```

Aggregate ops include: `count()`, `sum()`, `max()`, `min()`, `reduce()`, `collect()`.

---

### **16. What is a Pipeline?**

A **pipeline** is a **chain of stream operations** where data flows from a source through intermediate operations to a terminal operation.
Example:

```java
List<String> names = List.of("Alice", "Bob", "Ann");
names.stream()
     .filter(n -> n.startsWith("A"))
     .map(String::toUpperCase)
     .forEach(System.out::println);
```

Here, `filter` and `map` are **intermediate operations**, and `forEach` is the **terminal operation**.

---

### **17. Ways to Iterate Over a Pipeline**

1. **Terminal Operations** (consume the stream):

   * `forEach()`
   * `collect()`
   * `reduce()`

2. **Convert Back to Collection:**

   ```java
   List<Integer> results = stream.collect(Collectors.toList());
   ```

3. **Using Intermediate + Terminal Combo:**
   Any combination that ends with a terminal operation (streams are **lazy** until terminated).

---
