---
title: "Object Oriented Programming"
parent: "Part 4 - Object Oriented Programming"
permalink: /part4/1/
nav_order: 1
published: false
---

# Object Oriented Programming

We'll now begin our journey in to the world of object-oriented programming. We'll start with focusing on describing concepts and data using objects. From there on, we'll learn how to add functionality, i.e., methods to our program.

Object-oriented programming is concerned with isolating concepts of a problem domain into separate entities and then using those entities to solve problems. Concepts related to a problem can only be considered once they've been identified. In other words, we can form abstractions from problems that make those problem easier to approach.

Once concepts related to a given problem have been identified, we can also begin to build constructs that represent them them into programs. These constructs, and the individual instances that are formed from them, i.e., objects, are used in solving the problem. The statement "programs are built from small, clear, and cooperative objects" may not make much sense yet. However, it will appear more sensible as we progress through the course, perhaps even self-evident.

## Classes and objects

We've already used some of the classes and objects provided by C#. A class defines the attributes of objects, i.e., the information related to them (instance variables and properties), and their commands, i.e., their methods. The values of instance (i.e., object) variables define the internal state of an individual object, whereas methods define the functionality it offers.

A **Method** is a piece of source code written inside a class that's been named and has the ability to be called. A method is always part of some class and is often used to modify the internal state of an object instantiated from a class.

As an example, List is a class offered by C#, and we've made use of objects instantiated from it in our programs. Below, an List object named integers is created and some integers are added to it.

```cs
// we create an object from the List class named integers
List<int> integers = new List<int>();

// let's add the values 15, 34, 65, 111 to the integers object
integers.Add(15);
integers.Add(34);
integers.Add(65);
integers.Add(111);

// we print the size of the integers object
Console.WriteLine(integers.Count);
```

An object is always instantiated by calling a method that created an object, i.e., a constructor by using the new keyword.

A class lays out a blueprint for any objects that are instantiated from it. Let's draw from an analogy from outside the world of computers. Detached houses are most likely familiar to most, and we can safely assume the existence of drawings somewhere that determine what exactly a detached house is to be like. A class is a blueprint. In other words, it specifies what kinds of objects can be instantiated from it:

![House blueprints](https://github.com/centria/basic-coding/raw/master/assets/images/houses.jpg)

Individual objects, detached houses in this case, are all created based on the same blueprints - they're instances of the same class. The states of individual objects, i.e., their attributes (such as the wall color, the building material of the roof, the color of its foundations, the doors' materials and color, ...) may all vary, however. The following is an "object of a detached-house class":

![Single house](https://github.com/centria/basic-coding/raw/master/assets/images/singlehouse.jpg)

## Creating Classes

A class specifies what the objects instantiated from it are like.

* The **object's variables (instance variables)** specify the internal state of the object
* The **object's methods** specify what the object does

We'll now familiarize ourselves with creating our own classes and defining the variable that belong to them.

A class is defined to represent some meaningful entity, where a "meaningful entity" often refers to a real-world object or concept. If a computer program had to process personal information, it would perhaps be meaningful to define a seperate class Person consisting of methods and attributes related to an individual.

Let's begin. The example is using the **sandbox** from the exercises, so you can follow the instructions along. We'll assume that we have a project template that has an empty main program, called 
**Program.cs**. 

```cs
using System;
namespace sandbox
{
  class Program
  {
    public static void Main(string[] args)
    {

    }
  }
}
```

The next part follows [**this material**](https://docs.microsoft.com/en-us/dotnet/core/tutorials/with-visual-studio-code#add-a-class) for creating new classes in Visual Studio Code. You can, of course, use any editor you wish. This course material is intended for Visual Studio Code.

### Creating a new class

1. To add a new class, right click in the VSCode Explorer and select New File. This adds a new file to the folder you have open in VSCode.

As with variables and methods, the name of a class should be as descriptive as possible. It's usual for a class to live on and take on a different form as a program develops. As such, the class may have to be renamed at some later point

2. Name your file **Person.cs**. You must save it with a .cs extension at the end for it to be recognized as a csharp file.

Make sure the file Person.cs is in the same folder as **Program.cs**

3. Add this code to your file:

```cs
using System;

namespace sandbox
{
  public class Person
  {
    
  }
}
```

A class defines the attributes and behaviors of objects that are created from it. Let's decide that each person object has a name and an age. It's natural to represent the name as a string, and the age as an integer. We'll go ahead and add these to our blueprint:

```cs
public class Person {
    private string name;
    private int age;
}
```

We specify above that each object created from the Person class has a name and an age. Variables defined inside a class are called instance variables, or object fields or object attributes. Other names also seem to exist.

Instance variables are written on the lines following the class definition **public class Person {**. Each variable is preceded by the keyword private. The keyword private means that the variables are "hidden" inside the object. This is known as encapsulation.

In the class diagram, the variables associated with the class are defined as "variableName: variableType". The minus sign before the variable name indicates that the variable is encapsulated (it has the keyword private).

![Class Diagram](https://github.com/centria/basic-coding/raw/master/assets/images/person.jpg)

We have now defined a blueprint -- a class -- for the person object. Each new person object has the variables **name** and **age**, which are able to hold object-specific values. The "state" of a person consists of the values assigned to their name and age.

The person doesn't do anything yet, but we'll get there.

## Defining a Constructor

We want to set an initial state for an object that's created. Custom objects are created the same way as objects from pre-made classes, such as List, using the **new** keyword. It'd be convenient to pass values ​​to the variables of that object as it's being created. For example, when creating a new person object, it's useful to be able to provide it with a name:

```cs
    public static void Main(string[] args)
    {
      Person ada = new Person("Ada");
      // ...
    }
```

This is achieved by defining the method that creates the object, i.e., its **constructor**. The constructor is defined after the instance variables. In the following example, a constructor is defined for the Person class, which can be used to create a new Person object. The constructor sets the age of the object being created to 0, and the string passed to the constructor as a parameter as its name:


```cs
public class Person
{
  private string name;
  private int age;

  public Person(string initialName) {
    this.age = 0;
    this.name =  initialName;
  }
}
```

The constructor's name is always the same as the class name. The class in the example above is named Person, so the constructor will also have to be named Person. The constructor is also provided, as a parameter, the name of the person object to be created. The parameter is enclosed in parentheses and follows the constructor's name. The parentheses that contain optional parameters are followed by curly brackets. In between these brackets is the source code that the program executes when the constructor is called (e.g., new Person ("Ada")).

**Objects are always created using a constructor.**

A few things to note: the constructor contains the expression **this.age = 0**. This expression sets the instance variable age of the newly created object (i.e., "this" object's age) to 0. The second expression **this.name = initialName** likewise assigns the string passed as a parameter to the instance variable name of the object created.

![Class Diagram With Constructror](https://github.com/centria/basic-coding/raw/master/assets/images/personconstructor.jpg)

If the programmer does not define a constructor for a class, the C# compiler automatically creates a default one for it. A default constructor is a constructor that doesn't do anything apart from creating the object. The object's variables remain uninitialized (generally, the value of any object references will be null, meaning that they do not point to anything).

For example, an object can be created from the class below by making the call **new Person()**

```cs
public class Person
{
  private string name;
  private int age;
}
```

If a constructor has been defined for a class, no default constructor exists. For the class below, calling new Person would cause an error, as the compiler cannot find a constructor in the class that has no parameters.

```cs
public class Person
{
  private string name;
  private int age;

  public Person(string initialName) {
    this.age = 0;
    this.name =  initialName;
  }
}
```

## Defining Methods For an Object

We know how to create an object and initialize its variables. However, an object also needs methods to be able to do anything. As we've learned, a **method** is a named section of source code inside a class which can be invoked.

```cs
public class Person
{
  private string name;
  private int age;

  public Person(string initialName) {
    this.age = 0;
    this.name =  initialName;
  }

  public void PrintPerson() {
    Console.WriteLine(this.name + ", age " + this.age + " years");
  }
}
```

A method is written inside of the class beneath the constructor. The method name is preceded by **public void**, since the method is intended to be visible to the outside world (**public**), and it does not return a value (**void**).

We've used the modifier **static** in some of the methods that we've written. The static modifier indicates that the method in question does not belong to an object and thus cannot be used to access any variables that belong to objects.

Going forward, our methods **will not include the static keyword** if they're used to process information about objects created form a given class. If a method receives as parameters all the variables whose values ​​it uses, it can have static modifier.

In addition to the class name, instance variables, and constructor, the class diagram now also includes the method PrintPerson. Since the method comes with the **public** modifier, the method name is prefixed with a plus sign. No parameters are defined for the method, so nothing is put inside the method's parentheses. The method is also marked with information indicating that it does not return a value, here **void**.

![Class Diagram With Constructror](https://github.com/centria/basic-coding/raw/master/assets/images/printperson.jpg)