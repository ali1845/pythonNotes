# Inheritance

#### 1. Theory

  Inheritance is a **'Is a'** relationship. It is a process in which the subclass/child class takes on the attributes and methods of the parent class. i.e. *Derived* class, from a *Base* class, **is a** specialized version of the *Base* class.

**Base/Super/Parent Class:** A class that is inherited from another class.

**Child/Subclass/Derived Class:** A class that inherits the attributes from the Parent class.


  A subclass can have its own defined methods and attributes, also it inherits all the methods and attributes from its parent class. Methods and attributes from the parent class can also be overridden or extended in the child class.

##### For example

There is a superclass called *Building* and the derived class from that base class is called *House*. So the Inheritance relationship states that a *House* **is a** *Building*. As *House* inherits the implementation and the interface of the *Building* class. Objects of the derived class, *House* should replace the Objects of a base class, *Building*.

##### Liskov Subsitution Principl:
  States that in a computer program, if D is a subtype of S, then the Objects of type S may be replaced with the Objects type D, without altering any of the desired properties of the program.

Since in python everything is an Object. Let us start with how Python implements OOP at its core.

### 2. Core Inheritance in Python

Inheritance is a required feature for any Object-Oriented Programming language and Python supports it. Every Module, Class definition, function, and Object is derived from a parent class, called `object()`, and all of these are the Objects of that class in python. However, Exceptions (Errors) in python are the exceptions. Exceptions in Python are created using another class, called `BaseException()`.

  #### The object() Super Class in Python
  Every Superclass that you create drives from a built-in Superclass, called `object()`. That means it implements the interface and uses all the functionalities of the `object()` class.

  i.e. Create a class in python:

        >>> class MyClass:
        ...     pass
        ...

  Now create an object and use the dir() function to display its members.

        >>> c = MyClass()
        >>> dir(c)
        ['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__',
        '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__',
        '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__',
        '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__',
        '__str__', '__subclasshook__', '__weakref__']

  Now check out the members of the object() class.

        >>> o = object()
        >>> dir(o)
        ['__class__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__',
        '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__',
        '__init_subclass__', '__le__', '__lt__', '__ne__', '__new__', '__reduce__',
        '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__',
        '__subclasshook__']

Each member of the object() class is also present in the class, `Myclass`. Although my class may have some additional members.


#### Exception
However, there is an exception to this. Classes that create an Exception(Error Class) in python do not drive from the object() class.

There is a specific class, called `BaseException` that provides all the error types in Python.

The convention is to drive your custom Error class from the `**Exception**` class, which is a subclass of the `BaseException` class.

  **Example**

    >>> class MyError(Exception):
    	pass

    >>> raise MyError()
    Traceback (most recent call last):
      File "<pyshell#13>", line 1, in <module>
        raise MyError()
    MyError


### Inheritance implementation in Python

- Lets create a parent class `Email` in which we have three Methods, sendDetails(), attachmentsDetails() and the Construtor, `__init__()`.
- A child class `Type`.

      class Email:

          def __init__(self, subject, body):
              self.subject = subject
              self.body = body

          def sendDetails(self):
              return f"The Subject, {self.subject} and the message, {self.body} has been sent"

          def attachmentsDetails(self, add):
              return f"The Subject, {self.subject} and the message, {self.body} has the following attachment, {add}"

      class Type(Email):
          pass


Since the Child class, Type, inherits the Parent class, Email, it also inherits all the attributes and methods of the parent class.

**Run and see the output**

    >>> emlTmp = Type("Helloooo", "This is me")
    >>> emlTmp.subject
    'Helloooo'

  - We created an Object of the class Type, `emlTmp`.
  - Since the class type is derived from the Email class. It also inherits the Constructor, so while creating the Object we have to initialize it as well.
  - Then we called the instance attribute, `subject`, using the Type Object.

##### isinstance() function:
- Takes two arguments, an object, and a class.
- Returns a boolean value and checks if an instance belongs to the class or not.
- It will return a True value for the parent class as well.
- **Example**

      >>> isinstance(emlTmp, Type)
      True
      >>> isinstance(emlTmp, Email)
      True

##### Overriding Parent Methods

You can override methods from the Parent class by adding a method with the same name in the child class.

For example, HR Department has to send an email to several departments of your office with a specific attachment to each department.

- So for each department will be a new subclass for the Email class.
- And the attachmentsDetails() method will be overridden for each subclass.

**Example**

- Approach 1

    # Subclass
    class ITDep(Email):
        def attachmentsDetails(self, add = "IT Department File"):
            return f"THIS EMAIL IS FOR IT DEPARTMENT: {self.subject}, {self.body}. Find the following attachment, {add}"

      >>> ITeml = ITDep("This email is for IT Department", "This email has been sent to the employees of IT Department")

      >>> ITeml.attachmentsDetails()
      'THIS EMAIL IS FOR IT DEPARTMENT: This email is for IT Department, This email has been sent to the employees of the IT Department. Find the following attachment, IT Department File'

      >>> ITeml.attachmentsDetails("New attachmenttt")
      'THIS EMAIL IS FOR IT DEPARTMENT: This email is for IT Department, This email has been sent to the employees of the IT Department. Find the following attachment, New attachment

- Approach 2

  **Use super()**

  - You can access the parent class method from inside a method of a child class as well.
  - This won't change the default string in the parent class only the attachment.

    **i.e**

          # Subclass
          class ITDep(Email):
              def attachmentsDetails(self, add = "IT Department File"):
                  return super().attachmentsDetails(add)
          >>> ITeml.attachmentsDetails()
          'The Subject, This email is for IT Department and the message, This email has been sent to the employees of IT Department has the following attachment, IT Department File'

whitenarydairy@gmail.com
Chaunsanabeel@21

**Note**

As long as methods or attributes are not overridden in the subclass, any change in the Parent class will automatically propagate in the child class.
