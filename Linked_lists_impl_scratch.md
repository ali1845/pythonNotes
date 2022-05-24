# Implemention of Linked List

This section is going to implement the linked list from scratch in Python. Although, `collections.deque` is available for handling the linked list in Python. But implementing it can help you in:

  1. Enhancing your python algorithm skills.
  2. Learning Data Structure theory.
  3. Preparing for a job interview.


### Create your own Linked List in Python:

Process of creating your linked list.

- Class to represent your linked list. It contains the start, and head of your linked list.
- Class that represents the Node of your linked list. Which contains the data and the next pointer information.


1. Create a class to represent your linked list, you need this class to store the start, and head, of your linked list;

        class LinkedList:
            def __init__(self):
                self.head = None


2. Now create another class to represent each node of the linked list;

        class Node:
            def __init__(self, data):
                self.data = data
                self.next = None
