---
title: "Code-set-note 1"
tags: ""
---
## type-wrapper classes

these exist for all primitive type, so they can be treated as objects and classes  

    useful for creating ArrayLists and other collections from 'all primitive types'

### Integer

```java
Integer.parseInt(String str)

Integer five = new Integer(5); *:heap and stack
Integer five = 5 // constructors are called automatically
int x = five.intValue();
Integer six = five + 1; // intValue() and Integer() called automatically

*: these operations are also called boxing and unboxing
```

### Double

```java
Double.parseDouble(String str)
```

### String - not a wrapper

```java
String.valueof( Object o)
```

covered in the notes on strings

## the Random class

a class used to create Random thing

```java
import java.util.Date
import java.util.Random()
private Random r = new Random(long seed);
private Random r = new Random(new Date().getTime());
r.setSeed.(long seed);
r.nextInt(sup) 			 	// result is in [0,sup)
r.nextInt(max+1)			// result is in [0,max]
min + r.nextInt(max-min+1) 	// result is in [min,max]
```
