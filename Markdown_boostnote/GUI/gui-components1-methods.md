---
title: "GUI components1 methods"
tags: ""
---
### JLabel

```java
JLabel label = new JLabel(String text);

ImageIcon img = new ImageIcon("fileLocation");
JLabel label = new JLabel(img);
label.setIcon(img);
//either of the 2 above work
//file location is addressed from the project folder unless an absolute path is used
//ImageIcon can be a local file, URL, created in code, ...

label.setBackground()
label.setOpaque() --can be seen through or not
//If you need to paint the label's background, you
//should turn its opacity property to "true"
    
label.setHorizontalAlignment(int)	//LEFT, CENTER, RIGHT, LEADING, TRAILING
label.setVerticalAlignment(int)		//TOP, CENTER, BOTTOM
//LEADING (the default for text-only labels)
//CENTER (the default for image-only labels)

```

* * *

### JTextField

```java
//constructor
new JTextField(columns): constructs a new, empty JTextField with a specified number of columns.
//preferred size is calculated using column number. 
//number of characters depends on font size and the word that are entered
//it is not a constraint on the number of characters in the text field. they will pass the object border
```

* * *

### ButtonGroup - awt

-   Sometimes, you want options to be mutually exclusive—that is, you want the user to be  
    able to select only one of several choices ( JCheckBoxes / JRadioButtons ).

-   After a JCheckBox in a ButtonGroup has been selected,  
    one in the group will always be
    selected.

```java
aGroup.setSelected(aBox);	//setting the checked option by programmer
aBox.isSelected();			//available for each option

aGroup.add( box1 );aGroup.add( box2 );aGroup.add( box3 );

'a trick:'
box4.isVisible(false);
aGroup.add(box4);
aGroup.setSelected(box4);	//no options selected at first
```

* * *

### JComboBox

A combo box is a component that combines a button or an editable field and a drop-down list.  
If the field at the top of the
combo box is editable, the user can also type in it

```java
//Adding the angle brackets and String notifies the compiler of the expected data types
//a JComboBox expects items that are added to be Object types
JComboBox<String> majorChoice = new JComboBox<String>();
majorChoice.addItem("English");
majorChoice.addItem("Math");
majorChoice.addItem("Sociology
                    
String[] majorArray = {"English", "Math", "Sociology"};
JComboBox majorChoice = new JComboBox(majorArray);
                    
comboBox.setEditable(true)	//the text a user types must exactly match an item in the list box.
getSelectedIndex() 			//return -1 if the item typed is incorrect
if(getSelected!=-1)
	Do
else
	Dont	//error message or default option
```

-   first item is at position 0,
-   A JComboBox does not have to hold items declared as Strings; it can hold an array of Objects and  
    display the results of the toString() method used with those objects.

* * *

### setting up fonts

```java
Font newFont = new Font(name, style, size)
Component.setFont( newFont );
//The typeface argument in the Font constructor is only a request.
//if necessary, it substitutes a default font

component.getFont().deriveFont(style, size);	//same font type but different style and size
```
