---
title: "Conventions and simple stuff"
tags: ""
---
1.  package names start with lowerCase
2.  class names start with upperCase
3.  method names start with lowerCase
4.  constructor methods start with upperCase, to have the same name as className
5.  variable names start with lowerCase
6.  named constants conventionally are given identifiersusing all uppercase letters, using underscores as needed to separate words.
7.  object names start with lowercase
8.  reserved keys start in lower case.{ public, class, private, ... }
9.  ** AlwaysUseCamelCase **

A variable name in Java can only contain letters, numbers, underscores (\_) or the dollar sign ($)

### some notes:

-   put a space on both sides of all operators

-   using return in the middle of the program to end it

-   in printf: instead of using the escape sequence \\n,  we used the  
    **%n** format specifier which is a line separator     that’s portable across operating systems

-   The precedence of the conditional operator **( ? : )** is low, so the entire conditional expression is normally placed in parentheses

-   primitive types declared outside of a method as **_instance variables_** of a class are automatically assigned default values unless explicitly initialized. 
    >  Instance variables of types char, byte, short, int, long, float and double are all given the value 0 by default.
    >
    > type boolean are given the value false by default.
    >
    > Reference-type instance variables are initialized by default to the value **null.**

### imports

Any import statement you use must be placed outside of any class written in a file.

```java
import java.util.Scanner
import java.util.Arrays
import java.math.* --- very limited number of classes within the package
// java.lang.Math is already imported, no need for import.
// note difference: Math & math.

import javax.swing.JOptionPane; - used in GUI application

import java.util.InputMismatchException;

```

Variables or methods declared with access modifier **private** are accessible  
only to methods of the class in which they’re declared.  
So, the variable name can be used only in each **Account object’s methods**

If a method contains a "local variable" with the same name as an "instance variable" that method’s body will  refer to the **local variable** rather than the instance variable. In this case, the local variable is  said to **_shadow_** the instance variable in the method’s body. The method’s body can use the keyword `this` to refer to the shadowed instance variable explicitly
