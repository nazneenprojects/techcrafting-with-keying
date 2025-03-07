---
layout: single
title:  Algorithm Complexity
date:   2025-03-07 15:35:00 +0100
published: false
---


# Algorithm Complexity

## Prerequisites : Logarithms

Important Formula : A logarithm is the inverse of an exponential function, where the logarithm of a number is the exponent to which a base is raised to produce that number. 

```
If we have an equation in exponential form:

a^x = y

The equivalent logarithmic form is:

log_a(y) = x

```


Properties of Logarithms with Examples:

```
Product Rule: log_a(x×y) = log_a(x) + log_a(y)
Example: log_10(1000) = log_10(10×100) = log_10(10) + log_10(100) = 1 + 2 = 3
Quotient Rule: log_a(x/y) = log_a(x) - log_a(y)
Example: log_2(16/4) = log_2(16) - log_2(4) = 4 - 2 = 2
Power Rule: log_a(x^n) = n × log_a(x)
Example: log_10(1000) = log_10(10^3) = 3 × log_10(10) = 3 × 1 = 3

```

Types of Logarithms with Examples

```
Natural Logarithms (base e)
Written as ln(x) or log_e(x)
Example: ln(e^2) = 2

Common Logarithms (base 10)
Written as log(x) or log_10(x)
Example: log(1000) = 3

Change of Base Formula
log_a(x) = log_b(x) / log_b(a)
Example: To find log_2(16) using natural logarithms:
log_2(16) = ln(16) / ln(2) = 2.77 / 0.693 = 4

Graphing Logarithms
The logarithmic function y = log_a(x) is the reflection of y = a^x across the line y = x.

Graphing Logarithms
The logarithmic function y = log_a(x) is the reflection of y = a^x across the line y = x.
Key characteristics:
Domain: x > 0 (logarithms of zero or negative numbers are undefined)
Vertical asymptote at x = 0
If a > 1, the function increases slowly as x increases
If 0 < a < 1, the function decreases as x increases
```

![image](https://github.com/user-attachments/assets/8f0f70ef-b7e7-4bca-ba07-cda671b264ca)

![image](https://github.com/user-attachments/assets/7d8dedeb-b4bb-43be-8974-4cf10d0ad7bd)


# Big O Notation

Big O notation tells you how fast an algorithm is. For example, suppose you have a list of size n. Simple search needs to check each element, so it will take n operations. The run time in big O notation is O(n). Where are the seconds? There are none—big O doesn’t tell you the speed in seconds. Big O notation lets you compare the number of operations. It tells you how fast the algorithm grows. O(log n)

Big O establishes a worst-case run time. 
Run time complexity types:

1. Worst Case
2. Average Case
3. Best Case

Some common big O run times
Here are five big O run times  sorted from fastest to slowest:

O(log n), also known as log time. Example: binary search.

O(n), also known as linear time. Example: simple search.

O(n * log n). Example: a fast sorting algorithm, like quicksort 

O(n2). Example: a slow sorting algorithm, like selection sort

O(n!). Example: a really slow algorithm, like the traveling salesperson 



Algorithm speed isn’t measured in seconds but in growth of the number of operations.

Instead of seconds, we talk about how quickly the run time of an algorithm increases as the size of the input increases.

Run time of algorithms is expressed in big O notation.

O(log n) is faster than O(n), and it gets a lot faster as the list of items you’re searching grows.
