---
title: "GUI overall aspects"
tags: ""
---
IDE's have GUI design tools

History  

> AWT: Abstract Window Toolkit - uses OS real GUI system 
> Swing: extends AWT, powerful GUI construction  
> JavaFX: new approch to GUI programming

## Terminology

### Component

> a GUI widget that is placed in a container  
> countless components are awailable in Swing

### Container

    JPanel, Panel, Box, . . .

> a logical grouping for storing components  
> can use various **_Layout Managers_**

### Window

    JFrame, JWindow, JDialog, . . .

    * Frame and Dialog both inherit the Window class. 
    * Frame has maximize and minimize buttons but Dialog doesn't.
    * A frame is a window that has a title bar and border.
    * The Dialog control has a border and title and is  used to take some form of input from the user.

> a top level window container with  
> Title , Icon , Buttons 

-   A menu bar is a horizontal strip that is conventionally placed at the top of a container and contains user options.
-   A glass pane-a powerful container feature- resides above the content pane. tooltips reside here
-   If you add a MouseListener to the glass pane, it
    prevents the mouse from triggering events  
    on the components below the glass pane on the JFrame 

![](jframe-parts.JPG)

* * *

## LookAndFeels

```java
UIManager.LookAndFeelInfo info;
info.getClassName();
info.getName();
```

"getting installed LookAndFeels"

```java
for (UIManager.LookAndFeelInfo info : UIManager.getInstalledLookAndFeels()) {
	System.out.println(info.getClassName());
}

/*
javax.swing.plaf.metal.MetalLookAndFeel
javax.swing.plaf.nimbus.NimbusLookAndFeel
com.sun.java.swing.plaf.motif.MotifLookAndFeel
com.sun.java.swing.plaf.windows.WindowsLookAndFeel
com.sun.java.swing.plaf.windows.WindowsClassicLookAndFeel
*/

```

"changing the LookAndFeel

```java
try {
	for (UIManager.LookAndFeelInfo info : UIManager.getInstalledLookAndFeels() ) {
		if ("Nimbus".equals(info.getName())) { 
			UIManager.setLookAndFeel(info.getClassName());
			break; 
		}
	}
} catch (Exception e) {
	//keep current look and feel
}
```

"getting system lookAndFeel"

```java
System.out.println("System: " + UIManager.getSystemLookAndFeelClassName());
```

"getting currently using LookAndFeel"

```java
System.out.println("Current: " + UIManager.getLookAndFeel().getClass().getName());
```

* * *

## LayoutManagers

-   null			--absolute positioning
-   BorderLayout 	--five positions
-   FlowLayout	--place in order (allignment can be changed)
-   GridLayout 	--row and columns (same size)
-   BoxLayout		--arrange either vertically or horizontally
-   GridBagLayout	--aligns components that need not be of the same size. each component can span multiple cells
-   CardLayout	--only one component(card) is visible at a time
-   GroupLayout	--places them in a Container hierarchically.  Each component must exists in both a horizontal and vertical group
-   SpringLayout	--

considers preferredSize: null and FlowLayout:  
disregards preferredSize: BorderLayout and GridLaout  

> although BorderLayout considers it in primary(and fixed)  
> size of non=center components

**_ null --absolute positioning _**  
frame size is set including the width of the title bar
component location is set excluding the width of the title bar

> exact position of each component must be set  
> (setSize + setPosition) / (setBounds)  

**_FlowLayout _**  

```java
placed in order. changing allignment

setAllignment() FlowLayout.{LEFT, RIGHT, CENTER(default) }
```

**_BorderLayout_**

```java
panel.add(Component c, BorderLayout.POSITION );
		   NORTH, SOUTH, CENTER, LEFT, RIGHT
```

**_BoxLayout_**

```java
BoxLayout b1 = new BoxLayout(Container target[null] , int axis);
panel.setLayout(b1)
```

**_GridBagLayout_**  
The GridBagLayout class is a flexible layout manager that aligns components vertically,  
horizontally or along their baseline without requiring that components be of the same size.  
Each GridBagLayout object maintains a dynamic, rectangular grid of cells, with each component  
occupying one or more cells, called its **_display area_**.

To use a grid bag layout effectively, you must customize one or more of the **_GridBagConstraints_**  
objects that are associated with its components. You customize a GridBagConstraints object by  
setting one or more of its instance variables:

```java
Button button = new Button(name);
GridBagLayout gridbag = new GridBagLayout();
JPanel panel = new JPanel(gridbag);

GridBagConstraints c = new GridBagConstraints();
gridbag.'setConstraints'(button, c);
panel.add(button);
//a copy of object c is used. thus changing it
//later, will not affect the display
//the same "c" can be used for all object

GridBagConstraints c = new GridBagConstraints();

//determines whether to resize the component, and if so, how.
c.'fill' = GridBagConstraints.{ VERTICAL, HORIZONTAL, BOTH, NONE }

c.'weightx'	  = 0 //the weight of a component in horizontal resizing
c.'weighty'	  = 0 //the weight of a component in Vertical resizing
c.'gridwidth' = 1 //the number of cells to span horizontally
c.'gridheight'= 1 //the number of cells to span vertically
c.'insets' = new insets( , , , ) //empty space from position borders
gridwith can be set to:
GridBagConstraints.'RELATIVE';  //next-to-last in row
GridBagConstraints.'REMAINDER'; //end ro
```

* * *

### Borders

-   emptyBorder
-   lineBorder
-

```java
Border border = BorderFactory.creat[BorderType]()
```

* * *

* * *

```java
//classes with usable constants
SwingConstants. [ ]	--used in methods
SwingUtilities. [ ] --
InputEvent.	[ ]		--
"note": //just use the subClass which is being worked with
```

### common JWindows

```java
//default LayoutManager : BorderLayout
JWindow
JFrame		
JDialog		//short I/O messages

a JFrame has two parts:
1. the titleBar and buttons
2. a contentPane holding the components in the window
   contentPane is a JPanel, components are added to it
   before shortcut: 
   JPanel contentPane = (JPanel) frame.getContentPane();
   contentPane.add(Component c);
	//although still required
	//you must use a content panem When you want to use 
	//methods other than add(), remove(), or setLayout(), 
	"otherwise the results will not be shown"

"JWindow methods"
//size is set including the width of the title bar
"setSize();"		setting the size of the frame
"setMinimumSize()";	the minimum size of the window
//one of the previous two must be set
setMaximumSize();	the maximum size of the window
setLocation(600,300);		setting the location relative to screen
setLocationRelativeTo(); location calculated from here
setResizable();		whether user can change the size
setLayout(); 		changing the Layout			

setTitle();			setting the title of the window
setDefaultCloseOperation(); change action

EXIT_ON_CLOSE	   : exits the program when the JFrame is closed.
DISPOSE_ON_CLOSE   : closes the frame, disposes of the JFrame object, and keeps running the application.
DO_NOTHING_ON_CLOSE: disables the Close button.
HIDE_ON_CLOSE	   : closes the JFrame and continues running.

    
//close operations can be changed by adding a Windowlistener
//override methods windowClosing and windowClosed
// dispose method issues the WINDOW_CLOSED event
addWindowListener( overriden listener )

add(Component c) 	add a component
'pack()' 			sets the total size using preferredSizes
setVisible(true)	display

If you add or remove a component from a container after it has been made 'visible', you should
also call the invalidate(), validate(), and repaint() methods
You need to call repaint() if you add or remove a component after construction
```

### common JContainers

```java
//default LayoutManager : FlowLayout
JPanel

"JContainer methods"
setLayout() 		changing the Layout
add(Component c) 	add a component
remove(Component c)
setBorder()			a border surroundin the panel --lookup
```

### common JComponents

```java
JButton			// button
JCheckBox		// label positioned beside a square; click to display or remove a check mark
JRadioButton	// typically used for ButtonGroups
ButtonGroup		// a collection of JCheckboxes or JRadioButtons - single choice only
JSlider			// slide to set amount
JSpinner		
JProgressBar	
JToolBar		// toolbars ( like in ribbons )

JLabel			// uneditable image and/or text - does not accept key strokes
JTextField		// single row of text
JTextArea		// multiple rows & columns for text
JPasswordField	// without displaying content
JScrollPane		// used to scroll S.T. [like a textArea]
JScrollbar

JmenuBar, JMenu, JMenuItem // combined to create menus
				JCheckboxMenuItem
       		 	JRadioButtonMenuItem
JTabbedPane		// switching between tabs
JComboBox		// selection -dropdown list combined with a button or an editable field.
JList			// visible list, multi-selection

JTable
JTree
JColorChooser
JFileChooser

JOptionPane
JPopupMenu 		//A class that implements a menu which can be dynamically popped up
				//at a specified position within a component. 
				//As the inheritance hierarchy implies,
                //a PopupMenu can be used anywhere a Menu can be used

```

now to look at common methods:

```java
"common JComponent methods"
each property has a " get - is - set " method:

// name			// data-type
1. background	// Color
1/5Opaque		//paints every pixel within bounds
2. foreground	// Color
3. font			// Font		--used for text in component
4. border		// Border	--border around it
5. toolTipText	// String	--description with mouse hovering

6. height		// int		--size in pixels
7. width		// int		--size in pixels
8. size			// Dimension
9. minimumSize  // Dimension
10 maximumSize  // Dimension
11 preferredSize// Dimension 
 
12 enabled		// boolean	--can be interacted with  ? -ideal for buttons
13 focusable	// boolean	--can type key text on it ?
14 visible		// boolean	--can be seen on screen   ?

for null layout		//--exact positioning only
setBounds()			location and size
setLocation()		location
setSize()			size

getPreferredSize()	Returns the specified components preferred size.
					or calculated by the components layout manager, if none 
setPreferredSize()	for layouts other than null
					just the minimum size required to show contents

add[]Listener()		registering an EventListener of the specified type
					to the 'ListeneresList' of this Component

```

### some JComponents

![](components1.JPG)

* * *

### Awt class hierarchy

![Awt class hierarchy](awt-hierarchy.JPG)

* * *

### Swing inheritance hierarchy

![](swing-hierarchy.JPG)  

-   JComponent is a container ( from AWT )  
-   JPanel is a JComponent, not extended from panel or container

* * *
