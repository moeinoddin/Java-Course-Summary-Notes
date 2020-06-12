---
title: "GUI utility methods"
tags: ""
---
#### placing a frame in the center of the screen

```java
//using Toolkit
Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
frame.setLocation((int)screenSize.getWidth()/2-frame.getWidth()/2, (int)screenSize.getHeight()/2-frame.getHeight()/2);
```

#### adding a created event to event queue

```java
//for creating events through other means, like closing the frame with an item in a menu
Toolkit.getDefaultToolkit().getSystemEventQueue().postEvent( Event );

//to trigger the close event through other means
frame.dispatchEvent(new WindowEvent(frame, WindowEvent.WINDOW_CLOSING));
```

get project directroy absolute path

```java
System.getProperty("user.dir");
```
