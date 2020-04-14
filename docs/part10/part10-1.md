---
title: "IComparable Interface"
parent: "Part 10 - Sorting and other tools"
permalink: /part10/1/
nav_order: 1
published: true
---

# IComparable

In the previous section, we looked at interfaces in more general terms - let's now familiarize oruselves with one of C#'s ready interfaces. The [**IComparable interface**](https://docs.microsoft.com/en-us/dotnet/api/system.icomparable-1?view=netframework-4.8) defines the [**CompareTo**](https://docs.microsoft.com/en-us/dotnet/api/system.icomparable-1.compareto?view=netframework-4.8#System_IComparable_1_CompareTo__0_) method used to compare objects. If a class implements the IComparable interface, objects created from that class can be **Sort** using C#'s sorting algorithms.

The **CompareTo** method required by the IComparable interface gets as its parameter the object to which the "this" object is compared. If the "this" object comes before the object received as a parameter in terms of sorting order, the method should return a negative number. If, on the other hand, id "this" object comes after the object received as a parameter, the method should return a positive number. Otherwise, 0 is returned. The sorting resulting from the CompareTo method is called natural ordering.

Let's take a look at this with the help of a **Member** class that represents a child or youth who belongs to a club. Each club member has a name and height. The club members should go to eat in order of height, so the Member class should implement the IComparable interface. The IComparable interface takes as its type parameter the class that is the subject of the comparison. We'll use the same Member class as the type parameter.


```cs
namespace sandbox
{
  // IComparable is in System
  using System;
  // Implement IComparable<Member>
  // Explicit comparison to Member, not other objects
  public class Member : IComparable<Member>
  {
    public string name { get; }
    public int height { get; }

    // Basic constructor
    public Member(string name, int height)
    {
      this.name = name;
      this.height = height;
    }

    // CompareTo Member
    // For this we implement IComparable<Member>
    // With just IComparable, we would compare objects
    // With CompareTo(object obj)
    public int CompareTo(Member member)
    {
      // If compared member is null, return 1
      // "this" comes after null
      if (member == null)
      {
        return 1;
      }
      // If height is equal, return 0
      // They are now equal in comparison
      if (this.height == member.height)
      {
        return 0;
      }
      // If this height is more
      // Return 1
      // "this" comes after compared member
      else if (this.height > member.height)
      {
        return 1;
      }
      // As all other options have been done
      // Return -1
      // "this" comes before compared member
      else
      {
        return -1;
      }
    }

    // Basic ToString
    public override string ToString()
    {
      return this.name + " (" + this.height + ")";
    }
  }
}
```

The CompareTo method required by the interface returns an integer that informs us of the order of comparison.

Since returning a negative number from the **CompareTo()** is enough if the this object is smaller than the parameter object, and zero when the lengths are the same, the CompareTo method described above can also be implemented as follows.

```cs
public int CompareTo(Member member)
{
  return this.height - member.height;
}
```

Since the Member class now implements the IComparable interface, it is possible to sort a list of members by using the **Sort** method. In fact, objects of any class that implements the IComparable interface can be sorted using the **Sort** method. For example, strings and integers implement IComparable.

Sorting club members is straightforward now.

```cs
// List of Members
List<Member> member = new List<Member>();
// Add three regular members
member.Add(new Member("mikael", 182));
member.Add(new Member("matti", 187));
member.Add(new Member("ada", 184));
// Add null to show the sorting of null
member.Add(null);

// Print each member
member.ForEach(Console.WriteLine);

Console.WriteLine("Let's sort the members:");

// Sort the list
member.Sort();

// Print each member
member.ForEach(Console.WriteLine);
```

```console
mikael (182)
matti (187)
ada (184)

Let's sort the members:

mikael (182)
ada (184)
matti (187)
```