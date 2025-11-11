
## ✅ **Java Advanced — Answer Key**

---

### **1. Explain the benefits of using Spring in MVC.**

* Provides a **clean separation of concerns** between Model, View, and Controller.
* Reduces boilerplate through **dependency injection** and **annotations**.
* Simplifies **web request handling** with built-in controllers and mappings.
* Integrates easily with **Spring Data**, **Spring Security**, and **Spring Boot**.
* Enables **testable**, **modular**, and **scalable** applications.

---

### **2. How are URL patterns mapped to controller code in Spring MVC/Data?**

* URL patterns are mapped using **annotations** like `@RequestMapping`, `@GetMapping`, `@PostMapping`, etc.
* Each mapping associates a **URL path** with a specific **controller method**.
* Example:

  ```java
  @GetMapping("/users/{id}")
  public User getUser(@PathVariable Long id) { ... }
  ```

---

### **3. What does the `@RestController` annotation do?**

* Combines `@Controller` and `@ResponseBody`.
* Marks a class as a **web controller** where every method returns data **directly as JSON or XML** (not a view).
* Commonly used for **RESTful APIs**.

---

### **4. What does the `@ResponseBody` annotation do?**

* Indicates that a method’s **return value** should be written **directly to the HTTP response body**, rather than being interpreted as a view name.
* Converts objects automatically to JSON or XML using **Jackson**.

---

### **5. What does the `@RequestBody` annotation do?**

* Binds the **HTTP request body** (usually JSON) to a **Java object** parameter.
* Example:

  ```java
  @PostMapping("/users")
  public void addUser(@RequestBody User user) { ... }
  ```

---

### **6. What does the `@PathVariable` annotation do?**

* Extracts **values from the URL path** and binds them to method parameters.
* Example:

  ```java
  @GetMapping("/users/{id}")
  public User getUser(@PathVariable("id") Long userId) { ... }
  ```

---

### **7. What does the `@RequestMapping` annotation do?**

* Used at the **class or method level** to define URL patterns and HTTP methods.
* Example:

  ```java
  @RequestMapping(value="/users", method=RequestMethod.GET)
  public List<User> getUsers() { ... }
  ```
* Can be replaced with specialized annotations like `@GetMapping`, `@PostMapping`, etc.

---

### **8. What does the `@CrossOrigin` annotation do?**

* Enables **CORS (Cross-Origin Resource Sharing)** for a controller or method.
* Allows web applications from different domains to access your API.
* Example:

  ```java
  @CrossOrigin(origins = "http://localhost:3000")
  @GetMapping("/data")
  public List<Data> getData() { ... }
  ```

---

### **9. What does the `@Autowired` annotation do?**

* Performs **dependency injection** automatically.
* Spring finds a matching **bean** and injects it into the annotated field, constructor, or setter.
* Example:

  ```java
  @Autowired
  private UserRepository repo;
  ```

---

### **10. What does the `@Repository` annotation do?**

* Marks a class as a **Data Access Object (DAO)**.
* Enables **automatic exception translation** (converts database exceptions to Spring’s `DataAccessException`).
* Also makes the class eligible for **component scanning**.

---

### **11. What does the `@Transactional` annotation do?**

* Defines **transaction boundaries** for a method or class.
* Ensures that database operations are executed as a **single atomic transaction** — if one fails, all are rolled back.
* Example:

  ```java
  @Transactional
  public void saveOrder(Order order) { ... }
  ```

---

### **12. How does Maven help manage your app?**

* **Build automation and dependency management tool**.
* Automatically downloads and manages library versions from the central repository.
* Simplifies compiling, testing, and packaging with commands like:

  ```
  mvn compile
  mvn test
  mvn package
  ```
* Ensures consistent builds across environments.

---

### **13. How do you use a POM.xml file during development?**

* The **Project Object Model (POM)** file defines:

  * **Project metadata** (name, version, groupId)
  * **Dependencies** (e.g., Spring Boot, JUnit, MySQL)
  * **Build configuration** (plugins, packaging, goals)

* Example:

  ```xml
  <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-web</artifactId>
  </dependency>
  ```

* Developers run Maven commands, and POM ensures the correct dependencies and build steps are applied.

---
