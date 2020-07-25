---
title: "typical definititions of programming"
tags: ""
---
vocabulary:  
syntax:  

>  All languages have a specific, limited vocabulary (the language’s keywords)  
> and a specific set of rules for using that vocabulary 

Algorithm:  

> procedure for solving a problem in terms of the actions to execute and the order in which these actions execute

procedure:

> For convenience, the individual operations used in a computer program are often grouped into logical units called procedures.  
> Procedures are also called modules, methods, functions, and subroutines

Parsing

> it is the process the compiler uses to divide your
> source code  
> into meaningful portions. one aspect are > the curly braces in the program : { } 

clean build:

> Once in a while, when you make a change to a Java class and then recompile and execute it,  
> the old version still runs. The simplest solution is to delete the .class file and compile again.  
> Programmers call this creating a
> clean build.

transfer of control:  

> specify that the next statement to execute is not
> necessarily the next one in sequence.

control statements:  

> **all programs can be written in terms of only three control structures:** 
>
> > the sequence structure - execute in order  
> > the selection structure - if , if-else , switch  
> > the repetition structure - while , do-while , for , forEach  
> > we’ll refer to them as “control statements.”

sentinel value:

> a special value in loops to indicate “end of data entry”

access modifier

> in OOP or specifically java, it determines to what extent other classes can acces the class's methods and fields(fields always private).
> detailed list exists in the notes on classes and methods

class:  

> the classes objects come from, are essentially reusable software components.  
> they are the blueprints which objects can be instantiated from.

client class:

> a class that utilizes other classes in its code  
> in UML Class-Diagrams an arrow point from the class to the used class  
> a black arrow

subClass:

> inherits from superClasses, in UML Class-Diagram  
> a white arrow from subClass to superClass
>
> ```java
> public class SubClass extends superClass{
> 	additional fields
>     additional methods 
> }
> ```
>
> also consider **_inheritance hierarchies_**

superClass

> a class that holds common fields and methods of its subclasses

static keyWord:  

> A static method is special, because you can call it
> without first creating an object of the class in which the method is declared

reference type:

> store the addresses of objects in the computer’s memory. Such a variable is said to refer to an object in the program  
> Reference-type instance variables, if not explicitly initialized, are initialized
> by default to the value null—which represents a “reference to nothing.”

## Understanding OOP requires grasping three basic concepts:

### Encapsulation:

In object-oriented classes, attributes and methods are encapsulated into objects.  

> Encapsulation is the enclosure of data and methods within an object and allows  
> you to treat all of an object’s methods and data as a single entity.  
>
> concealment from outside sources.  
> Concealing data is sometimes called information hiding,and  
> concealing how methods work is implementation hiding;  

### Inheritance:

> the ability to create
> classes that share the attributes and methods of existing classes, but with more specific features.  
> you need to be concerned only with the attributes and methods that are “new”

### Polymorphism:

> the feature of languages that allows the
> same word or symbol to be interpreted correctly  
> in different situations based on the context.  

> object variables are polymorphic, they can have reference to objects of different types
> either the defined type or **_subclasses_** of the defined type which **_inherit_** from it

### static type

> the declared type of the varialble, left side of declaration  
> [ COMPILER CHECK ]  

### dynamic type

> the type of the object that is being referred to at the moment
> [ RUNTIME CHECK ]  

-   use the 'instanceof' operator to check for the dynamic type of a variable - can be used prior to casting in if-statements

### method dispatch/lookup

>

* * *

state - attribute - method:

> Attributes are the characteristics
> that define an object  
> A method is a self-contained block of program code that carries out some action  
>
> > mutators: changes the fields of the object - e.g. setters  
> > accessors: provide info about object state - e.g. getters

> values of the properties of an object are referred to as the object’s state

generic classes:  

> we give the type of data that we want to use. the class becomes tuned for that type. - ex)  
> ArrayList&lt;type) varName = new ArrayList&lt;type);  
> Iterator&lt;type) iteratorName = collectionObject.iterator()

Interface:

> it allows us to use other programmers codes,libraries, ...
> without knowing how it is implemented, like how we have used various classes supported by the java library without even knowing how they work on the inside. we just need an INTERFACE to use it in our own programs

API = Application programming interface

> interface description and documentation for all library classes

immutable Class / object

> once created, the memory in heap of it cannot be altered. must allocate new memory to it if need to change
>
> this is done by setting fields to private and not declaring Setters

kjkj
