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


