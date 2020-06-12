---
title: "GUI memorization notes"
tags: ""
---
The Swing classes are part of a more general set of  
GUI programming capabilities that are collectively called the **Java Foundation Classes (JFC).**  
JFC includes Swing component classes and selected classes from the java.awt package.

Almost all Swing components are said to be lightweight components because they are written  
completely in Java and do not have to rely on the local operating system code

The only heavyweight components used in Swing are  
swing.JFrame, swing.JDialog, swing.JWindow, swing.JApplet,  
awt.Component, awt.Container, and awt.JComponent.

> A frame is a window that has a title bar and border.

A container is a type of component that holds other components so you can treat a group of them as a single entity  
the Container class is a child of the Component class. Therefore, every Container object “is a” Component.
