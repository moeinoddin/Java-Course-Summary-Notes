---
title: "Inheritance and Polymorphism"
tags: ""
---
subClass:

> inherits from superClasses, also has additional fields and methods  
> in UML Class-Diagram a white arrow from subClass to superClass( screenshot exists )  
> similar to 'isa' in ER diagrams of database
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

subclass constructor:  
use **_super( )_** for superClass fields

```java
public class SubClass extends superClass{
	additional fields
    additional methods 
}

public subClass(superClassField1,superClassField2, subClassFields ... ){
	super(superClassField1,superClassField2); //must be first statement
    
    this.subClassFields = subClassFields;
    ...
}
```

### some notes

-   all methods and fields are inherited, it is impossible to remove them  
    if required, remove from superClass and create another class in the hierarchy for the other subClasses of superClass

-   collections can have instances of a class and all subClasses

```java
public class Post;
public class MessagePost extends Post;
public class PhotoPost extends Post;

private ArrayList<Post> posts;
public void addPost(Post postObj){
	posts.add( postObj ) //Post and all other subClass objects	
}
	//in another class / main:
	clientClass.addPost( messagePostObj );
	clientClass.addPost( photoPostObj );
```

-   this is also called **_substitution_**
    > using objects of subclasses instead of superclass as parameters to methods
-   a forEach is also available:

```java
public class newsField{
    private ArrayList<Post> posts;
	
    public displayPosts(){
        for(post: posts) //doesn't matter if its a messagePostObj or photoPostObj
            post.display()
    }

}
```

-   subclass objects may be assigned to superclass variables

```java
public class Vehicle{	}
public class Car extends Vehivle{	}
public class Bicycle extends Vehicle{	}

Vehicle v1 = new Vehicle();
Vehicle v2 = new Car();		//an object of a subclass for a superclass reference
Vehicle v3 = new Bicycle();	//an object of a subclass for a superclass reference

'note' : because bicycle and car 'isa' vehicle
'note' : only methods of the superClass are available not subclasses
```

-   object variables are polymorphic, they can have reference to objects of different types  
    either the defined type or **_subclasses_** of the defined type which **_inherit_** from it  

-   casting  
    we can assign subtype to supertype  
    but we can't assign supertype to subtype

```java
Vehicle V;
Car c = new Car();
v = c;	//correct
c = v;	//compile time eroor

'casting fixes this':
 c = (Car) v;
//only ok if the vehicle really is a car ( and not a bicycle ).
/*otherwise'*/: throws ClassCastException at runtime
```

-   all classes inherit from object ( this is used as a parameter in overriding equals() and hashcode() methods )

-   collections are also polymorphic, they can accept and return an **_ObjectObj_** . - usually avoided

```java
ArrayList list = new ArrayList<>();
```

* * *

-   inheritance is a one way street, methods of a superClass  
    cannot utilize fields or any other characteristics of a subclass.
    > methods of superClass can only use common things

-   if subClass methods need to use superClass fields, the fields  
    should be declared as **_protected_**, private fields are not accessible.

-   keeping private is still recommended, use **_protected accessors and mutators_**

### static type

> the declared type of the varialble, left side of declaration  
> [ COMPILER CHECK ]

### dynamic type

> the type of the object that is being referred to at the moment
> [ RUNTIME CHECK ]  

-   use the **_instanceof operator_** to check for the dynamic type of a variable  
    -can be used prior to casting in if-statements  
    -recovers **'lost'** type information

```java
//static  dynamic
Car c1 = new Car()		
Vehicle c2 = new Car()	
    
if(c2 instanceof Car){
 	Car cTemp = (Car) c2
    //TODO codes
}
```

### method dispatch/lookup

> when calling a method of an object, the inheritance hierarchy  
> is ascended until a match is found, overriden methods in a subClass  
> are  seen before superClass and thus executed [obj instanceof subClass ]  
> start of method lookup is the dynamic type not static type

note: the method must be declared in superClass as well for the code to compile

> superClass methods can be called from the methods that override them
>
> ```java
> super.method();
> ```

solutions for superClass using subClass:

1.  using the instanceof operator -- duplicate code problem  
2.  overriding methods  -- satisfies static and dynamic type check [ at runtime dynamic type method is used ] 

* * *

-   if subClasses do not have similarities in their   methods, it is best  
    to define an abstract method, class must also be defined as abstract

```java
public abstract className{
	/**
	*javadoc is still required
	*/
	public abstract void() methodName(){
		//no body -- overriden
	}
}

'note': if a Class contains abstract methods, objects cannot be created from it.
'note': Classes with abstract methods must be defined as: public abstract className{ } 
'note': abstract classes might be declared without abstract methods --> objects still cannot be created from the class
```

### multiple inheritance  is not available for classes

-   a diamond problem might occur [ feature removed in java ]  
    both superClasses have the same name, without overriding in subClass, which to execute?

-   instead interfaces are used. multiple interface implementation is available

## interface

does not contain any implementation in it at all

```java
public interface actor{
    
    
}
```

all methods are public and abstract [ keywords may be ommited ]  
all fields are public, static and final [ keywords may be ommited ]

-   methods in interface contain no methods bodies. [end with a ; without curly braces {} ]

-   when a class implements an interface, all the methods must be given a body  
    ( left blank if the method is to be left abstract and overriden in subClasses )

-   abstract classes are allowed not to define method implementation of interfaces

-   methods of interfaces can have a default implementation from java 8.0+

## important note

-   an object of a concrete class, might be assigned to a variable of an implemented **_interface_** and or **_superClass_**  

implementing classes are subTypes of interfaces

```java
List myList;

if(){
	myList = new ArrayList<String>
}
else{
 	myList = new LinkedList<Integer>   
}
    
```
