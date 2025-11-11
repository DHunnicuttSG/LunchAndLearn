## 🧠 **Java Basics — Interview Question Sheet**

---

1. What are the three steps in the life cycle of a Java program?
2. What is the difference between a compiler and an interpreter?
3. What is the syntax of the main method?
4. Describe the benefits of using an IDE during programming.
5. List the differences between syntax, runtime, and logic errors.
6. List the differences between data and information.
7. How do you write single-line and multi-line comments?
8. What is wrong with the following code?

   ```java
   public class Hello {
       String new = “My New House”;
       String short = “I am short”;
       String private  = “I am a private person”;
       int catch = 0;
       double this = 1.0;
   }
   ```
9. Assign each value to a data type:
   5
   128
   34,780
   Bob
   86.02
   true
   x
10. How would you keep the decimal value when doing the following operation?

    ```java
    int a = 10;
    int b = 4;
    float c = 0;

    c = a / b;
    ```
11. What data type is returned when reading from the console? What approach would you use to convert console data to another usable data type?
12. Describe how you would debug/step through your code using your IDE.
13. What is the output of this method?

    ```java
    public static void main(String[] args) {
        int a = 12;
        int b = 13;
        String  C = "Java";

        System.out.println(a + b + C);
        System.out.println(C + b + a);
    }
    ```
14. Analyze the following code and determine the output.

    ```java
    public static void main(String[] args) {
        int a = 12;
        int b = 13;
        String  C = "Java";

        if (a<=b) {
            System.out.println(a + " is less than " + b);
        }
        if (a<=b) {
            System.out.println(a + " is less than " + b);
        } else {
            System.out.println("This is false.");
        }
        if (C.equals("JAVA")) {
            System.out.println("This is true");
        } else {
            System.out.println("This is all uppercase!");
            if (C.equals("Java")) {
                System.out.println("This one is equal");
            }
        }
    }
    ```
15. Compare and contrast if statements with switch statements.
16. Write code to generate a random number between 1 and 6.
17. Evaluate and determine the output for the following code:

    ```java
    public static void main(String[] args) {
        boolean a = true;
        boolean b = false;
        String c = "Java";

        if (a && b ) {
            System.out.println("Both a and b are true");
        } else {
            System.out.println("Both a and b are not true");
        }

        if(a || b) {
            System.out.println("either a or b is true");
        }

        if (a && (b && c.equals("Java"))) {
            System.out.println("true");
        } else {
            System.out.println("false");
        }
    }
    ```
18. Write code that generates the following output:

    ```
    Counting down...

    10
    9
    8
    7
    6
    5
    4
    3
    2
    1
    0

    Blast off!
    ```
19. What is the difference between a while loop and a do/while loop?
20. Write code that generates the following output:

    ```
    1
    1 2
    1 2 3
    1 2 3 4
    1 2 3 4 5
    1 2 3 4 5 6
    ```
21. Explain the DRY principle.
22. Create a method to calculate the area of a rectangle.
23. Create a method to calculate the area of a triangle and return a value.
24. Explain the importance of scope.
25. What does the final keyword mean when used with a method?
26. What does the term @override do to a method?
27. How would you overload a method?
28. What does the static keyword mean?
29. What is the syntax to declare a simple array? A two-dimensional array?
30. Write syntax to declare and initialize an array with the values (1,2,3,4,5).
31. What occurred in the code if it returns an ArrayIndexOutOfBoundException?
32. What is the difference between an element and an index?
33. What are the limitations of an array?
34. Is an array an object?
35. Write code to print out the values of an array.
36. How does the garbage collector know when to return memory to the heap?
37. Compare and contrast the stack and the heap.
38. How is the import keyword used?
39. What is a package?
40. What is JavaDoc?
41. Is Java pass by value or pass by reference?
42. What does pass by value mean?
43. What does pass by reference mean?
44. What is a NullPointerException?

---
