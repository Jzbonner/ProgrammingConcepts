# Object Oriented Thought Process 
An in depth looked at Object Oriented Programming Concepts ranging from classes and objects to relational databases and client/server applications. Developers will be able to utilize these notes for practical and real world applicable design patterns in object oriented programming environments. 

## Introduction to Object-Oriented Concepts ~ Chapter 1
Object Wrappers are object oriented code that includes other code inside. You can also use object wrappers to wrap functionality such as security features, non-portable hardware features and so on. Developers who can combine the skills of mainframe and web development are in demand. 

An object is an entity that contains both data and behavior. In procedural programming code is placed into totally distinct functions or procedures; these procedures then become "black boxes" where input goes in and output comes out. In object oriented design, the attributes and behaviors are contained within a single object; there is no separation. In structured programming data is often separate from the procedures, at times this data is global (meaning it can be easy to modify that data outside the scope of your code). In Object Oriented design there is no such thing as data that is global. In object oriented programming methods are used to perform operations on the data as well as other actions. 

Object Oriented Design | 
--- |
* __Data__ is referred to as attributes. Data stored within an object represents the state of the object. 
* __Behaviors__ are referred to as methods. This is essentially what the data can do. In procedural programming the behavior is defined by procedures, functions and subroutines. In Object Oriented Programming these behaviors are contained in methods and you invoke a method by sending a message to it. 

![Diagram 1](https://github.com/Jzbonner/ProgrammingConcepts/blob/gh-pages/img-media/OOTP%20Ch.1%20Diagram%201.png)

> Procedural Programming normally separates the data of a system from the operation that manipulate the data. For example, if you want to send information across a network, only the relevant data is sent, with the expectation that the program at the other end of the network pipe knows what to do with the it. The fundamental advantage of Object Oriented programming is that data and the operations that manipulate the data (the code) are both encapsulated in the object.  

(_Object Oriented Thought Process_, Ch. 1)

The concept of Getters and Setters supports the concept of data hiding. Because other objects should not directly manipulate data within another object, the getters and setters provide controlled access to an object's data. Getters and Setters are sometimes referred to as accessor methods and mutator methods, respectively. 

### Example of Concepts 
![Diagram 2](https://github.com/Jzbonner/ProgrammingConcepts/blob/gh-pages/img-media/OOTP%20Ch.1%20Diagram%202.png)

The above is a UML Class Diagram that consist of three main parts: the name itself, the data (attributes) and the behaviors (methods). As you can see the Employee class diagram contains the attributes _SocialSecurityNUmber_, _Gender_, and _DateofBirth_. While the method section contains the behaviors that operate on those attributes. For now think of classes as templates from which objects are made. When objects are created we say that the objects are _instantiated_ (i.e. creating three real world employees using the above class structure would result in three instances of the Employee class). As you can see a _class_ is a blueprint for an object. In Object Oriented Programming the class always comes before the object, meaning an object can not be instantiated without a class. An implementation of a class and object relationship would look as follows: 
```java 
public class Person {
    //Attributes 
    private String name; 
    private String address; 

    //Methods 
    public String getName() {
        return name; 
    }

    public void setName(String n) {
        name = n;
    }

    public String getAddress() {
        return address; 
    }

    public void setAddress(String adr) {
        address = adr; 
    }
}
```

> When working in Java, a data type or method is defined as public, meaning other objects can directly access it. When a data type is defined as private, only that specified object can access it. In the person class, the behaviors `getName()`, `setName()`, `getAddress`, and `setAddress` allow other objects to inspect and change the values of the object's attributes. Messages are the communication mechanisms between objects. For instance when Object A invokes a method of Object B, it is really sending a message to Object B.

(_Object Oriented Thought Process_, Ch.1)

Let's take a look at another example of attributes, methods and messages in Java: 
```java 
public Class Payroll() {

    String name; 

    Person p = new Person(); // interaction with the previous Person class

    String = p.setName("Joe"); // Message being sent to the Person class

    ... code // additional code 

    String = p.getName(); // Message being received from the Person class
}
```

Encapsulation and Data Hiding | 
--- | 

In good Object Oriented Design an object should only reveal interfaces that other objects must have to interact with it. Details not pertinent to the use of the object should be hidden from all other objects. Essentially data hiding is a part of encapsulation. The basics of encapsulation involve _interface_ and _implementation_. 

The interface defines the fundamental means of communication between objects. The interface should completely describe how users of the class interact with the class. In java, for example, the methods that are part of the interface are designated with the `public` keyword. Yes there are interfaces to classes as well as methods, however it is important to remember that interfaces to the classes are the public methods while the interface to the methods relate to how you can call or invoke them in other objects. 

### Modeling Interface and Implementation Paradigms 
Let's assume that we are attempting to write the code for a class that calculates the squares of integers. In order to do this we will need a proper interface and implementation. Take notice of two important things in the code snippet below, the interface used to prime the calculation of the square integer and return the squared value is made public so that it can be accessed by other objects. The actual implementation of calculating the square integer should only be seen by the intSquare class so it is made private. 
```java 
public class intSquare {

    // private attribute that's only accessible to everything inside this class and nothing else
    private int squareValue; 

    // public interface 
    public int getSquare(int value) {
        squareValue = calculateSquare(value);
        return squareValue; 
    }

    // private implementation
    private int calculateSquare(int value) {
        return value*value; 
    }
}
```

### Inheritance 
One of the most powerful features of object oriented programming is code reuse. Object Oriented programming allows you to define relationships between classes that facilitate not only code reuse, but also better overall design. _Inheritance_ allows a class to inherit the attributes and methods of another class. 
![Diagram 3](https://github.com/Jzbonner/ProgrammingConcepts/blob/gh-pages/img-media/OOTP%20Ch.1%20Diagram%203.png)

The superclass or parent class contains all attributes and behaviors that are common to classes that inherit from it. The `Mammal` class would be seen as the parent class, since it contains general attributes and behaviors that are customary of a wide range of sub classes (i.e. eye color, hair color, generate body heat, etc.). The `dog` and `cat` sub classes inherit those commons traits (attributes and behaviors) and only needs to be defined by those attributes and behaviors that make it solely a cat. In some Object Oriented Languages a class can only have one parent class, this is known as __single-inheritance__; however in other Object Oriented Languages a class can have multiple parent class, this is known as __multi-inheritance__. 

### Is-A Relationships, Has-A Relationships and Inheritance/Composition 
__Polymorphism__ is often tightly coupled with inheritance but distinctly it is of the defining principles of Object Oriented Programming. In an inheritance hierarchy all subclasses inherit their interfaces from their superclass. However, because each subclass is a separate entity, each might require a separate response to the same message. This is known as polymorphism. 

Examples of Polymorphism with Shapes | 
--- |

Consider the following hierarchy: 

![Diagram 4](https://github.com/Jzbonner/ProgrammingConcepts/blob/gh-pages/img-media/OOTP%20Ch.1%20Diagram%204.png)

Clearly the _Circle_, _Square_, and _Star_ subclasses all inherit their interface through the _Shape_ superclass. This relationship is typically defined as an __is-a relationship__; because circle, square and star are all extensions of the _Shape_ class. Thus circle `is-a` shape, square `is-a` shape and star `is-a` shape. The `Draw()` method (derived from the shape superclass) for each of the subclasses should return a different response depending on the specific subclass. Instead of providing the implementation for the `Draw()` method in the Shape superclass you would relegate that responsibility to each individual subclass (i.e. your circle, square or star subclass). Consider the following __Shape__ class and the `getArea()` method: 

```java 
public abstract class Shape() { // When a class is designated by the keyword 'abstract', a subclass must provide the implementation for the method 

    private double area; 

    public abstract double getArea(); // the public implementation that is left up to the subclasses to define 

}

// Code to represent the Circle and Square subclasses 

public class Circle extends Shape { // The 'extends' keyword indicates that the Circle subclass inherits from the Shape superclass

    double radius; 

    public Circle(double r) { // This is a constructor 

        radius = r; 

    }

    public double getArea() { // polymorphism right here. The 'getArea()' implementation from the Shape superclass is now defined here

        area = 3.14*(radius*radius); 
        return area; 

    }
}

public class Rectangle extends Shape {

    double length; 
    double width; 

    public Rectangle(double l, double w) {

        length = l; 
        width = w; 
    }

    public getArea() {

        area = length*width; 
        return area; 
    }
}

// Instantiate the shape class by referencing the specific subclass and pointing to its specific constructor then defining the 'new' constructor; afterwards load the subclass shapes into a stack that references the superclass Shape and print the associated subclass areas from the stack. 

Circle circle = new Circle(5); 
Rectangle rectangle = new Rectangle(4,5); 

stack.push(circle);
stack.push(rectangle); 

while (!stack.empty()) {

    Shape shape = (Shape) stack.pop();
    System.out.println("Area = " + shape.getArea()); 

}
```
> A stack is a data structure that is last-in, first-out system. It is like a coin changer, where you insert coins at the top of the cylinder and, when you need a coin, you simply take one off the top; which is the last one you inserted. Pushing an item onto a stack means that you are adding an item to the top. Popping an item off the stack means you are taking the last item off the stack. 

(_Object Oriented Thought Process_, Ch.1)

As you can see from the above example, objects are often built or composed from other objects: in Object Oriented programming this is known as __Composition__. With regards to Object Oriented Programming there are only two ways to build classes from other classes: Inheritance and Composition. Inheritance allows one class to inherit from another class allowing the abstraction of attributes and behaviors for common classes. For instance dogs and cats are both mammals. Meaning that _dog_ is-a _mammal_ and _cat_ is-a _mammal_. 

With composition we can build classes by embedding classes in other classes. If you look at the relationship between a Car and an Engine, it would make sense to abstract them so that you could utilize the Engine class in numerous Car classes. However you would not say that an Engine _is-a_ Car, instead you would say that the Car class _has-a_ Engine class. This is the idea behind composition. 

* _is-a_ describes inheritance relationships 
* _has-a_ describes composition relationships 

## How to Think in Terms of Objects ~ Chapter 2
~ Refer to notes on Github. 