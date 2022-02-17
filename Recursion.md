# RECURSION

- goes top to down and then go back to up.


### Defination
Refers to a coding tachnique in which a function call itself.
### Recursion in Python
Interpreter creates a new local namespace whenever a function is **defined** or **called**. This keeps the objects decleared in the seperate namespaces. So, it doesn't matter if the names of the objects or the functions are the same.

In other words, if a function is called recursively python will create a new namespace for the function each time it is being called.

    def function():
       x = "Ali"
       function()

Note that, in python there is limit in python to call recursively by default, *1000 times*, after whuch it will through an exception:

`RecursionError: maximum recursion depth exceeded`


### Recursive Defination
Technically, it is not right to perform recursion endlessly, without achieving any goal.

There are **two** very important things to take under consideration before wirting any recursive function.

1. One or multiple **Base Case(s)**,
   - To solve the function without recursion,
   - Telling the function when to stop.
2. **Reductive Case(s)** or **Recursive calls**, must reach closer to the base cases.

#### Basic Examples

The basic example of writing a recursive function's Base case is **zero**

    def recTimer(x):
        # to view the timer
        print(x)
        # Base case
        if x == 0:
            return
        # Recursive call
        else:
            recTimer(x - 1)


#### Factorial example
##### Steps of writing a Recursive Function
Lets calculate *factorial of n* integer, *n!* with the help of recursion.

n! is the product of all the integers from 1 to n.
i.e. n! = 1 x 2 x .... x n.

###### 1. Define a recursive function
Recursive defination for a factorial:

    n! = {1               for n = 0 or n = 1
         {n x (n - 1)!    for n >= 2

###### 2. Define Base Case(s) from the defination

There are **two base cases**, as shown in the defination, `n = 0` or `n = 1`. These are the cases that are resolvable without recursion.

###### 3. Define Reductive Case(s) from the defination

From the defination we can determine for any number greater than 1 is not solvable without recursion so and **reductive case** is defined as `(n-1)!`.

###### 4. Write the code

Now we have our base cases and the reductive cases. We are all set to write a recursive python function.

    def fectorial(n):
        # Base cases
        if n == 0:
            return 1
        elif n == 1:
            return 1
        else:
            return n * factorial(n-1)

We can also write the following as;

    def fectorial(n):
        return 1 if n <= 1 else n * factorial(n-1)


##### How it works

Lets see how recursion function is executing with some print statements.


    def factorial(n):
       print(f"factorial() called with n = {n}")
       return_value = 1 if n <= 1 else n * factorial(n -1)
       print(f"-> factorial({n}) returns {return_value}")
       return return_value


    factorial(4)

    factorial() called with n = 4
    factorial() called with n = 3
    factorial() called with n = 2
    factorial() called with n = 1
    -> factorial(1) returns 1
    -> factorial(2) returns 2
    -> factorial(3) returns 6
    -> factorial(4) returns 24
    24
  **Note** This example is directly copied from the RealPython Tutorials.

  When recursion function is called all the recursion calls gets executed first and pile up, for `n = 4, 3, 2, and 1`. Once it reaches the base case and no more recursion calls can be executed then all the recursion calls un-pile themseleves and returns the out, `1, 2, 6, and 24`.


#### Traverse Nested List example:

Lets start looking into each item that is present in a nested list.

    numbers = [1, [3, [9, 8], 5, 6], 55, [71, 89], 10]

**Leaf elements** are all the elements that are present in the nested list. There are several approaches to count the number of leaf elements in the list, e.g. using *iteration or recursion*.

###### Top level of the list
    for index, value in enumerate(numbers):
        print(index, value)

    0 1
    1 [3, [9, 8], 5, 6]
    2 55
    3 [71, 89]
    4 10

The algorithm to traverse each and every element in the list and its sublists goes like this;
  - Look over each element in the list.
  - Find a leaf element and count it as +1
  - Once sublist is traversed go back up and add the leaf elements of the sublist to the count and resume looking for other elements in the top level.

##### Recursively Traverse Nested List

Since, we have to look for the leaf elements in the list and if encounter a sublist we have to start looking into that list as well. Hence, recursion fits here perfectly. So, lets create a recursive funnction to traverse all the leaf elements and count them.
