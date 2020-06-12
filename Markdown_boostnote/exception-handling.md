---
title: "Exception Handling"
tags: ""
---
-   When an exception occurs, the normal flow of operations withing a program is exited.  
    no return value, client method can only catch an exception.

-   exceptions provide mechanism for
    -   error reporting
    -   error handling
    -   attempting recovery

-   other methods can also be used sometimes
    -   checking validity/existence
    -   methods return value diagnostics & check for success

-   Exceptions handling is mostly used when encountering **environment** problems
    -   incorrect URL, network interruption
    -   file not existing, no permissions

-   Exceptions can be used to **prevent object creation**

-   Errors and Exceptions "are" **throwable**. errors happen in JVM and are not recoverable, don't work with them.  
    there are two **subclasses** of exceptions:
    -   Runtime exceptions, them and any subExceptions are uncheckedExceptions.  
        logical problems, unlikely recovery, unanticipated failures.
    -   non-runtime exceptions whether in library or defined later, are checkedExceptions --must be handled  
        environment problems, possible recovery, anticipated failures.

non-Runtime exception

1.  IOException --files

RuntimeExceptions:  

1.  NullPointerException
2.  ArithmeticException
3.  ClassCastException
4.  NoSuchElementException  
    4.1 InputMismatchException
5.  IndexOutOfBoundsException  
    5.1 ArrayIndexOutOfBoundsException
6.  IllegalArgumentException
7.  dsd  
    . . .

### to throw an exception:

exception objects are thrown:

```java
//anywhere in methods:
throw new ExceptionNameType(String message);
```

-   thrown checked exceptions must be declared in method headers
-   compiler makes sure that checled exceptions are handled
-   There are two ways to handle checked Exceptions:
    -   use try-catch in the client method --recommended
    -   declare "throws" in the header of client method --not recommended

```java
/**
@throws ExceptionNameType reason
*/
public return method(arg) throws ExceptionNameType
----------------------------------------------------
//in client:
try{
	//protected statements
    method();
}
catch(ExceptionNameType e){
	//attempt recovery
}
```

catching multiple exceptions / multi-catch

-   different procedures for different exceptions, considering inheritance and cheking by order
-   only one catch expression is executed
-   finally is executed under any condition, even after a return statement. --used for releasing resources / opened files
-   e.printStackTrace(); to see how the exception moved through client methods

```java
try{
    //exception thrower
}
catch(ExceptionType1 e){
    //for type 1
    e.printStackTrace();
}
catch(ExceptionType2 e | ExceptionType3 e){
    // if not of type1 --> for type 2 or 3
    e.printStackTrace();
}
finally{
    
}
```

-   it is possible to just use try-finally  
    this is mostly used for doing finally-stuff  
    in this method, the exception is still thrown.  
    if it is a checked exception, must also be declared in method header.

```java
try{
	//protected
}
finally{
    //not-protected
}
```
