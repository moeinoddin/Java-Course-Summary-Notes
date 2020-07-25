---
title: "Java Primary aspects"
tags: ""
---
A great wealth of helpful material exists at the [Java Web site - oracle](www.oracle.com/technetwork/java/index.html)  
Of particular value is the Java application programming interface, more commonly referred to as the Java API. The Java API is also called the Java class library; it contains information about how to use every prewritten Java class.

One of the main features of Java is that it is platform independent. This means that a program written in Java can be executed on any operating system (such as Windows, Mac or Linux). Every computer platform has its own machine code instruction set. Hence, machine code that is compiled for one platform will not work on another platform

When a user wants to run a Java program, a program inside the user’s computer (known as the Java Virtual Machine or JVM) converts this bytecode into machine code for the specific platform that the user uses. as long as the computer running the Java program has JVM installed. there are different versions for different computer platforms.

WORA: Write Once Run Anywhere

Object oriented programming is an approach to programming that breaks a programming problem into objects that interact with each other.

JDK stands for Java Development Kit and is a free kit provided by Oracle that contains a number of tools to help us develop Java applications:

1.  a compiler: to compile our written code into bytecode (javac.exe)
2.  an archiver: to package and distribute our Java files (jar.exe)
3.  a documentation generator: to generate HTML documentation from our Java code (javadoc.exe).

JDK also includes the Java Runtime Environment (JRE). JRE contains the JVM mentioned in Chapter 1 and the resources that JVM needs in order to run Java programs. If you are only interested in running Java programs, all you need is the JRE.

A package is simply a grouping of related classes and interfaces.

    javac _.java  
    The asterisk ( _ ) in \*.java indicates that all files in the current directory ending with the
    filename extension “.java” should be compiled

You can write two kinds of programs using Java:

-   **Applets** are programs that are embedded in a Web page.  

-   **Java applications** that are stand-alone programs.  
    Java applications can be further subdivided
    into:  
    > 1.  console applications, which support character or text output to a computer screen.  
    > 2.  windowed applications, which create a GUI with elements such as menus, toolbars, and dialog boxes.  

### memory regions in java

static data

> for variables that are neither created or destroyed throughout the program, like name constants and other class variables(static fields) 

heap

> used when creating objects, memory is allocated from the heap

stack

> used to store local variables of methods
> a new stackframe is created when calling a method

    remember in heap-stack diagrams:
    heap --> new objects are created, store here
    stack --> reference to ojects
    **: different usage might cause some things to go 		  to stack form heap
    ***: all down to new objects

-   in classical architectures, heap and stack grow from opposite size to maximize memory usage
-   in heap-stack trace's we also need to consider an overhead memory to define the start of objects(in heap) and start of methods(in stack)
-   heap starts at 1000 and stack at FFFC. each memory size is 4bytes. thus the above numbers change by 4.  
    all fields, local var's,references and etc take 4bytes
-   for primitive types we do not show any allocated memory, because they do not need a reference in stack to heap. calculate outside of both(not really), and then store in heap.

sad
