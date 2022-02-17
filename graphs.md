
###### Graphs:
- Graphs are used to show relationship between Objects.
- There are many ways to implement graphs but the most common way is to use **Adjacency List**.

  Following is the representation of the Directed Acyclic Graph.

  ![Directed Acyclic Graph](https://files.realpython.com/media/Group_20.32afe2d011b9.png)

- **Adjacency List** is a list of linked lists where each vertex of the graph is stored alongside a collection of connected vertices.

- Implementing graphs using adjacency list is both time and memory efficient.

**i.e;**

  Node  |  Linked List containing corresponding Nodes
  --|--
  1 | 2->3->None
  2 | 4->None
  3 | None
  4 | 5->6->None
  5 | 6->None
  6 | None

- Each vertex/Node is on the left column of the table above
- And the series of linked list are on the right column.
- The series of linked lists represents the connection to the corresponding Nodes.
