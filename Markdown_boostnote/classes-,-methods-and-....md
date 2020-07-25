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
default(package-private): classes within the same Package have access to it
```

In Java, the reserved keyword static means that a method is accessible and usable even though no objects of the class exist

-   both methods and fields can have static value, thus exist whether objects have been created or not
-   static values are shared across all object, it is better to say it is a **_class field_** rather than a field
-   values can be static and final at the same time

```java
private int salary; 
private static int count = 0; //or in constructor
private final int nationalID;
private final static double GRAVITY_ACCELERATION = -9.8;
```

Note: Strings, Arrays, Objects and ... are **_reference types_**, they refer to memory where data is stored.  

-   Note the following:

```java
className obj1 = new className( args1 );
className obj2 = new className( args2 );
instead of className it could have been: 'Array, String, ... '

changing where the object 'refers' to:
obj1 = new className(args3)
obj1 = classNameArray[i];
obj1 = obj2;

obj1 == obj2
obj1.equals(obj2);
This only checks if they refer to the same object [reference] or not.
it does not compare their values.

'note': in previous version of java,
the equals method was used to compare values of objects not references, and was thus different from ==
'although' this method can still be overriden in newer version to do the same thing.
it has already been 'overridden' For the String Class.

```

## constructors

> public  
> no return type, not even void  
> same name as the class --> Start with uppercase

-   can be overloaded with different argument streams
-   other useful method for overloading

```java
using this() -- a super constructor with all possible fields

in other constructors-->
    1. obtain a fraction of those
	2. use constants or other expression For other fields
    public ClassName(int x, int y){}
    public ClassName(int x){
    	this(int x ,3 );
    }
"note" : can be used so that not all constructors need to be fixed later on

```

## methods

**method header -  usually in order:**

1.  synchronized
2.  final
3.  access ( public, "", protected, private )
4.  static
5.  return type [ must be here ]
6.  method name
7.  parameters

```java
synchronized final protected static double method(double x){
	
    return x + 0.02;   
}
```

-   synchronized: only one thread at a time - others are blocked and must wait
-   final: cannot be overriden in subclasses

### method overloading

-   achieved by using different parameter sets
-   the return type of different parameter sets can be different

```java
public int addToVar1(int x) {
		return var1 + x;
	}
	
public double addToVar1(double x) {
		return var1 + x * 10;
	}
```
