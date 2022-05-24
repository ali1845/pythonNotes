# Linked lists

## 1. Introduction

  - Linked lists are ordered collections of objects.

  - Just like lists/arrays Linear data structure;

    - elements are arranged sequentially and each element is connected to its previous and next element.


  - Elements in linked lists are not stored in a contiguous location, unlike lists.

  - Instead, elements in the linked list are linked using a pointer.


##### Limitations with Lists

  - Size of the array is fixed.

      - Upper limit of the element has to be specified in lists.


  - Memory allocated is equal to the upper limit.

  - Insertion and deletion are expensive in the list.

    - To insert a new element in the list, elements in the list have to be shifted to create a room for the new element.
    - And to delete an element from the list everything has to be shifted back.

##### Linked list advantages

  - Dynamic Size
  - Ease of Insertion and deletion

##### Linked list disadvantages

  - Random access to elements is not possible in the linked list. i.e. accessing an element with an index. Hence binary search is not allowed.

  - Extra pointer memory space is needed with each element.

  - No locality of reference in a linked list, as per in lists elements are stored in a contiguous location that is not the case in Linked list.

## 2. Structure of Linked list:

  - Each element of a linked list is called **Node**.
  - Every *Node* consists of two fields;

      1. **Data:** Holds the value to be stored in the Node.
      2. **Next Pointer:** A reference to the next Node.
###### Linked List structure;

      ![Linked List structure](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2013/03/Linkedlist.png)


  - A linked list is a collection of Nodes.
  - Where the first Node is called the **head**.
  - Head is used for iterating through the list.
  - To determine the end of the linked list. The last Node must have its **Next Pointer** pointing to `None`.

## 3. Some Practical Real-world Examples Of Linked List

- Used to implement **Queues, Stacks and Graphs**.
- Lifecycle management for an Operating System.
- Undo buttons for a program.
- Previous and Next of any application, e.g. Music Player, Web Browser.


## 4. Performance Comparison: Lists vs Linked List

##### i. Memory Usage:
Since python lists are dynamic arrays, the memory usage of both linked lists and lists is very similar.

##### ii. Deletion and Insertion of Elements:

###### Lists

There are two ways to insert elements and two corresponding ways to delete an element.

- **Insertion and deletion using `.append()` and `.pop()`.**

  - `.append()` adds an element at the end of the list.
  - `.pop()` removes the element from the end of the list.
  - These methods doesn't require the shifting of other elements. Since it performs operation only at the end of the list.
  - So the time complexity for performing the operation, `.append()` and `.pop()`, at the end of the list is constant, **O(1)**.


- **Insertion and deletion using `.insert()` and `.remove()`**

  - `.insert()` insert an element in the list at a given index.
  - `.remove()` removes the element from the list at a given index.
  - However, inserting and removing the element from the start or close to the start of the list requires shifting other elements in the list.
  - Which will increase the average time complexity to **O(n)**, where **n** is the length of the list.

###### Linked List
Since Linked lists do not use contiguous locations. And Nodes are linked together with a pointer and head. So deletion and insertion at any position in the linked list are very straightforward.

So the time complexity to perform this operation is always constant, that is **O(1)**.

##### iii. Retrieval of Elements
- ###### Lists: For a specific element from the list.
    If you know which element you want to access, lists work better than Linked lists in this case when it comes to the retrieval of that element.

    Since lists can access the element you want using indexes. You don't need to traverse the whole list to find that element.

    So the time complexity perform by this operation from the list is constant to **O(1)**.

- ###### Linked Lists: For a specific element from the list.
Whereas in linked lists you need to traverse the entire list to find that specific element. So the time complexity stretches to the length of the list, that is **O(n)**. Where **n** is the length of the list.

##### Python's collection.deque
The module **collection** in Python implements an Object called **deque**, stands for **double-ended queue**. The object contains several methods. Some of them are listed and implemented below.

The Object collection.deque uses an implementation of a link list, that can be used to access, insert, or remove elements from the beginning of the end of a list.

The time complexity of accessing elements using the collection.deque Object is constant, **O(1)**.

###### Implementation of the Object `deque`
**Steps**
  1. Import the object `deque`from the module `collection`.

          from collections import deque

  2. Create a linked list with the object, `deque`.
    - You can either create an empty linked list or populate it by passing an iterable as input.

            # Create an empty linked list
            >>> deque()
            deque([])

            # Creating a populated Linked list
            >>> deque([1,2,3,4,5])
            deque([1,2,3,4,5])


  3. And now simply add or remove elements from the ends of the linked list.
    - Adding and removing from the end.

            # Add element to the end of the linked list
            >>> lnkLst = deque("abcde")
            >>> lnkLst
            deque(['a','b','c','d','e'])
            >>> lnkLst.append('f')
            >>> lnkLst
            deque(['a','b','c','d','e','f'])

            # Delete element from the end of the linked list
            >>> lnkLst.pop()
            'f'
            >>> lnkLst
            deque(['a','b','c','d','e'])

    - Adding and removing from the start.

            # Add element to the start of the linked list
            >>> lnkLst.appendleft('q')
            >>> lnkLst
            deque(['q','a','b','c','d','e'])

            # Delete element from the start of the linked list
            >>> lnkLst.popleft()
            'q'
            >>> lnkLst
            deque(['a','b','c','d','e'])
