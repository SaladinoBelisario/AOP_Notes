# **`Aspect-Oriented Programming (AOP) Notes`**

The main objective of the AOP is the separation of functionalities within the:

* On the one hand, common functionalities used throughout the application.

* On the other hand, the features of each model

Each common function will be encapsulated in an entity.

**Key concepts**

* **Aspect:** is a cross-cutting functionality that is going to be implemented in a modular
way and separately from the rest of the system. The most common and simplest example of an
aspect is logging (event logging) within the system, as it necessarily affects all parts of
the system that generate an event.

* **Join point:** is an execution point within the system where an aspect can be connected,
such as a call to a method, the throwing of an exception or the modification of a field. The 
skin code will be inserted into the application execution flow to add its functionality.

* **Advice:** is the implementation of the aspect, that is, it contains the code that implements
the new functionality. They are inserted into the application at the Crossing Points.

* **Pointcut:** defines the Tips that will be applied to each Point of Crossing. It is 
specified by Regular Expressions or by name patterns (of classes, methods or fields), and
even dynamically at runtime according to the value of certain parameters.

* **Introduction:** allows you to add methods or attributes to existing classes. An example 
in which it would be useful is the creation of an Audit Council that maintains the date of
the last modification of an object, by means of a variable and a method setLastModification 
(date), which could be introduced in all classes (or only in some) to provide you with this 
new functionality.

* **Target:** is the advised class, the class that is object of advice. Without AOP, this
class should contain your logic, in addition to the skin logic.

* **Proxy:** is the object created after applying the Advice to the Recipient Object. The rest
of the application will only have to support the Recipient Object (pre-AOP) and not the
Resulting Object (post-AOP).

* **Weaving:** is the process of applying Aspects to Target Objects to create new Resulting
Objects at specified Cross Points. This process can occur throughout the life cycle of the 
Recipient Object:

  - _Compile-Time Aspects_, which requires a special compiler.
  
  - _Loading-Time Aspects_, Aspects are implemented when the Target Object is loaded. It 
  requires a special ClassLoader.
  
  - _Execution-Time Aspects_.


**Benefits of AOP**

* Code for Aspect is defined in a single class:
  - Much better than being scattered everywhere
  - Promotes code reuse and easier to change
  
* Business code in your application is cleaner:
  - Only applies to business functionality
  - Reduces the code complexity
  
**Disadvantages:**

* Too many aspects and the app flow is hard to follow.
* Minor performance cost for aspect execution (run-time weaving).

## Advice types

* **Before advice:** run before the method. 
* **After finally advice:** run after the method (finally). 
* **After returning advice:** run after the method (success execution).
* **After throwing advice:** run after the method (if exception is thrown). 
* **Around advice:** run before and after the method. 

## AOP in Java

**Spring AOP:**

* Advantages:
    - Simpler to use than AspectJ
    - Uses proxy pattern
    - Can migrate to AspectJ when using _@Aspect_ annotation

* Disadvantages:
    - Only support method-level joint points
    - Can only apply aspects to beans created by Spring app context
    - Minor performance cost for aspect execution (run-time weaving)

**AspectJ:**

* Advantages:
  - Supports all joint points
  - Works with any POJO, not just beans from app context
  - Faster than Spring AOP
  - Complete AOP support

* Disadvantages:
  - Compile-time weaving requires extra compilation step
  - AspectJ pointcut syntax can become complex