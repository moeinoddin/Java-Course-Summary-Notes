---
title: "JOptionPane messages"
tags: ""
---
import:

```java
import javax.swing.JOptionPane;
```

**_MessageDialog_** — displays a message to the user  
**_InputDialog_** — Prompts the user for text input  
**_ConfirmDialog_** — Asks the user a question, providing buttons that the user can click for **_"Yes, No, and Cancel"_** responses  

**_parentComponent_** might be used if the message is  
to be part of a larger application

## message dialog:

```java
JOptionPane.showMessageDialog( [parentComponent], [message], [title], [messageType], [icon] );

```

PARAMETERS:  

**_parentComponent:_** determines the Frame in which the dialog is displayed.  
**_message:_** the Object to display  
**_title:_** the title string for the dialog  
**_messageType:_** the type of message to be displayed:

> ERROR_MESSAGE, INFORMATION_MESSAGE, WARNING_MESSAGE, QUESTION_MESSAGE, PLAIN_MESSAGE

**_icon_**: the icon which is used to give the user a better understanding

note that the last 3/1 arguments are optional --> 3 polymorphs

When the first argument to showMessageDialog() is null  
it means the output message box should be placed in the center of the screen

NOTE: the escape sequences ' \\n ' , ' \\" ' , and ' \\ ' operate , but ' \\t ', ' \\b ', and ' \\r ' do not work in the GUI environment.

## input dialog:

An input dialog box asks a question and provides a text field in which the user can enter a
response.  
Six versions of this method are available. it's best to choose within the IDE --> **_" CTRL + SPACE"_**  
The showInputDialog() method returns a **_String_** that represents a user’s response or **_null_** meaning the user canceled the input

```java
import javax.swing.JOptionPane;  
JOptionPane.showInputDialog( [parentComponent], [message], [title], [messageType], [icon], [selectionValues], [initialSelectionValue] )
    
```

PARAMETERS:  

**_parentComponent_**: the parent Component  for the dialog  
**_message_**: the Object to display  
**_title_**: the String to display in the dialog title bar  
**_messageType_**: the type of message to be displayed:  

> ERROR_MESSAGE, INFORMATION_MESSAGE, WARNING_MESSAGE, QUESTION_MESSAGE, PLAIN_MESSAGE

**_icon_**: the Icon image to display  
**_selectionValues_**: an array of Objects that gives the possible selections  
**_initialSelectionValue_** the value used to initialize the inputfield

to convert to numerical values the following functions can be used:

```java
Integer.parseInt(String str);
Double.parseDouble(String str);
These classes are called type-wrapper classes. They include methods that can process primitive type values.
```

## confirm dialog:

the user can click to confirm a choice. 4 version are available  
the method returns an integer containing one of three possible values:  

> JOptionPane.YES_OPTION,  
> JOptionPane.NO_OPTION,  
> JOptionPane.CANCEL_OPTION  
> these can be compared in a boolean exception  

PARAMETERS:  
**_parentComponent:_**  the parent Component for the dialog, which can be null.  
**_message:_** the Object to display  
**_title:_** the title string for the dialog
**_optionType:_** an int designating the options available on the dialog:  

> YES_NO_OPTION,  
> YES_NO_CANCEL_OPTION  
> OK_CANCEL_OPTION  

**_messageType:_** an int designating the kind of message this is,primarily used to determine the icon:   

> ERROR_MESSAGE, INFORMATION_MESSAGE, WARNING_MESSAGE, QUESTION_MESSAGE,PLAIN_MESSAGE  

**_icon:_** the icon to display in the dialog
