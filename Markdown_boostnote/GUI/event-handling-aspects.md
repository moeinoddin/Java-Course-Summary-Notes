---
title: "Event handling aspects"
tags: ""
---
-   GUIs are EVENT driven
    > the order of code execution is different from using a main method  

-   sperating Logic from UI using MVC design pattern  
    Model - View - Controller  
    [Excellent tutorial video on youtube](https://www.youtube.com/watch?v=dTVVa2gfht8)

Model:

> Model represents an object or JAVA POJO carrying data. It can also have logic to update controller if its data changes. 

> by carrying data we mean, holding private fields and setters.

> Model doesn't even know view exists. has methods that will be used by controller to update view when data changes. (observer class?)

View

> presents the model’s data to the user. The view knows how to access the model’s data, but it does not know what this data means or what the user can do to manipulate it.  

> usually has more fields and getters

> has methods to add EventListeners, that are defined in the controller class.

Controller

> exists between the view and the model. It listens to events triggered by the view (or another external source) and executes the appropriate reaction to these events. In most cases, the reaction is to call a method on the model. Since the view and the model are connected through a notification mechanism, the result of this action is then automatically reflected in the view  

> knows about both the model and view (has fields about them)

> defines the listeners, registers them using the methods of the **view class**. in the implementation of the listener, uses methods of the model.

> updates the view using an accessor of the models data

Controller acts on both model and view. It controls the data flow into model object and updates the view whenever data changes. It keeps view and model separate.

```java
typically it has 2 field
public class controller{
	private Model model;
    ...
    private View view;
	...
}
```

![](mvc-design-pattern.png)

-   using nested-classed recommended instead of implementing a Listener in the outer class


-   nested classes  
    -   used especially when some code is only practical to a certain class
    -   using a private or protected access modifier for the nested-class is practitcal
    -   it can be declared static as well, non-static nested classes are called **inner classes**  
    -   it can directly access the fields of its outer-class

-   Event handling is usually done through nested classes:  
    1.  creat a class representing the event handler
    2.  implement at least one Listener interface in it
    3.  create an object of this Listener class and register it for a component

```java
an EventHandler Class can implement "multiple classes"
private class []Handler implements []Listener1, []Listener2 {
	//implement all methods	
}

usually in constructor{
	[]Handler handler = new []Handler();

	componentObj1.add[]listener1(handler); //register a Listener1 type event handler
	componentObj1.add[]Listener2(handler); //register a Listener2 type event handler
	componentObj2.add[]Listener2(handler); //register a Listener2 type event handler
}
```

* * *

## Event **_Classes_** List:

an object of these classes is sent to a method of corresponding Listener classes

-   ActionEvent >> clicking a button or pressing Enter
-   AdjustmentEvent >>
-   ItemEvent >> clicking an Item on a JList or . . .
-   TextEvent
-   ComponentEvent
    -   FocusEvent  >> selecting a component. components have a setFocusable() method  
    -   InputEvent  
        -   MouseEvent  
            -   MouseWheelEvent 
        -   KeyEvent
    -   ContainerEvent >> a component is added or removed
    -   PaintEvent
    -   WindowEvent

* * *

## Listener **_interfaces_**:

-   an interface exists for each EventType.  
-   an **eventHandler nested-class** can implement multiple Listener interfaces  
-   each component can have multiple eventHandlers (ListenersList).
-   also each listener can be registred on multiple sources
-   splitted Listeners:
    -   MouseListener
    -   MouseMotionListener
    -   MouseInputListener >> extends both interfaces	
-   an AdapterClass also exists for each Listener with an empty implementation.
    > we can choose which ones to override later on

### existing listeners

![](event-listeners.JPG)

### supported listeners

![](available-listeneres-jpg.JPG)

* * *

#### Action Event & Listener:

```java
ActionListener interface methods:
	actionPerformed(){ /* implement */ }

ActionEvent e
e.'getSource'(); //component that created event - can be used on other event types as well 
```

#### Focus Event & Listener:

```java
FocusListener interface methods:
	1. focusGained(){ /* implement */ }
	2. focusLost()  { /* implement */ }

FocusEvent e;
e.'isTemporary'; 	//when the frame has been deFocused completely
e.'getComponent';	//the currently focused component
e.'getOppositeComponent'; //previously focused component
```

#### Mouse Event's' & Listener's'

```java
MouseListener interface methods:
    1. mousePressed		//any mouse button pressed on a component
    2. mouseClicked		//pressed and released while remaining on component
    3. mouseReleased	preceeded by 'mousePressed' and one or more 'mouseDragged' events
    4. mouseEntered		//enter the bounds of a component
	5. mouseExited		//exit the bounds of a component

MouseMotionListener interface methods:
    1. mouseDragged		//all events sent to component which dragging began on
    2. mouseMoved		//all events sent to component which mouse is currently on
"note": these are called for each Pixel.
        
MouseEvent e;
e.'getX';
e.'getY';
e.'getClickCount';

InputEvent.'is[]MouseButtom'; 	//which button was interacted with 
// SwingUtilities, InputEvent, MouseEvent can all be used for this

MouseWheelEvent e; //a subClass of MouseEvent
e.'atleast 3 methods for scroll amount'
```

#### Key Event & Listener

```java
KeyListener interface methods:
	1. keyPressed	//any key is pressed
    2. KeyTyped		//any non actionKey is pressed
    3. keyReleased	//after atleast one of previous two

KeyEvent e;
e.'getKeyCode()';	//int constant
	KeyEvent.'getKeytext(int code)' //String value of key - as written on keyboard
e.'getKeyChar()'	//Unicode value of "typed" character
e.'isActionKey()'	//Home, F2, PageUp, ...
        
e.'getModifiers()'	//CTRL, SHIFT, ALT, ...
	keyEvent.'getKeyModifiersText()' //String value of modifiers

"note": these methods work with "keyPressed" events, not keyTyped events
        
InputEvent.'isAltDown()';
InputEvent.'isCTRLDown()';
InputEvent.'isSHIFTDown()';
```

#### item Event and Listener

When the status of say a **_JCheckBox_** changes from unchecked to checked (or from checked to  
unchecked), an **_ItemEvent_** is generated, and the **_itemStateChanged()_** method executes.

```java
ItemListener interface methods:
	1. itemStateChanged

ItemEvent e
e.'getItem()'		//determine which object generated the event
e.'getStateChange()'//method to determine whether the event was a selection or a deselection.



ItemEvent.SELECTED 
ItemEvent.DESELECTED

```

* * *
