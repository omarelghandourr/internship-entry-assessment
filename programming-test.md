# Programming Test

This test was composed to create a general overview of your knowledge regarding general programming and how it fits with the needs in our lab. Please try to answer all questions using your own knowledge and in your own words. If you get stuck on one of the exercises, still try to give a short answer.

---

## Exercise 1

### Task
Write a program in the language of your choice where:

1. The iteration number (starting from 1), followed by a random number between 1 and 100, is printed 100 times.
2. After every 5 iterations, write an additional separator (e.g., `---`).
3. Write “Lucky number!” after every random number that is divisible by 7.

> Try to keep the procedure as short as possible.
>PROGRAM-
> import java.util.Random;

public class Luckyprogram
{
    public static void main(String[] args) 
    {
        Random rand = new Random();
        for (int i = 1; i <= 100; i++) 
	{
            int num = rand.nextInt(100) + 1;
            System.out.print(i + ": " + num);
            if (num % 7 == 0) System.out.print(" Lucky number!");
            System.out.println();
        }
    }
}


---

## Exercise 2

### 1. **What is your understanding of the term “Design Patterns”?**  
   Provide a description in your own words.

  > Design patterns are reusable building blocks for solving recurring design problems in object-oriented programming. Instead of reinventing the wheel each time, you apply these patterns to structure your code in a way that is already known to work well.

### 2. **Explain the MVC Pattern**  
   - What does MVC stand for?
   -  >>>MVC stands for Model-View-Controller. It is a design pattern commonly used in software development to separate concerns within an application, especially 
         in user interface-based applications like web or desktop apps.


   - Explain the pattern in detail.
   - >>>  a software architectural design that separates an application into three interconnected components: Model, View, and Controller. This separation helps 
          organize code, promotes scalability, and makes the application easier to maintain and test
     
   - What are some use cases for this framework?
   - >>>Web applications
     >>>Desktop applications
     >>>Mobile applications
     >>>Game development
     >>>Data-driven applications

### 3. **List three other design patterns** 

   -Singleton pattern
   -observer pattern
   -factory method pattern
     
   - Provide names and details for three additional design patterns.
     >> 1. Builder Pattern
           -The Builder Pattern is used to construct a complex object step by step, allowing the creation of different representations using the same construction 
           process.
     >> 2. Decorator Pattern
            -The Decorator Pattern allows you to add new behavior to objects dynamically at runtime without modifying their structure
     >> 3. Strategy Pattern
     >>     -The Strategy Pattern defines a family of algorithms, encapsulates each one, and makes them interchangeable without altering the client using them
   
   - Explain how you have used those patterns in the past and how they have solved your problem

        1. Builder Pattern
        How I Used It:
        In a real estate listing platform, we needed to create House objects with a large number of optional features like garden, garage, swimming pool, solar 
        panels, etc
        
	2.Decorator Pattern
        How I Used It:
        In a text formatting tool, we allowed users to apply formatting options like bold, italic, and underline to text.

        Rather than hardcoding combinations like BoldItalicUnderlineText, I used the Decorator Pattern to wrap base Text objects with formatting decorators 
        dynamically.



   - Use diagrams to explain the design patterns.

---

## Exercise 3

### 1. **Implementation Task**  
   Based on the class diagram below, provide an implementation in any object-oriented programming language of your choice.
   
```mermaid
classDiagram

class A {
	# Name : string
	+ PrintName() void
}

<<abstract>> A

class B {
	- PrintName(message : string) void
}

class C {
	+ PrintName(message : string) void
}

D --|> A
B --|> A
C --|> B


ANSWER PROGRAM:-

// Abstract class A
abstract class A {
    // Protected attribute Name
    protected String Name;

    // Constructor to initialize Name
    public A(String name) {
        this.Name = name;
    }

    // Abstract method PrintName to be implemented by subclasses
    public abstract void PrintName();
}

// Class B extends A
class B extends A {
    public B(String name) {
        super(name);
    }

    // PrintName method with a message parameter
    public void PrintName(String message) {
        System.out.println("B's PrintName: " + message + " " + Name);
    }
}

// Class C extends B
class C extends B {
    public C(String name) {
        super(name);
    }

    // Overriding PrintName method with a message parameter
    @Override
    public void PrintName(String message) {
        System.out.println("C's PrintName: " + message + " " + Name);
    }
}

// Class D extends A
class D extends A {
    public D(String name) {
        super(name);
    }

    // Providing the implementation of PrintName inherited from A
    @Override
    public void PrintName() {
        System.out.println("D's PrintName: " + Name);
    }
}

public class Main {
    public static void main(String[] args) {
        // Create instances of D, B, and C
        D objD = new D("D Object");
        B objB = new B("B Object");
        C objC = new C("C Object");

        // Calling the PrintName methods
        objD.PrintName();  // Prints D's PrintName: D Object
        objB.PrintName("Hello from");  // Prints B's PrintName: Hello from B Object
        objC.PrintName("Hello from");  // Prints C's PrintName: Hello from C Object
    }
}

```


### 2. **Key Questions**  
   - Are you able to directly create a new instance of `ObjectA`? Please explain your answer.
     >>No, you cannot directly create a new instance of ObjectA, ObjectA is an abstract class, meaning it cannot be instantiated directly
     
   - Given an instance of `ObjectC`, are you able to call the method `PrintMessage` defined in `ObjectB`? Please explain your answer.
     >>Yes, you can call the PrintMessage method from an instance of ObjectC, ObjectC extends ObjectB, which means ObjectC inherits all non-private methods from 
     ObjectB, including the PrintMessage method.  
   - Try to explain as many key features of object-oriented programming as you can find in this example.
     >>Abstraction
     >>Inheritance
     >>Polymorphism
     >>Encapsulation
     >>Method Overriding
     >>Constructor Overriding

---

## Exercise 4

### Maintaining and Expanding Software for Component Validation

This exercise focuses on strategies for working with existing code bases and ensuring the software remains maintainable as new features and requirements are introduced.

### 1. **Working with Existing Code**  
- How would you approach understanding and contributing to an existing code base with minimal disruption?
  >>Start by reviewing documentation (if available). This could include README files, architecture diagrams, and developer notes.
  >>Explore the core modules. Focus on understanding the core components and how they interact. Look at critical paths and the main entry points of the application
  >>Run the application and observe its behavior. Understanding the software from a user's perspective helps you grasp the flow of operations and functionality
   
- What practices would you follow to ensure your changes integrate well with the current structure?
  >>Follow existing coding conventions: This includes naming conventions, indentation styles, and other standard practices to maintain consistency.
  >>Use version control effectively: Always create new branches for your changes. Break down large changes into smaller, manageable commits with clear messages
  >>Code reviews: Engage in code reviews with your team to ensure that the integration of changes is smooth and does not introduce unintended side effects



### 2. **Ensuring Maintainability**  
- What techniques would you use to keep the code base clean, modular, and easy to maintain as new features are added?
 >>Modularize the code: Break down large files and classes into smaller, reusable components. Each class or module should have a clear, single responsibility (i.e., follow the Single Responsibility Principle).
 >>Refactor regularly: Don't wait for the code to become a mess before refactoring. If you see any duplication or overly complex logic, refactor it immediately to improve readability and reduce the chances of bugs.
 >>Follow SOLID principles

- How would you handle code documentation and testing to support long-term maintainability?
  >>Write meaningful comments: Focus on explaining the "why" rather than the "what". This can help new contributors understand your design decisions.
  >>Use docstrings or Javadoc-style comments for method and class documentation
  >>Unit tests: Write unit tests for all critical functions and ensure that existing functionality is covered. This helps prevent regressions.
  >>Integration tests: For larger systems, integration tests ensure that various parts of the software interact as expected. These should be used alongside unit 
    tests.

### 3. **Balancing Flexibility and Stability**  
- How would you design or refactor the software to make it flexible for future changes while ensuring the existing functionality remains stable?
  >>Use design patterns
  >>Use interfaces and abstract classes
  >>Keep functionality extensible
- Which design patterns or principles would you apply to achieve this balance
  >>Abstract Factory
  >>Observer Pattern
  >>Strategy Pattern
  >>Decorator Pattern
---
