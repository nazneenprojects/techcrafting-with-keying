---

layout: single
title:  Deep Dive into Design Patterns in Python""
date:   2024-10-22 19:30:00 +0000
published: true

---
# Design Patterns

---
### Helps in :
1. Avoid Duplicating efforts
2. Improve quality
3. Lowers cost
---
---
### Characteristics :
1. Language Neutral
2. Dynamic
3. Intentionally Incomplete
---

### Inheritance : 
Estabish relation between child and classes as a Parent and child
### Polymorphism :
Relies on Inheritance
Polymorphism relies on inheritance and it allows us to instantiate a child class and treat it as the same type as its parent. In other words, polymorphism enables a parent class to be a placeholder for its child classes.

There are three different types of design patterns: creational, structural, and behavioral patterns. 

## Creational :
Creational design patterns are for building objects systematically. The main benefit lies in their flexibility, especially in the area of modifiability and scalability. Here is an example of using creational patterns to make code changes more elegant and effective. Let's say that you're developing software for a pet shop. If you're short-sighted, you may create individual classes for each pet the shop offers as you go. This approach is not scalable. A better option is to have a general class called Pet that contains all the common properties across the pets being handled now and to be added in the future. These common properties include: pet type, such as dog or cat, their name, age, et cetera. When there is a new pet type to be introduced next time, all you have to do is to write a new child class that inherits from the Pet class with minimal new properties and methods. This way, your code stays less redundant, and there are no major changes to the rest of the code base. Creational patterns also allow adding new subtypes of objects from the same class at runtime. Using the Pet class makes it possible for us to use a common interface that can handle any of its subtypes, such as dog or cat. Let's say we have a method called printPetName that prints a pet's name. We can create any objects of various pet types and pass them to the printPetName method because it accepts the Pet class instead of a specific pet type, like dog or cat. 

## Structural :
We use structural patterns to establish repeatable relationships between software components in particular configurations. The goal here is to satisfy specific functional or non-functional requirements with flexibility and efficiency. Functional requirements refer to what software does. Drawing a circle on a screen is a functional requirement. On the other hand, non-functional requirements also known as quality attributes are how well software completes its job. The question of how fast or slow software functions belongs to the non-functional domain. If your application needs one minute to draw a circle but users want one millisecond completion time, the software does not meet its non-functional requirements. In addition to speed, there are other non-functional requirements such as security, usability and modifiability. Different requirements lead to various structures implemented in structural patterns just as architects use different designs for houses to meet different needs.

## Behavioral :
Behavioral patterns are the best practices of how you make your objects interact with each other. The focus here is defining the protocols between these objects when trying to work together to accomplish a common goal. You may want to write code processing an online banking transaction. The program should be able to handle tasks like depositing or withdrawing money. It'll be ideal if you have ways to compose individual reusable actions into a transaction, or cancel it altogether. Let's consider withdrawing money. The first action is to identify a user. Depending on the mode of identification, appropriate actions to verify the user's identity ensues. Once the user indicates the amount to withdraw from which account, the next action is to check if there is enough balance to continue on with the next steps. At this time, the system may cancel the entire transaction due to the insufficient fund in the account. You can already see so many moving parts involved here, namely the authentication mechanism, the subsystem that checks the user balance, et cetera, which requires the careful orchestration of the actions, including close monitoring and backtracking. Luckily, we have behavioral patterns at our disposal to address the potential problems that could arise in these transaction-heavy scenarios. 


### Object-oriented design concepts are foundations for developing design patterns. In the creation of patterns, polymorphism is often in use. Structural patterns take advantage of inheritance a lot. Behavioral patterns heavily use metals and their signatures through interfaces. Interfaces are at work across all the different types of design patterns. Knowing the design pattern types is helpful, especially because it allows to locate the needed design patterns very quickly.


### Design patterns are low level and concrete. They are at the class level and address how classes are instantiated, structured, and orchestrated. On the other hand, architectural patterns are high level and abstract. They're at the module level and address global concerns such as security, performance, and maintainability, et cetera. 

### Builder :
Builder is a creational design pattern. It addresses an Anti-pattern called telescoping constructor. An Anti-pattern is the opposite of the best programming practice and what we want to avoid. The telescoping constructor Anti-pattern occurs when a software developer attempts to build a complex object using an excessive number of constructors. Think of a scenario in which you're trying to build a car. This test requires various car parts to be first constructed individually, and then assembled. The Builder Pattern brings order to this chaotic process to remove unnecessary complexity as much as possible. It partitions the process of building a complex object into four different roles. The first role is a director in charge of actually building a product. The second role provides all the necessary interfaces required in building an object. We call this one an Abstract builder because there'll be a ConcreteBuilder inheriting from it. The ConcreteBuilder class inherits from the Abstract builder class and actually implements the details of the interfaces of the Abstract builder class for the specific type of a product. The product role represents an object being built. The Builder Pattern does not rely on polymorphism. The focus of the Builder Pattern is on reducing the complexity of building an elaborate object through a divide and conquer strategy.

      



