### **Part B: "Undo System for Text Editor"**

A simple text editor uses a **stack** to support **undo** operations. Every time the user types a word, it is pushed onto the `actionStack`. The editor also supports a **"redo"** feature, but only **immediately after an undo**, and only **once**.

You are to design a system using **two stacks**:
- `actionStack`: stores words typed (most recent on top)
- `redoStack`: stores words that were undone (only one level of redo allowed)

Implement a method:
```java
public String undoLastAction()
```
- Pops the last word from `actionStack`
- Pushes it to `redoStack` (only if `redoStack` is empty — no multiple redos)
- Returns the undone word

Also implement:
```java
public String redoLastUndo()
```
- Only works if `redoStack` is not empty
- Moves the word back to `actionStack`
- Returns the word, or `null` if redo not possible


```java
import java.util.Stack;

public class TextEditor {
    private Stack<String> actionStack;
    private Stack<String> redoStack;

    public TextEditor() {
        actionStack = new Stack<>();
        redoStack = new Stack<>();
    }

    /**
     * Undo the last action: pop from actionStack, push to redoStack (if empty)
     * @return the undone word, or null if no action to undo
     */
    public String undoLastAction() {
        
    }

    /**
     * Redo the last undone action
     * @return the word restored, or null if redo not possible
     */
    public String redoLastUndo() {
        
    }
}
```

---

**[7 marks]**

> 🎯 *Tests understanding of stack use in real systems and constraints.*

---
**Answer**
```Java 
public String undoLastAction(){
    if(actionStack.isEmpty){
        return null; 
    }
    String undoneWord = actionStack.pop();
    redoStack.clear();
    redoStack.push(undoneWord);
    return undoneWord;
}
```
```java 
public String redoLastUndo(){
    if (redoStack.isEmpty()) {
        return null;
    }
    String redoneWord = redoStack.pop();
    actionStack.push(redoneWord);
    return redoneWord;
}
```

---

## **Question 3: Binary Trees – Diagram-Based Operations**

### **Given**:
A **binary search tree (BST)** with the following nodes inserted in this order:  
**50, 30, 70, 20, 40, 60, 80**

---

### **Part A**:
Draw the **final structure** of the BST after all insertions. Label all nodes.

**[3 marks]**

---
**Answer**
```
             50
           /    \
          30    70
         /  \   /  \
       20   40 60   80 
```

---

### **Part B**:
Now perform the following operations **in sequence**, drawing the tree **after each step**:

1. Insert **35**
2. Insert **75**
3. Delete **30** (use standard BST deletion: if two children, replace with **in-order predecessor**)
4. Delete **70**

Show the tree after **each** operation.

**[8 marks – 2 each]**

> 📌 *Ensure diagrams are clear, with left/right children correctly positioned.*

---
**Answer**
```
insert 35 
             50
          /       \
        30         70
      /    \     /    \
     20     40  60     80
       \
        35

insert 75 
             50
          /       \
        30         70
      /    \     /    \
     20     40  60     80
       \              /
        35           75

delete 30 
             50
          /       \
        20         70
           \     /    \
           35   60     80 
             \        /
              40     75 

Delete 70 
             50
          /       \
        20         60
           \          \
           35          80 
             \        /
              40     75 
```
---

### **Part C**:
After the final tree, state:
- The **height** of the tree
- Whether it is **balanced**
- One advantage of a **balanced BST** over an unbalanced one

**[3 marks]**

---
**Answer**

Height : 4 

Yes it is balanced 

A balanced binary tree has a guaranteed logarithmic time complexity, compared to and unbalanced binary tree 

---

## **Question 4: Vocabulary & Diagram Quiz**

### **Part A: Definitions**
Define the following terms (1 mark each):

1. Node
2. Singly linked list
3. Stack (LIFO)
4. Binary search tree (BST)
5. Balanced tree
6. In-order traversal
7. Overflow (in stack context)
8. Head (in linked list)

**[8 marks]**

---
**Answer**

1. **Node** - It's a unit that holds data and contains a link or a pointer to another node.
2. **Singly linked list** - A singly linked list is a linear data structure made up of a sequence of nodes. Each node stores data and a reference to the next node in the list. Traversal is only possible in one direction, from the first node to the last.
3. **Stack** - A stack is an abstract data type that follows the Last-In, First-Out (LIFO) principle. The last element added to the stack is the first one to be removed.
4. **Binary search tree** - A Binary Search Tree (BST) is a binary tree where the nodes are arranged in a specific order: for any given node, all values in its left subtree are less than its own value, and all values in its right subtree are greater
5. **Balanced tree** - A balanced tree is a type of tree where the height of the left and right subtrees of any node is roughly equal, with the difference in height being no more than a small, constant number.
6. **In-order traversal** - In-order traversal is one of the three main tree traversal methods. It visits the nodes of a binary tree in the following order: first the left subtree, then the root node, and finally the right subtree 
7. **Overflow** - An overflow in a stack occurs when an attempt is made to add an item to a stack that is already at its maximum capacity.
8. **Head** - The head is a reference or pointer to the first node in a linked list.

---

### **Part B: Diagram Interpretation**

You are given the following **singly linked list diagram**:

```
[Anna] -> [Bob] -> [Cara] -> null
```

Each node contains a `Customer` object.

1. Label the **head node**.
2. What is the **successor** of Bob?
3. What happens if the reference from Bob to Cara is lost?
4. Why can't you traverse from Cara to Bob?

**[4 marks]**

---
**Answer** 

1. the head node is anna 
2. cara 
3. then the successor of bob will be null 
4. because in a singly linked list you can only traverse one direction. 

---

### **Part C: Tree Type Identification**

Given three tree diagrams (describe them verbally or sketch in exam):

- **Tree A**: All leaves at same level, full at every level
- **Tree B**: Skewed heavily to the left, height = n-1
- **Tree C**: Height difference between left and right subtrees ≤ 1 at every node

Identify each as:
- Full binary tree
- Skewed (unbalanced) tree
- Balanced BST

And state which would give **best search performance** and why.

**[5 marks]**

---
**Answer**

Tree a : Full binary tree

Tree b : Skewed (unbalanced) tree 

Tree c: balanced BST 

Explain : 
Tree C would give the best search performance. Although the time complexity of Tree A and Tree C is the same Olog(n). 
A full binary tree is a rigid structure that is often impossible to maintain when inserting or deleting without rebuilding the whole tree, unlike a balanced binary tree. 
A balanced binary tree is easier to maintain when inserting or deleting. 

---