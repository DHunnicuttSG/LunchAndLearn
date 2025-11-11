## ✅ **SQL Basics — Answer Sheet**

---

### **1. What is a relational database?**

A **relational database** organizes data into **tables (relations)** consisting of rows and columns. Each table represents an entity, and relationships are formed between tables using **keys** (primary and foreign).
**Example:** MySQL, PostgreSQL, Oracle.

---

### **2. What are some advantages of relational databases?**

* **Data integrity** through constraints (primary/foreign keys).
* **Reduced redundancy** via normalization.
* **ACID compliance** ensures reliable transactions.
* **Powerful querying** with SQL.
* **Scalability** and **data consistency** across applications.

---

### **3. What is the purpose of a database management system (DBMS)?**

A **DBMS** manages data storage, retrieval, and security while enforcing consistency and access control.
It provides tools to **create**, **read**, **update**, and **delete** data efficiently (CRUD operations).

---

### **4. Explain the difference between a MySQL server and a MySQL client.**

* **MySQL Server:** The background service that stores data and processes SQL commands.
* **MySQL Client:** A tool (like `mysql` CLI or Workbench) used to connect to and send queries to the server.

---

### **5. What is DDL and how is it used in database management?**

**DDL (Data Definition Language)** defines and manages database structure.
Examples:

```sql
CREATE TABLE, ALTER TABLE, DROP TABLE
```

Used to **create**, **modify**, or **remove** schema objects.

---

### **6. What is DML and how is it used in CRUD management?**

**DML (Data Manipulation Language)** is used to manage data within existing tables.
Examples:

```sql
INSERT, SELECT, UPDATE, DELETE
```

These commands correspond to **CRUD** operations (Create, Read, Update, Delete).

---

### **7. What does the `application.properties` file do?**

It’s a **Spring Boot configuration file** that defines application settings like:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=pass
```

Used for configuring the database connection, port, and logging.

---

### **8. What is normalization?**

**Normalization** is the process of organizing data to minimize redundancy and dependency.
It divides large tables into smaller ones and defines relationships.
**Normal forms:** 1NF, 2NF, 3NF, BCNF.

---

### **9. Compare and contrast primary key and foreign key.**

| Feature     | Primary Key                     | Foreign Key                               |
| ----------- | ------------------------------- | ----------------------------------------- |
| Purpose     | Uniquely identifies each record | Establishes a relationship between tables |
| Uniqueness  | Must be unique                  | May contain duplicates                    |
| Null values | Not allowed                     | Allowed (unless constrained)              |

---

### **10. Give an example of a one-to-one relationship.**

Each **person** has **one passport**.

```sql
Person(person_id, name)
Passport(passport_id, person_id)
```

---

### **11. Give an example of a one-to-many relationship.**

A **customer** can have **many orders**.

```sql
Customer(customer_id, name)
Order(order_id, customer_id)
```

---

### **12. Give an example of a many-to-many relationship.**

A **student** can enroll in **many courses**, and each **course** can have many students.
This requires a linking table:

```sql
Student(student_id)
Course(course_id)
Enrollment(student_id, course_id)
```

---

### **13. What is referential integrity?**

Ensures that relationships between tables remain consistent — foreign key values must match an existing primary key value or be null. Prevents orphaned records.

---

### **14. Explain how commit and rollback work in an SQL transaction.**

* **COMMIT:** Saves all changes made during the transaction permanently.
* **ROLLBACK:** Undoes all changes made in the current transaction.
  Used to maintain data consistency.

---

### **15. Explain how a dangling reference could be created.**

Occurs when a **foreign key** references a record that has been deleted or never existed — violating referential integrity.

---

### **16. What is a bridge/linking table?**

A **bridge** (or **junction**) table resolves **many-to-many** relationships by linking two entities via foreign keys.
Example: `StudentCourse(student_id, course_id)`

---

### **17. What types of relationships require a bridge/linking table?**

**Many-to-many (M:N)** relationships.

---

### **18. What is a validation table (system table)?**

A **lookup** or **reference** table containing valid values for another table.
Example: A `Status` table with values like "Active", "Inactive", "Pending."

---

### **19. How does a cascade delete/cascade update work?**

* **Cascade Delete:** Automatically deletes related child records when a parent record is deleted.
* **Cascade Update:** Automatically updates child foreign keys when the parent key changes.
  Example:

```sql
FOREIGN KEY (dept_id) REFERENCES Department(id)
ON DELETE CASCADE
ON UPDATE CASCADE
```

---

### **20. Create a simple SQL select statement.**

```sql
SELECT first_name, last_name FROM Employees;
```

---

### **21. Create a delete statement.**

```sql
DELETE FROM Employees WHERE id = 101;
```

---

### **22. Create an update statement.**

```sql
UPDATE Employees SET salary = 50000 WHERE id = 101;
```

---

### **23. Create a simple SQL join statement.**

```sql
SELECT Employees.name, Department.dept_name
FROM Employees
JOIN Department ON Employees.dept_id = Department.id;
```

---

### **24. Compare and contrast the types of SQL join statements.**

| Join Type  | Description                                  |
| ---------- | -------------------------------------------- |
| INNER JOIN | Returns matching rows from both tables       |
| LEFT JOIN  | Returns all from left + matches from right   |
| RIGHT JOIN | Returns all from right + matches from left   |
| FULL JOIN  | Returns all rows from both tables            |
| CROSS JOIN | Returns Cartesian product (all combinations) |

---

### **25. What is a Cartesian product (SQL cross join)?**

A join that returns **every combination** of rows from two tables.
If table A has 3 rows and B has 4, result = 3×4 = 12 rows.

---

### **26. What are the advantages of using Spring JDBC Template or JPA?**

* Simplify database access and transaction management.
* Reduce boilerplate code.
* Provide **object mapping** and **exception translation**.
* Allow switching between databases easily.
* JPA adds an **ORM layer** for entity management.

---

### **27. What is a prepared statement and when should it be used?**

A **precompiled SQL statement** that can be executed multiple times with different parameters.
Used for **performance** and **security** — especially when handling user input.

---

### **28. What is the relationship between prepared statements and SQL injection attacks?**

Prepared statements prevent SQL injection by **separating SQL logic from user input**, ensuring inputs are treated as data, not executable code.

---

### **29. What is JDBC / JDBC Template / JPA?**

* **JDBC (Java Database Connectivity):** Low-level API for database access using SQL queries.
* **JDBC Template:** Simplifies JDBC usage, handles exceptions and resource management automatically.
* **JPA (Java Persistence API):** High-level ORM framework for managing relational data using Java objects.

---

### **30. What is an ORM?**

**Object-Relational Mapping (ORM)** allows developers to interact with a database using **objects** instead of SQL.
Maps Java classes to database tables and attributes to columns.
**Examples:** Hibernate, JPA.

---
