###### Stacks:
- Uses **LAST-IN/FIRST-OUT**(FIFO) approach to retrieve an element.

- Have a **Top Pointer;**
  - Points at the last element inserted in the list.
  - The last element inserted is to be retrieved first.

It is very convenient to implement stacks and queues with linked.


### Implementing Stacks using the Object `collections.deque`


**Stacks uses LIFO approach:**

Last element inseted in the list should be the first one to come out.

###### Example
A history function in a web browser. That allows user to go back to the previous web page. So the last page a user visited will be loaded when the back button is pressed.

- Creating a stack for the web browser history using `deque`:

  - The url links of the history will be added in the stacks using `.appendleft()` because we want the last element added to the list at the top.

        from collections import deque

        # Empty history object
        histStack = deque()

        # Add the number of pages visited by the user in a stack
        >>> histStack.append('https://www.google.com')
        >>> histStack.append('https://www.geeksforgeeks.org/stack-data-structure/')
        >>> histStack.append('https://www.geeksforgeeks.org/fundamentals-of-algorithms/?ref=shm')

        # Display history content
        >>> histStack
        deque(['https://www.google.com', 'https://www.geeksforgeeks.org/stack-data-structure/', 'https://www.geeksforgeeks.org/fundamentals-of-algorithms/?ref=shm'])

  - However, to go back we must remove the last element from the TOP of the list, using `.popleft()`.

        >>> histStack.popleft()
        'https://www.geeksforgeeks.org/fundamentals-of-algorithms/?ref=shm'
        >>> histStack.popleft()
        'https://www.geeksforgeeks.org/stack-data-structure/'
        >>> histStack
        'https://www.google.com'



        
