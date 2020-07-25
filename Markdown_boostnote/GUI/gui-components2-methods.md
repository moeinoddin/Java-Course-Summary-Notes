---
title: "GUI components2 methods"
tags: ""
---
### designing JMenus

-   each frame has 1 JMenuBar

```java
JMenu menu = new JMenu(String title);
JMenuItem item = new JMenuItem(String text);
	item.add'ActionListener'();

menu.'add'( JMenuItem / JMenu / component );

JMenuBar menuBar = new JMenuBar();
menuBar.add( menu );
frame.'setJMenuBar'( menuBar );
```

* * *

### setting MNemonics & accelerators

```java
//any component that has an actionListener
Component component;
component.setMnemonic('KeyEvent.VK_N');
component.setAccelerator(KeyStroke.'getKeyStroke'(KeyEvent.VK_N, 'ActionEvent'.CTRL_MASK));
//specially used for menu items.
```

* * *

### JList and Renderers

-   represents a list of text items. The list of text items can be set up so that the user can choose  
    either one item or multiple items. It inherits JComponent class.
-   it will use the **toString** method of the type of objects in it for the text items.

```java
JList<ClassType> list = new JList<ClassType>();

list.setListData(Object[] listData);
list.setSelectionMode(ListSelectionModel.SINGLE_SELECTION);
list.setFixedCellWidth(width);
list.setFixedCellHeight(height);
list.setCellRenderer(new MyCellRenderer());

list.addListSelectionListener( listener );
list.addMouseListener();
list.getSelectedIndex();
list.getModel();

//using a DefaultListModel to store data of a list
DefaultListModel<String> l1 = new DefaultListModel<>();  
	l1.addElement("Item1");
	
//better way to initialize a list
JList<ClassType> list = new JList<ClassType>(ListModel);
	
```

general structure of creating a ListCellRenderer

```java
private class MyCellRenderer extends DefaultListCellRenderer{  

@Override
public Component getListCellRendererComponent(JList list, Object value,int index,
                                              boolean isSelected, boolean cellHasFocus) {
	
    if (object instanceof  ClassType) {
		ClassType typeObj = (ClassType) object;
    	'setText'(String str) //method to display items in the list
		'setIcon'(icon);//icon on the left side of text
        
    	if (isSelected) {
	    	setBackground(list.getSelectionBackground());
	 		setForeground(list.getSelectionForeground());
	    } else {
    	    setBackground(list.getBackground());
        	setForeground(list.getForeground());
    	}
	setEnabled(list.isEnabled());
	}
	return this; // with the selected text and icon
}
```

* * *

### JTree and Renderers

-   used to display the tree structured data or hierarchical data. JTree is a complex component.  
    It has a 'root node' at the top most which is a parent for all nodes in the tree.

```java
// with the object that holds the data of this node
DefaultMutableTreeNode root = new DefaultMutableTreeNode(Object obj);
'root.add'(DefaultMutableTreeNode newNode/folder );

JTree tree = new JTree( TreeNode root ); //DefaultMutableTreeNode
JTree tree = new JTree( TreeModel treeModel );

tree.setModel(TreeModel newTreeModel);
tree.setRootVisible(boolean b);
tree.setCellRenderer( MyTreeCellRenderer );
tree.setCellEditor( MyTreeCellEditor );
```

general structure of creating a TreeCellRenderer

```java

private class MyCellRenderer extends DefaultTreeCellRenderer{
    
	@Override
	public Component getTreeCellRendererComponent(JTree tree, Object value, boolean selected, boolean expanded,
				boolean leaf, int row, boolean hasFocus) {
			// TODO Auto-generated method stub
			return null;
		}    
}
```
