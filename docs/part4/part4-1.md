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

We've already used some of the classes and objects provided by C#. A class defines the attributes of objects, i.e., the information related to them (properties), and their commands, i.e., their methods. The values of instance (i.e., object) variables define the internal state of an individual object, whereas methods define the functionality it offers.

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

![House blueprints]("/assets/images/houses.jpg")