---
title: "collections and Iterators"
tags: ""
---
## Arrays

creating arrays

```java
declaration only:	int[] userAge = int userage[]

After you declare an array variable, you need to create an array
and assign it to the variable. the array size is 'not' changeable afterwards:

1.	int[] userAge;
	userAge = new int[] {21, 22, 23, 24, 25};
	>> "note": using This method, it is also possible to 
			   change the array which is referred to, along with the size of course.
			   also, This change of reference can be done with other array object, 'regardless of size'

2.	int[] userAge2 = new int[] {21, 22, 23, 24, 25};
	int[] userAge2 = {21, 22, 23, 24, 25}; 'can be ommited'
        
3.	int[] userAge3 = new int[5];
```

** in order to do anything with arrays, they must first be initialized. even if it means: **

```java
int[] testArray = null ;
System.out.println(testArray) --> "null"

>>'note': if an array is defined in a Class as an instance variable,
the initializer to 'null' is automatically implemented in the 'constructor'
>>'note': if the array is a Class Array, it is first initialized to null, however
'each element' of the array can also have a null value 'after intialization' of some of them. -'null array'
```

Array methods:

-   import java.util.Arrays

```java

boolean result2 = 'Arrays.equals'(arr1, arr3); // two parameters

int[] dest = 'Arrays.copyOfRange'(source, start, end); [ to end-1]

String s = 'Arrays.toString'(arr1)
System.out.println(Arrays.toString(arr1)); // output: [1, 2, 3, 4, 5]

void 'Arrays.sort'(numbers2);

int foundIndex = 'Arrays.binarySearch'(anArray, value to lookup);
	return the exact index(Start with zero)
	if nothing exists: return ' - ' and position(Start with one) if existed
    // index = position-1
	
for length: a Field insted of a method:
		arr1.'length'

```

## ArrayLists

import:

    java.util.ArrayList

creating ArrayList:

```java
declaration only:	private ArrayList<type> listName; 

After you declare the object, you need to initialize it:

1. listName = new ArrayList<type>();

2. private ArrayList<type> listName = new ArrayList<type>();
```

ArrayList methods - how it's implemented is not required:

```java
listvarName.add(type object) -- add to the list
listvarname.get(index in ArrayList) -- Return an object from the list
listName.size() --- the lenght of it

not declaring a variable in the class for the size.
delegating it to the ArrayList:
	public int getCount / count() {
    return listlistName.size();
    }
	the second proposed name is present and used instead of a field

listName.remove(index) -- removing the object in the index of the ArrayList
listName.remove(Object obj) -- another way of the overloaded method
* : all indexes after this are reduced by 1

for each:
	for ( type tempObj: listName ){
    	codes on each element
    }

'NOTE' : the ArrayList cannot be altered within a for-each statement
		 listName.remove( --- ) throws an 'error'
```

## Iterators:

declaration:

```java
Iterator<type> iteratorName = collectionObject.iterator();

"note": the Iterator must be 'updated' before any while() execution
		otherwise, it will not have access to the actual collection
        "thus" never instantiate the Iterator at the beginning. or recreate[update] it before while()

a collection object can be an arrayList (or array(?) - not sure)
```

Iterator methods:

```java
Iterator<type> it = myCollection.iterator();

while(it.hasNext()){ // does another element exist or not
    it.next() -- gets the next element
    // codes executed on the new element
}
```

TIP: this can be used in a while statement to remove items.
       this makes the code similar to for-each statements.  

sideTip: sometimes the temp object might act wierdly,
		 declaring it in while at all loops might solve this.

```java
Iterato.utir<type> it = myCollection.iterator(); //always update prior to iteration
type temp;
while(it.hasNext()){ // whether another element exists
	temp = it.next();
	if(condition on temp)
        it.remove();
}
```

## HashSet - using sets

sets do no usually mainatin the order of entry - indexing is not supported  

declaration

```java
import java.util.HashSet;
java.util.Iterator;
HashSet<type> mySet = new HashSet<type>();

mySet.add(type obj); // sets do not have repetitive elements, will not be added if exists
Iterator<type> it = mySet.iterator();
```

## HashMap - using maps

a set that has a key field and a value field  
used for looking up ( searchin ) using the key field
supplying a key and retrieving values

```java
HashMap<type key, type value> myMap = new HashMap<type key, type value>();

myMap.put(type1 key, type2 value);

myMap.get(type1 key); //return the value correspondent to key

```
