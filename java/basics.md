## Table of Contents
- [Table of Contents](#table-of-contents)
- [1. Syntax Overview](#1-syntax-overview)
- [2. Printing](#2-printing)
- [3. For Loop](#3-for-loop)
- [4. Foreach Loop](#4-foreach-loop)
- [5. Conditions](#5-conditions)
- [6. Basic Methods](#6-basic-methods)
- [7. Exception Handling](#7-exception-handling)
---

## 1. Syntax Overview

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Java 17!");
    }
}
```

---

## 2. Printing

```java
System.out.println("This prints a line");
System.out.print("This prints without a newline");
System.out.printf("Formatted output: %d, %s%n", 42, "Java");
```

- %d decimal integer
- %.2f floating-point
- %c character %C CHARACTER
- %s string %S STRING
- %h hashcode - reference
- %n newline equiv of \n 

---

## 3. For Loop

```java
for (int i = 0; i < 5; i++) {
    System.out.println("Iteration: " + i);
}
```

---

## 4. Foreach Loop

```java
List<String> items = List.of("Apple", "Banana", "Cherry");
for (String item : items) {
    System.out.println(item);
}
```

---

## 5. Conditions

```java
int number = 10;
if (number > 5) {
    System.out.println("Number is greater than 5");
} else {
    System.out.println("Number is 5 or less");
}

switch(number) {
  case 1:
    break;
  case 2:
    break;
  default:
}

```

---

## 6. Basic Methods

```java
public int add(int a, int b) {
    return a + b;
}
```

---

## 7. Exception Handling

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
} finally {
    System.out.println("This block runs no matter what");
}
```

