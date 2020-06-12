---
title: "Strings"
tags: ""
---
String s="learn working with strings";

## Strings and arrays are refference types

    there is a difference between primitive types and reference types;
    the former stores a valuen while the latter stores an address to where the data is stored.

    Strings are Immutable: changing it is actually creating a new string and assigning the new address

    Strings cannot span multiple lines of code.

## object methods:

```java
String s;
's.length()'; -can be used on typed strings as well
	int x = "hey there".lenght();

's.toUpperCase() , s.toLowerCase()'

's.substring'(int start, int end) - from start to 'before' end (end-1)
	[index of the first position to 'stop' extracting]
    String y = s.substring(o,s.length) = s.substring(o);

char[] charArray = s.'subSequence'(int start, int end);

char[] charArray = s.'toCharArray()'

public void getChars /** note it being a void */
s.getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)
	name of destination character array and starting point to place characters


s.'charAt'(int i) - return the character at index i

s1.'equals'(String s2);
	boolean equalsOrNot = s1.equals(s2);

String[] parts = s.'split'(String splitter);
splits a string into substrings based on a user-defined separator.
returns an array that contains the resulting substrings
```

```java
s.'isEmpty()' - true/false

s1.'compareTo'(s2) : Compares two strings lexicographically - difference of the two character values at
position k in the two strings. If there is no index position at which they differ, then the shorter
string lexicographically precedes the longer string. - [s1-s2].
can be '-' or '+'

s.'indexof'(char ch / String str, [int fromIndex])
the index of the first occurrence of the character in the character sequence represented by this 
object that is greater than or equal to fromIndex, or -1 if the character does not occur.

s.'lastIndexOf'(char ch / String str, [int fromIndex])

String s2= s.'replace'(char oldChar, char newChar)
a string derived from this string by replacing every occurrence[ or 's.replaceFirst'] of oldChar with newChar.

boolean ifContain = s.'contains'(char[] c / String s);

s.'trim()' - the same string without any whitespaces


```

## Class(Static) methods

```java
String.'valueOf'(char[] / int[] / ... ) // convert to String
String.'format'("s1 %d s2 %f %c ", , , ... )// create a String like printf without output

```
