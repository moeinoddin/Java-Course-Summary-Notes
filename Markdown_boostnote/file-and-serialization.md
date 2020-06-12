---
title: "File and serialization"
tags: ""
---
classes in this section:

```java
import java.io.*;

//Byte-based:
1. FileInputStream, FileOutputStream;//don't use, cuz only bytes can be read/written
2. BufferedInputStream; BufferedOutputStream	
3. ObjectInputStream; ObjectInputStream 		
//Character-based:
4. FileReader, FileWriter;
5. BufferedReader, BufferedReader;
//utilities:
6. Scanner
7. PrintWriter
8. Formatter

9. implements Serializable 	private static final long serialVersionUID = 1L; 
10. File;

import java.nio.file.*;
11. Path
12. Paths
13. File
14. DirectoryStream
```

* * *

File

> a sequential Stream of bytes [0, n-1].  
> which ends with and EOF marker = -1  
> java receives an EOF indication from the system.

### NIO classes and interfaces

getting file and directory information:  

```java
import java.NIO.file.*;
```

interfaces:

-   Path:
    > without opening the file  
    > represents location of a file/directory

```java
Path path = Paths.get(String URI);

path'getFileName()';
path'isAbsolute()';
...
```

-   DirectoryStream: 
    > allow iteration through contents of a directory

classes:

-   Paths:
    > static methods to get Path objects

```java
Path path = Paths.get(String URI);

//java runs from the "projects" folder
Absolute path: "E://CourseCodes/ ..."
relative paths:
    "./folder/file.type"  //the current folder -- project directory
    "folder/file.type"    //by default using the project directory
    
    "../rest" //up by one folder
        
//use '/' instead of '\' --although both are rendered the same in path expressions
```

-   Files: working with files and directories
    > static methods to do various things with files & directories  
    > copy-create-delete-information-read contents  
    > create objects that can manipulate the file

```java
Files.'size()';
Files.'newDirectoryStream()';
Files.'isDirectory()';
Files.'exists()';

File f = new File(URI);
    f.exists();
```

* * *

Stream

> a sequence of bytes which can be read/written  
> inputStream from source  
> outputStream to   destination

System

```java
System.setOut(PrintStream stream)
System.setErr(PrintStream stream)
System.setIn(PrintStream stream)
```

types of streams:

-   Byte-based Streams:
    > in binary data format [char-2, int-4, double-8]  
    > Binary files
-   Character-based Streams:
    > using sequence of characters - 2bytes for each  
    > text files

```java
import java.io
import java.nio
```

## Character Streams: **_Reader & Writer_**

-   BufferedReader - BufferedWriter
-   FileReader - FileWriter  

![](character-streams.JPG)

## Byte Streams: **_InputStream & OutputStream_**

-   FileInputStream - FileOutputStream
-   BufferedInputStream - BufferedOutputStream
-   ObjectInputStream - ObjectOutputStream

![](byte-streams.JPG)

* * *

### common notes

-   many checked exceptions when working with files
    -   SecurityException --insufficient permissions
    -   FileNotFoundException --doesn't exist and can't create
    -   NoSuchElementException --using Scanner, wrong format or no more data
    -   %%%ClosedException --if the object has been closed

```java
client method() throw IOException

try-catch-finally in called method()
try(resources){}catch{}//resources-(readers/writers) closed automatically
```

-   close writers/readers and ... in code
-   if an existing file is opened, its contents are truncated

* * *

### FileReader - Character input

```java
FileReader reader = new FileReader( File/address );

reader.'read()'; //get next character code in file as integer
reader.'ready()';//if the end hasn't been reached
    
int input = fileReader.'read()'
char data = (char) input	  //needs to be cast
while( (input = fileReader.read()) != -1 ) //-1 is EOF
```

### FileInputStream - Byte input

```java
FileInputStream in = new FileInputStream( File/address );

in.'read()'; //get next Byte in file as integer
in.'available()';//if the end hasn't been reached

int data = in.read();
while( (data=in.read()) != -1 ) //-1 is EOF
```

### FileWriter - Character output , FileOutputStream - Byte output

```java
FileWriter out = new FileWriter( File/address );
FileOutputStream out = new FileOutputStream( File/address );

out.'write()';
```

### Buffering - enhanced File IO

**BufferedOutputStream - BufferedInputStream**  

> using a byte\[] buffer object, hold the data of many output operations and transfer all at once when buffer fills  
> logical output operation --> physical output operation  

```java
int count;
byte[] buffer = new byte[4096];
BufferedInputStream in;
BufferedOutputStream out;
//then in try:
in = new BufferedInputStream(new FileInputStream(srcFile));
out = new BufferedOutputStream(new FileOutputStream(dstFile));
while (in.available() > 0) {
    //just use the BufferedWriter object, instead of FileWriter
	count = in.read(buffer);
	out.write(buffer, 0, count);
}
out.flush();
```

**BufferedWriter - BufferedReader**  

> using a byte\[] buffer object, hold chunks of data read from a file all at once, whenever the buffer object is empty.  
> logical input operation &lt;-- physical input operation 

```java
BufferedWriter writer = null; //then in try:
writer = new BufferedWriter(new FileWriter(txtFile));
//just use the BufferedWriter object, instead of FileWriter

writer.'write(txt)';
writer.'flush();
//buffer doesn't need to be defined for writing
//-------------------------------------------------
BufferedReader reader = null;
reader = new BufferedReader(new FileReader(txtFile));
char[] buffer = new char[2048];//buffer for inputs

while (reader.'ready()') {
	count = reader.read(buffer);
    //read to buffer object, return number of read characters
	//do stuff with read inputs
}
```

using the **flush** method of a stream object. to transfer partial buffer logical **output** operation.

* * *

utilities for File IO:  
**Scanner** - the same functionalities as before

```java
Scanner scanReader = new Scanner(fileReader/File/address)
//also supports any File,Readable,InputStream
while(scanReader.hasNext---()) ...
```

**PrintWriter** - similar to System.out.---

```java
PrintWriter output = new PrintWriter (fileWriter/File/address);
//also supports any File,PrintStream,OutputStream

output.'println() , print() , printf()';
```

**Formatter** - string formatting - regex?  
can also be used with files like using "printf"

```java
Formatter output = new Formatter(fileWriter/File/address);
//also supports any File,PrintStream,OutputStream

output.format("StringFormat",args);
```

* * *

## Serialization - Object in File IO

-   Objects must implement the **Serializable** interface in order to be available for saving files ( OutputStreams )
    -   all fields must be serializable
    -   fields can be declared **transient** to be skipped in serialization
        -   these fields must be **recalculated** after deserialization
-   this is just a tagging interface
-   can be used together with Byte-based file stream classes
    -   FileInputStream, FileOutputStream

```java
public class ClassName implements Serializable{
private static final long serialVersionUID = 1L; 
//used for versioning, since different versions must be interpreted differently   

}

```

### ObjectInputStream

```java
ObjectInputStream in;
in = new ObjectInputStream(new FileInputStream(new File(fileAdress)));

in.'readObject()' //read an object from an InputStream and return the reference
				  //must be cast to a variable in the stack
```

### ObjectOutputStream

```java
ObjectOutputStream out;
out = new ObjectOutputStream(new FileOutputStream(new File(fileAddress)));

out.'writeObject()' //write an object to an outputStream
```

* * *

* * *

### obtained notes:

-   before data can be read from a file, it must be closed,  
    inorder to commit the changes.
