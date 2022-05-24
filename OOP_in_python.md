# Object Oriented Programming (OOP)

### 1. Object-Oriented Programming:

Object-Oriented Programming is a method that bundles the related properties/attributes and behaviors of a program and organizes it around individual **objects**.

OOP models real-world entities as Software Objects that have some data associated with them (*attributes*) and can perform certain functions (*behaviors*).

##### Difference between classes and primitive Data structures in python:
The primitive Data structure, like lists, integers, and strings, is used to hold simple information, i.e. age of a person, the name of a person, or a list of hobbies of a person.

What if we want to represent all the people in a person's family? To manage and maintain this more complex problem is to use *classes* rather than these primitive DS because it will be harder to manage and maintain that.

### 2. Classes

***Classes*** are just like the template in which you can add the data. A blueprint for an **Object**.

##### implementation of a Class:

**Class** is defined using a *class* keyword following the name of the class. By convention name of the class is written in CapitalizedWords notation.

    class Email:
        # body of the class


### 3. Object:

- **Object** of a class is also known as an **instance**
- That is built from the class and it contains the real data as well as the overall structure of the program.
- An Instance uses the attributes and methods of the class.
- Instantiating an Object means creating a new object.
- Instantiate a new object by simply typing the class name with parentheses.

i.e.

    class Email:
        # body of the class

     # Run
     eml = Email()
     eml1 = Email()

     eml == eml1
     # Output
     False

 ###### Explanation
 - Two Person objects have been Instantiated and were assigned to a different variable
 - p1 is not equal to p2 because each Email instance is unique and located at a different memory address.

##### Relationship between an instance and a class:

The relationship between an Object and a class is just like the relationship between a laptop and Lenovo. A laptop is an abstract concept. Whereas, Lenovo is a laptop.

So the abstract class, Laptop, is implemented from Legion, HP, Dell, etc.


### 4. Attributes:
Attributes are the properties that an object holds. Objects are used to access the attributes of the class. In easy words, attributes are just the variables that are declared inside the class, which defines the properties of the class.

Other than user-defined attributes, every Object in Python has some default attributes as well.

- To see all the attributes and all the methods of an object in a class in Python, the built-in function `dir()` is used.

      >>> eml = Email()
      >>> dir(eml)
      ['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__',
      '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__',
      '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__',
      '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__',
      '__str__', '__subclasshook__', '__weakref__']


**Note:**
   The origin of default attributes and methods in python is discussed in detail in the **inheritance** section.

#### Instance and Class attributes
In general, there are two types of Attributes. **Class** and **Instance**.

###### Class attributes
Class attributes are the attributes that are created outside the methods and inside the class. They are shared by all the objects of the class.

By convention, the name of the class attribute is referred to by the class name.


    class Email:
        # Class attribute
        email_message = "Thank You! Regards"


###### Instance attributes
Instance attributes are created inside any method. They are the exclusive property of an instance/object. It defines all the properties each instance should have.


    class Email:
        # Class attribute
        thanksMessage = "Thank You! Regards"

        # Constructor
        def __init__(self, subject):
            self.subject = subject

        def sendDetails(self, message):
            # instance attribute
            self.message = message
            return f"The Subject, {self.subject} and the message, {self.message} has been sent"


- Instance attributes are referred to using the keyword `self`.

- The values of the instance attributes are passed as an argument of any method.

- We have created two methods one is a Constructor and the other is a `sendDetails()`.

-  `subject` is the instance attribute created in the Constructor and the `message` attribute is created in the `sendDetails()` method.


#### Example of Class and Instance Attributes

Let's create an object of the class Email and call the method sendDetails.

Since the Dunder method, `.__init__()`, is defined. We need to instantiate the class object by passing the values of the Instance attributes.

Python creates a new instance and passes it to the first parameter of the `.__init__()` function, `self`.

To call the methods and attributes of any class we use **dot notation**

    class Email:
        # Class attribute
        thanksMessage = "Thank You! Regards"

        # Constructor
        def __init__(self, subject):
            # instance attribute
            self.subject = subject

        # Instance method
        def sendDetails(self, message):
            # instance attribute
            self.message = message
            print("Message sent!")


    eml1 = Email("To whom it may concern")
    eml1 = Email("Notes")


In REPL

    # Accessing Instance attribute of __init__
    >>> eml1.subject
    'To whom it may concern'

    # Accessing Instance attribute of other methods
    >>> eml1.sendDetails("There?")
    >>> eml1.message
    'There?'

    # Accessing the Class attribute of the class
    >>> eml1.thanksMessage
    'Thank You! Regards'


The custom Objects are **mutable**. As the values of instances in a class can be changed.


        >>> eml1.subject
        'To whom it may concern'

        >>> eml1.subject = "Hello there!"
        >>> eml1.subject
        'Hello there!'

 ### 4. Methods
*Methods* are the functions that define the functionalities and the behavior of an object.

In general, there are three types of methods;

   1. Instance Methods
   3. Class Methods
   2. Static Methods


#### 4.1. Instance Methods

The most common methods are the **Instance method**. The first parameter of each Instance Method is *self*. Which points to an instance of the class when the method is called.

Instance methods are very powerful. As they can easily access the attributes and other methods on the same object. They can also access the class through `self.__class__`.

 ###### Example

 Create an instance method, `sendDetails()` in the `Email` class.

    class Email:
        # Class attribute
        thanksMessage = "Thank You! Regards"

        # Constructor
        def __init__(self, subject):
            self.subject = subject

        # Instance Methods
        def sendDetails(self, message):
            # instance attribute
            self.message = message
            return f"The Subject, {self.subject} and the message, {self.message} has been sent"

 In REPL:

    # Create an Instance
    >>> eml = Email("Hello World!")

    # Calling the Instance method
    >>> eml.send details("I am learning python has been sent")
    'The Subject, Hello World! and the message, I am learning python has been sent'

- Python replaces `self` with the instance Object, `eml`, when the method, `sendDetails()`is called.

#### 4.2. Class Methods

`@classmethod` decorator is used to flag a **Class method**. This method can be called directly using the name of the class. Since these methods do not use the `self` parameter. Instead, they use the class as their parameter that points at the class, i.e. `cls`.

The class method does not have access to the `self` parameter. So they can only modify the members of the class, which applies to all instances of the class. i.e. They cannot modify the instance members. As they are unaware of that.

We generally use class methods for **Factory Methods**. They return the class object, similar to the constructor, `__init__()`
###### Example

Create a class method, `sendDetails()` in the `Email` class.

    class Email:
        # Class attribute
        thanksMessage = "Thank You! Regards"
        # Constructor
        def __init__(self, subject):
            self.subject = subject

        # Instance Method
        def sendDetails(self, message):
            # instance attribute
            self.message = message
            return f"{self.subject}, {self.message}"

         # Class Method
        @classmethod
        def itEmail(cls, subject):
            return cls(subject)

        @classmethod
        def hrEmail(cls, subject):
            return cls(subject)


In REPL:

    # Object with instance
    >>> eml = Email('Hello')

    # Objects with Class Methods
    >>> itEml = Email.itEmail('IT Personnel')
    >>> hrEml = Email.hrEmail('To HR departmant')

    # Calling Instance method
    >>> eml.sendDetails("This is a general message")
    'Hello, This is a general message'

    # Calling Instance method using class methods
    >>> itEml.sendDetails("This is message is for IT PERSONNEL")
    'IT Personnel, This is message is for IT PERSONNEL'

    >>> hrEml.sendDetails("This is message is for HR DEPARTMENT")
    'To HR departmant, This is message is for HR DEPARTMENT'


#### 4.3. Static Methods
`@staticmehtod` decorator is used to flag the **Static method**. The static method can be called directly using the name of the class. These are bound to the class, not to the object of the class. They don't need any specific parameter, i.e. `self` or `cls`.

Static methods can not modify the state of the nor of any instance, they are primarily used for namespace your methods.

We generally use Static methods to create **Utility Functions**

    class Email:
        # Class attribute
        thanksMessage = "Thank You! Regards"
        # Constructor
        def __init__(self, subject):
            self.subject = subject

        # Instance Method
        def sendDetails(self, message):
            # instance attribute
            self.message = message
            return f"{self.subject}, {self.message}"
        ...
        ...
        ...
        # Static Method
        @staticmethod
        def msgLen(msg):
            return len(msg)

In REPL

    # Calling Static method
    >>>Email.msgLen("This is message is for HR DEPARTMENT")
    36


### 5. Dunder Methods

Methods starts with double underscores are called **Dunder Methods**. e.g `.__init__()` and `.__str__()`.

#### Method `.__init__()`:

The dunder method `.__init__()`, also known as the Constructor. It is called by default whenever a new object is created. The `.__init__()` method sets the initial state of the object. The first parameter is always `self` and it can take any number of parameters.

So whenever a new instance is created it is automatically passed to the self variable where new attributes are defined on the object.

    class Email:
        # Constructor
        def __init__(self, subject):
            self.subject = subject
        ...
        ...
        ...


#### Method `.__str__()`:

Since everything in Python is an object and every object has the `__str__()` method by default. So when we use an object as a string the `__str__()` method is called.

By default

    class Email:
        # Constructor
        def __init__(self, subject):
            self.subject = subject
        ...
        ...
        ...

In REPL

    >>> eml = Email("Hello there!")
    >>> print(eml)
    <__main__.Email object at 0x000002923272AC40>

In the above script we use our Email class object, `eml` as a string, and the default `__str__()` method is called and it prints the memory location of the object where it is stored.

However, we can create our own `__str__()` method in our class.

After creating `__str__()`

    class Email:
        # Constructor
        def __init__(self, subject):
            self.subject = subject

        # .__str__() method
        def __str__(self):
          return "Email class Object"
        ...
        ...
        ...

In REPL

    >>> eml = Email("Hello there!")
    >>> print(eml)
    Email class Object



### 5. Local and global variables:

#### Local variables:
Local variables are the variables that are defined inside a method. A local variable can only be accessed inside the method.

    class Email:
        ...
        ...
        ...
        # Instance Method
        def sendDetails(self, message):

            # Local variable
            samMsg = "Hello world!"

            # instance attribute
            self.message = message
            return f"{self.subject}, {self.message}"


We have created a local variable, `Samsung` inside the `sendDetails()`. We cannot access a local variable outside the block in which it is defined. Example;

    >>> eml = Email("Yo")
    >>> eml.samMsg
    AttributeError: 'Email' object has no attribute 'samMsg'

##### Difference between local variable and instance attribute is that.

**Instance attributes** are defined using the `self` keyword. And it can be accessed between the methods of the same class.

**Local variable** Cannot be accessed outside the code block in which it is defined. It doesn't use any special keyword, like `self`.

#### Global variable:
Variables that are defined outside the code block, i.e. method. It can be accessed anywhere inside the class.

    class Email:
      globMsg = "Global message!"
        ...
        ...
        ...
        # Instance Method
        def sendDetails(self, message):

            # Local variable
            samMsg = "Hello world!"

            # instance attribute
            self.message = message
            return f"{self.subject}, {self.message}"

We have created a global variable, `globMsg`. Which can be shared in all the methods that are defined inside the class.

### 6. Access modifiers

**Access modifiers** are used to modify the default scope of the members of the class and restrict their access.

In python 'underscore' (`_`) is used to determine the access control of a variable. Access specifiers help secure the data from unauthorized access, preventing data from being exploited.

There are three kinds of access modifiers;

1. Public Access Modifiers,
2. Protected Access Modifiers (`_`).
3. Private Access Modifiers, (`__`)

###### 1. Public Access Modifiers
Members that can be accessed anywhere, inside or outside the class, are public access modifiers.

By default all the members, i.e. methods and variables, are public.

###### 2. Protected Access Modifiers
Members that are accessible within the class and the class derived from it are protected access modifiers.


    class Email:

        # Protected variable
        _message = "Protected Access Modifier Message"

        # Constructor
        def __init__(self, subject, protSubj):

            # Protected variable
            self._protSubj = protSubj
            self.subject = subject

        def sendDetails(self, message):
            samMsg = "Hello world!"
            self.message = message
            return f"{self.subject}, {self.message}"


        >>> eml = Email("Sunject", "protected subject")
        >>> eml._protSubj
        'protected subject'


###### 3. Private Access Modifiers
Members that can only be accessed inside the class are private access modifiers. These are the most secure access modifiers, as they cannot be even accessed with the class object. You can only use them within the class to print them on the screen.

    class Email:

        # Protected variable
        _message = "Protected Access Modifier Message"

        # Private variable
        __priMesg = "This message is private"

        # Constructor
        def __init__(self, subject, protSubj):

            # Protected variable
            self._protSubj = protSubj
            # Private variable

            self.subject = subject

        def sendDetails(self, message):
            samMsg = "Hello world!"
            self.message = message

            # Using Private variable inside the class
            return f"{self.subject}, {self.message}, {sel.____priMesg}"


      >>> eml = Email("Subject", "protected subject")
      >>> eml.__priMesg
      AttributeError: 'Email' object has no attribute '__priMesg'

You will get an attribute error if you try to access the private variable outside the class. However;

    >>> eml.sendDetails("Helloooo")
    'Subject, Helloooo, This message is private'
