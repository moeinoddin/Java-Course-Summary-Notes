---
title: "side-GUI : optional section of chapter 4 from Deitel"
tags: ""
---
the import statements allow us to use class  
Graphics (from package java.awt), which provides various methods for drawing text and shapes onto the screen  
class JPanel (from package javax.swing), which provides an area on which we can draw.

```java
import java.awt.Graphics;
import javax.swing.JPanel;
```

a new class:  
the keyword extends is used to indicate that class DrawPanel is an enhanced type of JPanel, a  
so-called **_inheritance relationship_** in which our new class DrawPanel begins with the existing members  
(data and methods) from class JPanel. then we add new features we’re adding in our DrawPanel class declaration

```java
public class DrawPanel extends JPanel
```

The first statement in every paintComponent method you create should always be this, which ensures  
that the panel is properly rendered before we begin drawing on it.

```java
super.paintComponent(g);
```

## complete example

#### a new defined class:

```java
import java.awt.Graphics;
import javax.swing.JPanel;
public class DrawPanel extends JPanel{
    
	public void paintComponent(Graphics g){
		super.paintComponent(g);
		int width = getWidth(); // total width
		int height = getHeight(); // total height
		g.drawLine(0, 0, width, height);
		g.drawLine(0, height, width, 0);
    }  
}
```

#### a main for execution:

To display the DrawPanel on the screen, you must place it in a window. You create a window
with an object of class JFrame.

```java
import javax.swing.JFrame;
public class DrawPanelTest{
	public static void main(String[] args){
        // create a panel that contains our drawing
        DrawPanel panel = new DrawPanel();
        
        // create a new frame to hold the panel
        JFrame application = new JFrame();
        
        // set the frame to exit when it is closed
        application.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        application.add(panel); // add the panel to the frame
		application.setSize(250, 250); // set the size of the frame
		application.setVisible(true); // make the frame visible
    }
}
```
