---
title: "primary developing technics"
tags: ""
---
comments and overall structure

```java
/** used for blue comments, javadoc */
/*  used for multi comment lines*/
//  single line comment
package packageName;

import java.util.Scanner; ...

public class ClassName{
	public static void main(String[] args){
    	Code to execute
    }
}
```

Javadoc comments are a special case of block comments called documentation comments. they are used to automatically generate nicely formatted program
documentation with a program named javadoc.
The Java Development Kit (JDK) includes the javadoc tool, which you can use when writing programs in Java.
The tool produces HTML pages that describe classes and their contents:

```java
javadoc: //for public members only
/**
* Description of the following class/method/field
* @Author - for class only
* @version - typically for class
* 
* {@inheritDoc} - for inheritance & overriding
* @param
* @returns
* @throws ExceptionNameType reason
```

primitive data types:

1.  byte: -128 to 127 (used if concerned with storage)
2.  short: 2bytes: -32768 to 32767
3.  int: 4bytes: -2^31 to 2^31-1
4.  long: 8bytes: -2^63 to 2^63-1 (with **L suffix**: ###L)


1.  float: 4bytes : -3.40282347x10^38 to +, [ float has 7 decimal precision ] \( with **F suffix**: ###F )
2.  double: 8bytes : 1.79769313486231570 x 10^308 to + [ double has 15 decimal precision]

### the use of suffixes : { ###L , ###F } might not be required in some IDE's.

1.  char: 2bytes: a single character  
    it can also be an escape character: '\\t' '\\n' ....
2.  boolean: true / false


    	7 / 2.0 = 3.5;

named constants: A named constant can be assigned a value only once, and then it cannot be changed later
in the program, whether initialized or obtained through other means.

```java
final String MY_ADDRESS; obtained later in program
final int DAYS_IN_WEEK = 7;
final double PI = 3.14;

CAPS_CASE

if the named constant is a private field in a class, it can be given value within constructors,  
it is recommended to initilize their value upon construction or with default value after declaring the variable.
```

If we want to convert a smaller data type into a larger data type, we do not need to do anything explicitly. However, if we want to assign a **larger data type to a smaller data type**, we need to indicate it explicitly using a pair of parenthesis.

```java
int x = (int) 20.9
this is called casting !!
```

Narrowing conversion is not safe and should be avoided unless absolutely necessary.  
This is because narrowing conversion can result in a loss of data.

**some notes about output and input:**

```java
System.out.println("you don't need \ to display ', but you need it for \" ");

System.out.printf(" number is %,8.2f",12.4);\\"   12.40"

comma(,)--> seperating by thousands with ','
3 spaces in front of the number, giving us a
total width of 8 including the decimal point

out is an object that is a property of the System Class that refers to the standard
output device for a system, normally the monitor.
The out object itself is an instance of the PrintStream class,
which contains several methods, including println().
  
%b--> boolean format specifier in printf.
```

```java
import java.util.Scanner / *

Scanner input = new Scanner(System.in);
	input.nextDouble();
    input.nextInt(); 
    input.nextLine(); "until the first \n" //Retrieves the next line of data and returns it as a String
    input.next(); "until next whitespace" //Retrieves the next complete token as a String
    input.nextShort();
    input.nextByte();
    input.nextFloat(); // no need to type F in the end
    input.nextLong();  // no need to type L in the end

    input.close()

Each retrieved value is a 'token', which is a set of
characters that is separated from the next set by whitespace
```

The Scanner methods next(), nextInt(), and nextDouble() retrieve the next token in  
the buffer up to the next 'whitespace', which might be a space, tab, or Enter key.  
The nextLine() method reads all data up to the 'Enter key character'.

The solution to the problem is simple. After any next(), nextInt(), or nextDouble() call,  
you can 'add an extra nextLine()' method call that will retrieve the abandoned Enter key  
character. Then, no matter what type of input follows, the program will execute smoothly.

```java
	input.'hasNext()' 
    input.'hasNextInt()'
    input.'hasNextBoolean()' ...

these can be used in a while statement, prior to obtaining any data within the body  
can be used to control flow and handle errors on entry
```

### Control Flow Statements

These statements include:

-   decision-making statements java ( `if, switch` ) 
-   looping statements ( `for, while, do-while` )
-   and branching statements ( `break, continue` )

In for( ; ; ), The initialization and increment expressions can be comma-separated lists that enable  
you to use multiple initialization expressions or multiple increment expressions

```java
forEach - enhanced for:

for (variable declaration : name of array){
    // must be a new defined variable, only within for's scope
    'Codes' run on each element of the array in order
}

int[] myNumbers = {10, 20, 30, 40, 50};
for (int item : myNumbers)
System.out.println(item);

'NOTE' : the array/ ArrayList/ collection/ ... cannot be altered within a for-each statement
		 throws an 'error' if it is tried
```

You can use either a char, byte, short or int variable for switching. Starting &lt;>

from Java 7, you can also use a String variable for switching.
