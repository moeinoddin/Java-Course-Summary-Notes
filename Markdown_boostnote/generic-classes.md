---
title: "Generic classes"
tags: ""
---
## writing classes and methods, able to work with different Types

-   generics enable us to specify with a method or class, **a set of related types**

-   a general structure can be defined first,  
    details of the using Types will be assigned later.
    > similar concept to static and dynamic types  
    > general implementation, specific implementation

-   generic classes and methods are also known as  
    **parameterized** classes and methods

* * *

### generic classes

```java
public class ClassName< T , E >{
    //sample code
    private T t;
    
    public void set(T t){
    	this.t = t;
    }
    
    public T get(){
        return t
    }
    
}
```

### generic  methods

compiler handles each method call seperately

```java
type parameter section, precedes the return type

public static <E> void method( E inputParam ){
	//statements based on E
}
// E can also be the return type
```

* * *

### Bounded Type Parameteres

it is possible to restrict the kind of types allowed to be passed

-   to do so, use the superClass of the valid types

classes

```java
public class ClassName < A extends superClass>{
	//statements based on A
	//all methods of the superClass are available
}
```

methods

```java
public static <T extends superClass> T methodName()
public static <T extends GenericClass<T> > T methodName(){
	//statements based on A
	//all methods of the superClass are available
}     
```

* * *

interface comparable

```java
public class className implements Comparable{
    @Override
    public int compareTo(){
		//compare
    }    
}
```
