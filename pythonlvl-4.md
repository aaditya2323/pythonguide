# Object Oriented Programming 

#### What is OOP (Object Oriented Programming )?
- OOP is a programming paradigm based on the concept of "objects", which can contain data, in the form of fields (often known as attributes or properties), and code, in the form of procedures (often known as methods).
- A feature of objects is that an object's procedures can access and often modify the data fields of the object with which they are associated (objects have a notion of "this" or "self"). 
- In OOP, computer programs are designed by making them out of objects that interact with one another. OOP languages are diverse, but the most popular ones are class-based, meaning that objects are instances of classes, which also determine their types.

#### What is a class?
- A class is a blueprint for the object.
- A class is a template for objects. It defines object's properties and methods without actually implementing them.
- A class is a user defined data-type which has data members and member functions.
- A class is a collection of objects of similar type.
- A class is a logical entity.

#### What is an object?
- An object is an instance of a class.
- An object is a real world entity.
- An object is a run-time entity.
- An object is a physical entity.
- An object is a concrete entity.

*example*
```python 
class Human:
    name = "Kushal"

h1=Human()
print(h1.name)
```
#### What is a constructor?
- A constructor is a special type of method (function) which is used to initialize the instance members of the class.
- Constructor is called automatically when the object is created.
- Constructor is used to initialize the object.
- Constructor is used to allocate memory to the object.

```python
class Human:
    def __init__(self):
        print("Constructor is called")

h1=Human()
```
#### What is self?
- self is a reference variable which refers to the current object.
- self represents the instance of the class.

```python
class Human:
    def __init__(self):
        print("Constructor is called")
        print(self)

h1=Human()
print(h1)
```
#### What is the difference between a function and a method?
- A function is a piece of code that is called by name. It can be passed data to operate on (i.e. the parameters) and can optionally return data (the return value). All data that is passed to a function is explicitly passed.

- A method is a piece of code that is called by a name that is associated with an object. In most respects it is identical to a function except for two key differences that are as follows:
1. A method is implicitly passed the object on which it was called.
2. A method is able to operate on data that is contained within the class (remembering that an object is an instance of a class - the class is the definition, the object is an instance of that data).

#### What is the difference between a class variable and an instance variable?
- Class variable is shared by all the objects of the class.
- Instance variables are owned by the objects of the class.

```python
class Human:
    name = "Kushal" # class variable

    def __init__(self):
        self.age = 20 # instance variable

h1=Human()
h1.age = 21
h2=Human()
h2.age = 22:
print(h1.name)
print(h2.name)
print(h1.age)
print(h2.age)
```
*Example* 
Creating a class of person with methods properties and attributes 
```python
class Person:
    def __init__(self, name, age):
        self.name = name # attribute
        self.age = age # attribute

    def say_hello(self): # method
        print("Hello my name is " + self.name + " and I am " + str(self.age) + " years old")
    
    def change_name(self, new_name): 
        self.name = new_name
    
    def double_age(self):
        self.age *= 2
    
    @property
    def age(self):
        return self._age
    
    @age.setter
    def age(self, value):
        if value < 0:
            raise ValueError("Age cannot be negative")
        self._age = value

p1 = Person("Kushal", 20)
p1.say_hello()
p1.change_name("Iron Man")
p1.say_hello()
p1.double_age()

print(p1.age)

p1.age = 10
print(p1.age)

``` 
#### What is Inheritance?
- Inheritance is a mechanism in which one class acquires the property of another class.
- Inheritance is the process of defining a new class based on an existing class by extending its common data members and methods.
- Inheritance allows us to define a class in terms of another class, which makes it easier to create and maintain an application.
- The class whose properties are inherited by another class is called the Parent or Super class.

*example of single inheritance*
```python
class A:
    def feature1(self):
        print("Feature 1 is working")

    def feature2(self):
        print("Feature 2 is working")

class B(A):
    def feature3(self):
        print("Feature 3 is working")

    def feature4(self):
        print("Feature 4 is working")

a1 = A()
a1.feature1()
a1.feature2()
b1=B()
b1.feature1()
b1.feature2()
b1.feature3()
b1.feature4()
```
*example of multiple inheritance*
```python
class A:
    def feature1(self):
        print("Feature 1 is working")

    def feature2(self):
        print("Feature 2 is working")
    
class B:
    def feature3(self):
        print("Feature 3 is working")

    def feature4(self):
        print("Feature 4 is working")

class C(A,B):
    def feature5(self):
        print("Feature 5 is working")

c1 = C()
c1.feature1()
c1.feature2()

```

#### constructor in inheritance
```python
class Mammals:
    def __init__(self):
        print("Mammals are warm blooded and give birth to young ones.")
        give_birth = True
        Age = 0

class Cat(Mammals):
    def __init__(self):
        Mammals.__init__(self)
        self.lifes = 9

cat1 = Cat()
print(cat1.lifes)
```
#### Using Super method

```python
class Mammals:
    def __init__(self):
        print("Mammals are warm blooded and give birth to young ones.")
        give_birth = True
        Age = 0

class Cat(Mammals):
    def __init__(self):
        super().__init__()
        self.lifes = 9

cat1 = Cat()
print(cat1.lifes)
```
#### What is Polymorphism?
- Polymorphism is an ability (in OOP) to use common interface for multiple form (data types).
- Polymorphism is the ability of an object to take on many forms.
- Polymorphism is the ability of a message to be displayed in more than one form.
- Polymorphism is the ability of an object to perform differently in different situations.

*example*
```python
class VSCode:
    def execute(self):
        print("Compiling")
        print("Running")
    
class MyEditor:
    def execute(self):
        print("Spell Check")
        print("Convention Check")
        print("Compiling")
        print("Running")
    
class Laptop:
    def code(self, ide):
        ide.execute()

ide = VSCode()
lap1 = Laptop()
lap1.code(ide)
```

*example 2*

```python
from abc import ABC, abstractmethod
class Animal(ABC):
    def __init__(self, name):    # Constructor of the class
        self.name = name
    @abstractmethod
    def speak(self):              # Abstract method, defined by convention only
        raise NotImplementedError("Subclass must implement abstract method")
class Dog(Animal):
    def speak(self):
        return self.name+' says Woof!'
class Cat(Animal):
    def speak(self):
        return self.name+' says Meow!'
fido = Dog('Fido')
isis = Cat('Isis')
print(fido.speak())
print(isis.speak())
```
#### What is Encapsulation?
- Encapsulation is the process of binding the data members and member functions into a single unit.
- Encapsulation is the process of wrapping up of data and information under a single unit.
- Encapsulation is the process of hiding the internal details of an object from the outside world.
- Encapsulation is the process of making the fields in a class private and providing access to the fields via public methods.

*example*
```python
class Student:
    _age= 20 # protected variable

    def __init__(self):
        self.__id = 123 # private variable
        self.__name = "Kushal" # private variable

    def display(self):
        print(self.__id)
        print(self.__name)
    
s1 = Student()
print(s1._age)
s1.display()
```

#### What is Data Abstraction?
- Data abstraction is the process of hiding the internal details and showing only the functionality.
- Data abstraction is the process of hiding the implementation details from the user and only showing the functionality to the user.
- Data abstraction is the process of providing only the essential details to the user and hiding the implementation details.

*example*
```python
from abc import ABC, abstractmethod
class Car(ABC):
    def __init__(self, name):
        self.name = name
    @abstractmethod
    def drive(self):
        pass
    @abstractmethod
    def stop(self):
        pass
class Sportscar(Car):
    def drive(self):
        return 'Sportscar driving!'
    def stop(self):
        return 'Sportscar braking!'
class Truck(Car):
    def drive(self):
        return 'Truck driving slowly because heavily loaded.'
    def stop(self):
        return 'Truck braking!'

cars = [Truck('Bananatruck'),
Truck('Orangetruck'),
Sportscar('Z3')]
for car in cars:
    print(car.name + ': ' + car.drive())
```
#### What is a module?
- A module is a file containing Python definitions and statements.
- A module is a Python object with arbitrarily named attributes that you can bind and reference.
- A module can define functions, classes and variables. A module can also include runnable code.

*example*
```python
import math
print(math.sqrt(25))
```
in above example math is a module and sqrt is a function

#### What is a package?
- A package is a collection of modules.
- A package is a directory containing Python modules.
- A package can have modules or subfolders.

*example*
```python
from sklearn import datasets
iris = datasets.load_iris()
print(iris.data)
```
in above example sklearn is a package and datasets is a module

### [__name__ == "__main__"](#)
- Before executing code, Python interpreter reads source file and define few special variables/global variables.
- If the python interpreter is running that module (the source file) as the main program, it sets the special __name__ variable to have a value "__main__". If this file is being imported from another module, __name__ will be set to the module's name.
- __name__ is a built-in variable which evaluates to the name of the current module. Thus it can be used to check whether the current script is being run on its own or being imported somewhere else by combining it with if statement, as shown below.
- If the module is imported from another module, then __name__ will be set to that module's name.
- Every Python module has it's __name__ defined and if this is '__main__', it implies that the module is being run standalone by the user and we can do corresponding appropriate actions.

*example*
```python
def main():
    print("Hello World!")

if __name__ == "__main__":
    main()
```
in above example if we import this module in another module then main() function will not be executed but if we run this module then main() function will be executed

#### creating our own module
- create a file named mymodule.py
- write the following code in mymodule.py
```python
def greeting(name):
  print("Hello, " + name)
```
- create another file named myprogram.py
- write the following code in myprogram.py
```python
import mymodule

mymodule.greeting("Kushal")
```
- run myprogram.py

#### modules using class and objects
- create a file named classmodule.py
- write the following code in classmodule.py
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def myfunc(self):
        print("Hello my name is " + self.name)
```
- create another file named myprogram.py
- write the following code in myprogram.py
```python
from classmodule import Person

p1 = Person("Kushal", 20)
p1.myfunc()
```
- run myprogram.py

#### What is a namespace?
- A namespace is a collection of currently defined symbolic names along with information about the object that each name references.
- A namespace is a system to have a unique name for each and every object in Python.
- An object might be a variable or a method. Python itself maintains a namespace in the form of a Python dictionary.
- There is a global namespace, which is visible throughout the program and local namespace which is visible only to the function in which it is declared.

*example*
```python
def outer_function():
    a = 20 # local namespace
    def inner_function():
        a = 30 # local namespace
        print('a =',a)
    inner_function()
    print('a =',a)

a = 10 # global namespace
outer_function()
print('a =',a)
```
in above example there are three namespaces
1. local namespace of inner_function()
2. local namespace of outer_function()
3. global namespace

#### Exception Handeling 
- An exception is an event that occurs during the execution of a program that disrupts the normal flow of instructions.
- An exception is a Python object that represents an error.
- When a Python script raises an exception, it must either handle the exception immediately otherwise it terminates and quits.
- When an exception occurs, it causes the current process to stop and passes it to the calling process until it is handled.
- If not handled, our program will crash.
- When an exception occurs, the code following it will not be executed, and Python will try to find an exception handler.
- An exception handler is a block of code that can handle exceptions raised by some portion of a program.

*example*
```python
try:
   pass
except:
    pass
```
in above example we are trying to print a variable x which is not defined so it will raise an exception and the code following it will not be executed

#### The try and except Block
- The try and except block in Python is used to catch and handle exceptions.
- The try block lets you test a block of code for errors.
- The except block lets you handle the error.

*example*
```python
a= 10
b=0
try:
    print(a/b)
except:
    print("Hey, you cannot divide a number by zero")
```
```python
a=10
b=0
try:
    print(a/b)
except Exception as e:
    print(e)
```

#### Multiple Exceptions
- A try statement can have multiple different except blocks to handle different exceptions.
- Multiple exceptions can also be put into a single except block using parentheses, to have the except block handle all of them.

*example*
```python
try:
    a = int(input("Enter a:"))
    b = int(input("Enter b:"))
    print(a/b)
except ZeroDivisionError:
    print("Hey, you cannot divide a number by zero")
except ValueError:
    print("value error")
```

#### finally
- The finally block, if specified, will be executed regardless if the try block raises an error or not.
- The finally block gets executed no matter if the try block raises any errors or not.
- The finally block is used to release the resources like closing the file, closing the database connection etc.

*example*
```python
try:
    a = int(input("Enter a:"))
    b = int(input("Enter b:"))
    print(a/b)
except ZeroDivisionError:
    print("Hey, you cannot divide a number by zero")
except ValueError:
    print("value error")
finally:
    print("resource closed")
```

#### raise
- The raise keyword is used to raise an exception.
- You can define what kind of error to raise, and the text to print to the user.

*example*
```python
x = -1
if x < 0:
    raise Exception("Sorry, no numbers below zero")
```
#### magic python / dunder methods 
- Magic methods in Python are the special methods that start and end with the double underscores.

*example*
```python
class Employee:
    def __init__(self, fname, lname, salary):
        self.fname = fname
        self.lname = lname
        self.salary = salary

    def __add__(self, other):
        return self.salary + other.salary

    def __repr__(self):
        return 'Employee({},{},{})'.format(self.fname, self.lname, self.salary)

    def __str__(self):
        return 'The name of the employee is {}'.format(self.fname)

emp1 = Employee("Kushal", "subedi", 10000)

print(emp1)
print(repr(emp1))
print(str(emp1))
```

    
