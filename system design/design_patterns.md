# Design Patterns

## Introduction
In software engineering, a software design pattern or design pattern is a general, reusable solution to a commonly occurring problem in many contexts in software design.[1] A design pattern is not a rigid structure that can be transplanted directly into source code. Rather, it is a description or a template for solving a particular type of problem that can be deployed in many different situations. Design patterns can be viewed as formalized best practices that the programmer may use to solve common problems when designing a software application or system. 


## Types of Design Patterns
Design patterns can be organized into groups based on what kind of problem they solve. 
* Creational patterns create objects. 
* Structural patterns organize classes and objects to form larger structures that provide new functionality. 
* Behavioral patterns provide communication between objects and realizing these patterns.


### Strategy pattern
In computer programming, the strategy pattern (also known as the policy pattern) is a behavioral software design pattern that enables selecting an algorithm at runtime. Instead of implementing a single algorithm directly, code receives runtime instructions as to which in a family of algorithms to use.

![alt text](image-7.png)
A sample UML class and sequence diagram for the Strategy design pattern.

In the above UML class diagram, the Context class does not implement an algorithm directly. Instead, Context refers to the Strategy interface for performing an algorithm (strategy.algorithm()), which makes Context independent of how an algorithm is implemented. The Strategy1 and Strategy2 classes implement the Strategy interface, that is, implement (encapsulate) an algorithm.
The UML sequence diagram shows the runtime interactions: The Context object delegates an algorithm to different Strategy objects. First, Context calls algorithm() on a Strategy1 object, which performs the algorithm and returns the result to Context. Thereafter, Context changes its strategy and calls algorithm() on a Strategy2 object, which performs the algorithm and returns the result to Context. 

