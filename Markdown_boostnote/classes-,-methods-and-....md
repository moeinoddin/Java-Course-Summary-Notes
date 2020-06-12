---
title: "Classes , methods and ..."
tags: ""
---
you must save the class in a file with exactly the same name and a ' .java ' extension.

An access specifier defines the circumstances under which a class  
can be accessed and the other classes that have the right to use a class:

```java
public: all classes can access it
protected: only classes and its own subclasses can access
private: only objects of the same Class have access
```

In Java, the reserved keyword static means that a method is accessible and usable even though no objects of the class exist.

Note: Strings, Arrays, Objects and ... are **_reference types_**, they refer to memory where data is stored.  

-   Note the following:

```java
className obj1 = new className( args1 );
className obj2 = new className( args2 );
instead of className it could have been: 'Array, String, ... '

changin where the object 'refers' to:
obj1 = new className(args3)
obj1 = classNameArray[i];
obj1 = obj2;

obj1 == obj2
obj1.equals(obj2);
This only checks if they refer to the same object [reference] or not.
it does not compare their values.




```
