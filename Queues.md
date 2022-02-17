###### Queues:
- Uses **FIRST-IN/FIRST-OUT**(FIFO) approach to retrieve an element.
- Have a **Front pointer** and **Rear pointer**.

  - **Front pointer** points the start Node of the list and **Rear pointer** points at the last Node of the list.


- When a new element is appended in the queue it added form the Rear end.

- Element is retrieved from the front of the queue.


### Implementing Queues using the Object `collections.deque`

##### enqueue
To add a value in the queue
##### dequeue
To remove the value from the queue

**Queues uses FIFO approach:**

First element inserted into the list should be the first one to com out.

###### Example
The first arrives at the restaurant will get in the queue first and rest will follow. So the first person enters the queue will get the order first.

- Creating a queue for the restaurant's orders using `deque`:

      from collections import deque

      # Create an empty Linkedlist
      >>> queue = deque()

      # Add values in the Linkedlist
      >>> queue.append('Ali')
      >>> queue.append('Kamran')
      >>> queue.append('Rubiya')
      >>> queue.append('Usama')
      >>> queue
      deque(['Ali','Kamran',Rubiya','Usama'])

- So now in order to make this Linkedlist work as a Queue.  Remove elements the first element that was entered in the list.
- We will be using the method `popleft()`

      # Remove the first person entered the queue, Ali
      >>> queue.popleft()
      'Ali'
      >>> queue.popleft()
      'Kamran'

- Every call of `popleft()` method will simply remove the head  element of the queue.
