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

class:  

> the classes objects come from, are essentially reusable software components.  
> they are the blueprints which objects can be instantiated from.

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

state - attribute - method:

> Attributes are the characteristics
> that define an object  
> A method is a self-contained block of program code that carries out some action  
> values of the properties of an object are referred to as the object’s state

generic classes:  

> we give the type of data that we want to use. the class becomes tuned for that type. - ex)  
> ArrayList&lt;type) varName = new ArrayList&lt;type);  
> Iterator&lt;type) iteratorName = collectionObject.iterator()

dsa
