---
title: "Developing note set1"
tags: ""
---
-   Technique in constructors: Use blank for null arguments. 

```java
public ContactDetails(String name, String phone, String address)
    {
        // Use blank strings if any of the arguments is null.
        if(name == null) {
            name = "";
        }
        if(phone == null) {
            phone = "";
        }
	}
```

-   throwing Exceptions can also be used to **prevent object creation** withing constructors

```java
public TestClass(int var,String s) {
		this.var = var;
		if( s== null || s.equals("") )
			throw new IllegalArgumentException("s cannot be null");
		this.s = s;
	}
```

to obtain non-endin input from user

```java
// Use CTRL+D on UNIX or CTRL+Z on Windows to end the loop
System.out.println("Enter: first name,  last name,  student ID,  grade");

while (input.hasNext()) {
    //use input
}
```
