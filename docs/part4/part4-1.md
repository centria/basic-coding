---
title: "Object Oriented Programming"
parent: "Part 4 - Object Oriented Programming"
permalink: /part4/1/
nav_order: 1
published: true
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

The next part is meant for creating new classes in Visual Studio Code. You can, of course, use any editor you wish. This course material is intended for Visual Studio Code.

### Creating a new class

1. To add a new class, right click in the VSCode Explorer and select New File. This adds a new file to the folder you have open in VSCode.

As with variables and methods, the name of a class should be as descriptive as possible. It's usual for a class to live on and take on a different form as a program develops. As such, the class may have to be renamed at some later point

2. Name your file **Person.cs**. You must save it with a .cs extension at the end for it to be recognized as a csharp file.

Make sure the file Person.cs is in the same folder as **Program.cs**

3. Make sure to include the correct **namespace** so you can reference it from your Program.cs file. 

We'll get to namespaces later. For now, whenever you create a new class, **use the folder name as the namespace**.

4. Add this code to your file:

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

![Class Diagram With Print](https://github.com/centria/basic-coding/raw/master/assets/images/printperson.jpg)

The method **PrintPerson** contains one line of code that makes use of the instance variables **name** and **age** -- the class diagram says nothing about its internal implementations. Instance variables are referred to with the prefix this. All of the object's variables are visible and available from within the method.

Let's create three persons in the main program and request them to print themselves:

```cs
class Program
{
  static void Main(string[] args)
  {
    Person ada = new Person("Ada");
    Person antti = new Person("Antti");
    Person martin = new Person("Martin");

    ada.PrintPerson();
    antti.PrintPerson();
    martin.PrintPerson();
  }
}
```

Prints:

```console
Ada, age 0 years
Antti, age 0 years
Martin, age 0 years
```

## Changing an Instance Variable's Value in a Method

Let's add a method to the previously created person class that increments the age of the person by a year.

```cs
public class Person
{
  private string name;
  private int age;

  public Person(string initialName)
  {
    this.age = 0;
    this.name = initialName;
  }

  public void PrintPerson()
  {
    Console.WriteLine(this.name + ", age " + this.age + " years");
  }

  public void GrowOlder()
  {
    this.age = this.age + 1;
  }
}
```

The method is written inside the Person class just as the printPerson method was. The method increments the value of the instance variable age by one.

The class diagram also gets an update.

![Class Diagram With Growth](https://github.com/centria/basic-coding/raw/master/assets/images/persongrow.jpg)

Let's call the method and see what happens:

```cs
static void Main(string[] args)
{
  Person ada = new Person("Ada");
  Person antti = new Person("Antti");
  Person martin = new Person("Martin");

  ada.PrintPerson();
  antti.PrintPerson();
  martin.PrintPerson();

  Console.WriteLine();

  ada.GrowOlder();
  antti.GrowOlder();
  antti.GrowOlder();

  ada.PrintPerson();
  antti.PrintPerson();
  martin.PrintPerson();
}
```

Prints

```console
Ada, age 0 years
Antti, age 0 years
Martin, age 0 years

Ada, age 1 years
Antti, age 2 years
Martin, age 0 years
```

That is to say that when the two objects are "born" they're both zero-years old (**this.age = 0**; is executed in the constructor). The **ada** object's GrowOlder method is called once, and **antti** object's GrowOlder is called twice.. As the print output demonstrates, the age of Ada is 1 years after growing older, for Antti it is 2. Calling the method on an object corresponding to Ada or Antti has no impact on the age of the other person object since each object instantiated form a class has its own instance variables, as can be seen from Martin.

The method can also contain conditional statements and loops. The GrowOlder method below limits aging to 100 years.

```cs
public class Person
{
  private string name;
  private int age;

  public Person(string initialName)
  {
    this.age = 0;
    this.name = initialName;
  }

  public void PrintPerson()
  {
    Console.WriteLine(this.name + ", age " + this.age + " years");
  }

  public void GrowOlder()
  {
    if (this.age < 100)
    {
      this.age = this.age + 1;
    }
  }
}
```

## Returning a Value From a Method

A method can return a value. The methods we've created in our objects haven't so far returned anything. This has been marked by typing the keyword **void** in the method definition.

```cs
public class Door 
{
  public void Knock() 
  {
      // ...
  }
}
```

The keyword **void** means that the method does not return a value.

If we want the method to return a value, we need to replace the void keyword with the type of the variable to be returned. In the following example, the Teacher class has a method **Grade** that always returns an integer-type (**int**) variable (in this case, the value 10). The value is always returned with the **return** command:

```cs
public class Teacher 
{
  public int Grade() 
  {
      return 10;
  }
}
```

The method above returns an **int** type variable of value 10 when called. For the return value to be used, it needs to be assigned to a variable. This happens the same way as regular value assignment, i.e., by using the equals sign:

```cs
class Program
{
  static void Main(string[] args)
  {
  Teacher teacher = new Teacher();

  int grading = teacher.Grade();

  Console.WriteLine("The grade received is " + grading);
  }
}
```

```console
The grade received is 10
```

The method's return value is assigned to a variable of type **int** value just as any other int value would be. The return value could also be used to form part of an expression.

```cs
static void Main(string[] args)
{
Teacher first = new Teacher();
Teacher second = new Teacher();
Teacher third = new Teacher();

double average = (first.Grade() + second.Grade() + third.Grade()) / 3.0;

Console.WriteLine("Grading average " + average);
}
```

```console
Grading average 10
```

All the variables we've encountered so far can also be returned by a method. To sum:

* A method that returns nothing has the **void** modifier as the type of variable to be returned.

```cs
public void MethodThatReturnsNothing() {
  // the method body
}
```

* A method that returns an integer variable has the **int** modifier as the type of variable to be returned.

```cs
public int MethodThatReturnsAnInteger() {
  // the method body, requires a return statement
}
```

* A method that returns a string has the **string** modifier as the type of the variable to be returned

```cs
public string MethodThatReturnsAString() {
  // the method body, requires a return statement
}
```

* A method that returns a double-precision number has the **double** modifier as the type of the variable to be returned.

```cs
public double MethodThatReturnsADouble() {
  // the method body, requires a return statement
}
```


Let's continue with the Person class and add a **ReturnAge** method that returns the person's age.

```cs
public class Person
{
  private string name;
  private int age;

  public Person(string initialName)
  {
    this.age = 0;
    this.name = initialName;
  }

  public void PrintPerson()
  {
    Console.WriteLine(this.name + ", age " + this.age + " years");
  }

  public void GrowOlder()
  {
    if (this.age < 100)
    {
      this.age = this.age + 1;
    }
  }

  // the added method
  public int ReturnAge()
  {
    return this.age;
  }
}
```

![Class Diagram With Return](https://github.com/centria/basic-coding/raw/master/assets/images/personreturn.jpg)

Let's illustrate how the method works:

```cs
static void Main(string[] args)
{
  Person pekka = new Person("Pekka");
  Person antti = new Person("Antti");

  pekka.GrowOlder();
  pekka.GrowOlder();

  antti.GrowOlder();

  Console.WriteLine("Pekka's age: " + pekka.ReturnAge());
  Console.WriteLine("Antti's age: " + antti.ReturnAge());
  int combined = pekka.ReturnAge() + antti.ReturnAge();

  Console.WriteLine("Pekka's and Antti's combined age " + combined + " years");
}
```

```console
Pekka's age: 2
Antti's age: 1
Pekka's and Antti's combined age 3 years
```

As we came to notice, methods can contain source code in the same way as other parts of our program. Methods can have conditionals or loops, and other methods can also be called from them.

Let's now write a method for the person that determines if the person is of legal age. The method returns a boolean - either **true** or **false**:

```cs
class Person
{
  //... The existing code could be up here

  public bool IsOfLegalAge()
  {
    if (this.age < 18)
    {
      return false;
    }

    return true;
  }

  /*
  The method could have been written more succintly in the following way:

  public bool IsOfLegalAge() 
  {
    return this.age >= 18;
  }
  */
}
```

And let's test it out:

```cs
static void Main(string[] args)
{
  Person pekka = new Person("Pekka");
  Person antti = new Person("Antti");

  int i = 0;
  while (i < 27)
  {
    pekka.GrowOlder();
    i = i + 1;
  }

  antti.GrowOlder();

  if (antti.IsOfLegalAge())
  {
    Console.Write("of legal age: ");
    antti.PrintPerson();
  }
  else
  {
    Console.Write("underage: ");
    antti.PrintPerson();
  }

  if (pekka.IsOfLegalAge())
  {
    Console.Write("of legal age: ");
    pekka.PrintPerson();
  }
  else
  {
    Console.Write("underage: ");
    pekka.PrintPerson();
  }
}
```

```console
underage: Antti, age 1 years
of legal age: Pekka, age 27 years
```

Let's fine-tune the solution a bit more. In its current form, a person can only be "printed" in a way that includes both the name and the age. Situations exist, however, where we may only want to know the name of an object. 

In many programming languages, you would write a **get method** for this. In C#, properties, such as our Person's **age** and **name**, can be used with [**Auto Implementation Property**](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties). 

```cs
public string name { get; }
```

Let's open this up a bit. "Under the hood", the code above tells our **C# compiler** that our property **name** has kind of "built-in" methods for getting an setting the value. The code above is equal in functionality to:

```cs
string _name;
public string name
{
  get
  {
    return _name;
  }
}
```

In this example, there is now also a line **string _name;**, and on both our original **string name** is now **public**. The **string _name;** is known as a [**Backing field**](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties#properties-with-backing-fields), you can read more about them from the link. We do not have to worry about them now.


Rather than having a method like we did with our **age**:

```cs
public string ReturnAge() {
  return age;
}
```

We have a very short solution

```cs
public string name { get; }
```

NOTICE! We have to change our string **name** into **public** (from private), so it can be accessed from the **Main program**, or any other class. There are ways of protecting the property, but we'll get to that later.

Let's use this way of getting age:

```cs
static void Main(string[] args)
{
  Person pekka = new Person("Pekka");
  Person antti = new Person("Antti");

  int i = 0;
  while (i < 27)
  {
    pekka.GrowOlder();
    i = i + 1;
  }

  antti.GrowOlder();

  if (antti.IsOfLegalAge())
  {
    Console.WriteLine(antti.name + " is of legal age");
  }
  else
  {
    Console.WriteLine(antti.name + " is underage");
  }

  if (pekka.IsOfLegalAge())
  {
    Console.WriteLine(pekka.name + " is of legal age");
  }
  else
  {
    Console.WriteLine(pekka.name + " is underage ");
  }
}
```

```console
Antti is underage
Pekka is of legal age
```

You can see, that now we can call our **Person's** name with simply adding **.name** after the object, such as **antti.name**. Let's update our **age** to have a **get method** as well, and remove the old ReturnAge-method. Now our class looks like this:


```cs
public class Person
{
  public string name { get; }
  public int age { get; set; }

  public Person(string initialName)
  {
    this.age = 0;
    this.name = initialName;
  }

  public void PrintPerson()
  {
    Console.WriteLine(this.name + ", age " + this.age + " years");
  }

  public void GrowOlder()
  {
    if (this.age < 100)
    {
      this.age = this.age + 1;
    }
  }

  public bool IsOfLegalAge() 
  {
    return this.age >= 18;
  }
}
```

You can see that **age** has also a method for **set**. This is because we are changing the age of **Person** in our method **GrowOlder**. We will get into **set method** later.

## A string representation of an object and the ToString-method

We are guilty of programming in a somewhat poor style by creating a method for printing the object, i.e., the **PrintPerson** method. A preferred way is to define a method for the object that returns a "string representation" of the object. The method returning the string representation is always **ToString** in C#. Let's define this method for the person in the following example:

```cs
public class Person
{
  // ..
  public override string ToString() 
  {
      return this.name + ", age " + this.age + " years";
  }
}
```

The **ToString** functions as **PrintPerson** does. However, it doesn't itself print anything but instead **returns** a string representation, which the calling method can execute for printing as needed.

The method is used in a somewhat surprising way:

```cs
static void Main(string[] args)
{
  Person pekka = new Person("Pekka");
  Person antti = new Person("Antti");

  int i = 0;
  while (i < 27)
  {
    pekka.GrowOlder();
    i = i + 1;
  }

  antti.GrowOlder();

  Console.WriteLine(pekka); // Same as Console.WriteLine(pekka.ToString() )
  Console.WriteLine(antti); // Same as Console.WriteLine(antti.ToString() )
}
```

In principle, the **Console.WriteLine** method requests the object's string representation and prints it. The call to the **ToString** method returning the string representation does not have to be written explicitly, as C# adds it automatically. When a programmer writes:

```cs
Console.WriteLine(antti);
```

C# extends the call at run time to the following form:

```cs
Console.WriteLine(antti.ToString());
```

As such, the call **Console.WriteLine(antti)** calls the **ToString** method of the **antti object** and prints the string returned by it.

We can remove the now obsolete printPerson method from the Person class.

## Method parameters

Let's continue with the **Person** class once more. We've decided that we want to calculate people's body mass indexes. To do this, we write methods for the person to set both the height and the weight, and also a method to calculate the body mass index. The new and changed parts of the Person object are as follows:

```cs
public class Person
{
  public string name { get; }
  public int age { get; set; }
  public int weight { get; set; }
  public int height { get; set; }

  public Person(string initialName)
  {
    this.age = 0;
    this.weight = 0;
    this.height = 0;
    this.name = initialName;
  }

  public double BodyMassIndex()
  {
    double heigthPerHundred = this.height / 100.0;
    return this.weight / (heigthPerHundred * heigthPerHundred);
  }

  // ...
}
```
The instance variables **height** and **weight** were added to the person. We can now see the **{ get; set; };** on both of these new variables. We will use them next to be able to tell our program, how tall or heavy a person is.

```cs
static void Main(string[] args)
{
  Person matti = new Person("Matti");
  Person juhana = new Person("Juhana");

  matti.height = 180;
  matti.weight = 86;

  juhana.height = 175;
  juhana.weight = 64;

  Console.WriteLine(matti.name + ", body mass index is " + matti.BodyMassIndex());
  Console.WriteLine(juhana.name + ", body mass index is " + juhana.BodyMassIndex());

}
```

This prints us 

```console
Matti, body mass index is 26.54320987654321
Juhana, body mass index is 20.897959183673468
```

## A parameter and instance variable having the same name!

In our constructor, we use the variable **initialName** rather than just **name**.

```cs
public Person(string initialName)
{
  this.age = 0;
  this.weight = 0;
  this.height = 0;
  this.name = initialName;
}
```

The parameter's name could also be the same as the instance variable's, so the following would also work:

```cs
public Person(string name)
{
  this.age = 0;
  this.weight = 0;
  this.height = 0;
  this.name = name;
}
```

In this case, **name** in the method refers specifically to a parameter named **name** and this.name to an instance variable of the same name. For example, the following example would not work as the code does not refer to the instance variable **name** at all. What the code does in effect is set the **name** variable received as a parameter to the value it already contains:

```cs
public Person(string name)
{
  this.age = 0;
  this.weight = 0;
  this.height = 0;
  // DO NOT DO THIS!
  name = name;
}
```

```cs
public Person(string name)
{
  this.age = 0;
  this.weight = 0;
  this.height = 0;
  // DO THIS INSTEAD!
  this.name = name;
}
```

## Calling an internal method

The object may also call its methods. For example, if we wanted the string representation returned by ToString to also tell of a person's body mass index, the object's own BodyMassIndex method should be called in the ToString method:

```cs
public override string ToString()
{
      return this.name + ", age " + this.age + " years, my body mass index is " + this.BodyMassIndex();
}
```

So, when an object calls an internal method, the **name of the method** and **this** prefix suffice. An alternative way is to call the object's own method in the form BodyMassIndex(), whereby no emphasis is placed on the fact that the object's own bodyMassIndex method is being called:

```cs
public override string ToString()
{
      return this.name + ", age " + this.age + " years, my body mass index is " + BodyMassIndex();
}
```

**You can now do the exercises for object oriented programming (oop)**
