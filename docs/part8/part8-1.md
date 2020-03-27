---
title: "Dictionaries"
parent: "Part 8 - Dictionaries"
permalink: /part8/1/
nav_order: 1
published: true
---

# Dictionaries

One of the most commonly used data structures among lists is  a **dictionary**. In C#, the [**Dictionary<TKey,TValue> Class**](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2?view=netframework-4.8) is located in the **System.Collections.Generic** Namespace. But what does it do?

Data in dictionaries is stored as **key-value pairs**, where values can be added, retrieved, and deleted using keys. 

In the example below, a Dictionary object has been created to search for cities by their postal codes, after which four postal code-city pairs have been added to the Dictionary object. At the end of it, the postal code "00710" is retrieved from the dictionary. Both the postal code and the city are represented as strings.

```cs
using System;
using System.Collections.Generic;

namespace sandbox
{
  class Program
  {
    static void Main(string[] args)
    {
      Dictionary<string, string> postalCodes = new Dictionary<string, string>();
      postalCodes.Add("00710", "Helsinki");
      postalCodes.Add("90014", "Oulu");
      postalCodes.Add("33720", "Tampere");
      postalCodes.Add("33014", "Tampere");

      Console.WriteLine(postalCodes["33720"]);
    }
  }
}
```

```console
Tampere
```

The internal state of the dictionary created above looks like this. Each key refers to some value.

![Dictionary](https://github.com/centria/basic-coding/raw/master/assets/images/part8-1-dict.png)

If the dictionary does not contain the key used for search, we get a **KeyNotFoundException**.

```cs
Dictionary<string, string> postalCodes = new Dictionary<string, string>();
postalCodes.Add("00710", "Helsinki");
postalCodes.Add("90014", "Oulu");
postalCodes.Add("33720", "Tampere");
postalCodes.Add("33014", "Tampere");

Console.WriteLine(postalCodes["67100"]);
```

```console
Unhandled exception. System.Collections.Generic.KeyNotFoundException: The given key '67100' was not present in the dictionary.
   at System.Collections.Generic.Dictionary`2.get_Item(TKey key)
   at sandbox.Program.Main(String[] args) in /mnt/c/Users/HeikkiHei/Documents/coding-exercises/sandbox/Program.cs:line 17
```

Two type parameters are required when creating a dictionary - the type of the key and the type of the value added. If the keys of the dictionary are of type string, and the values of type integer, the dictionary is created with the following statement 

```cs
Dictionary<string, integer> dict = new Dictionary<string, integer>();
```

Adding to the dictionary is done through the **Add(*key*, *value*)** method that has two parameters, one for the key, the other for the value. Retrieving from a dictionary is done with the familiar **dictionary[*key*]** syntax. How ever, this time we are looking for a value with a key, and not with an index.

## Dictionary Keys Correspond to a Single Value at Most

The dictionary has a maximum of one value per key. If a new key-value pair is added to the dictionary, but the key has already been associated with some other value stored in the dictionary, we will get an ArgumentException:

```cs
Dictionary<string, string> postalCodes = new Dictionary<string, string>();
postalCodes.Add("67100", "Kokkola");
postalCodes.Add("67100", "Karleby");
```

```console
Unhandled exception. System.ArgumentException: An item with the same key has already been added. Key: 67100
   at System.Collections.Generic.Dictionary`2.TryInsert(TKey key, TValue value, InsertionBehavior behavior)
   at System.Collections.Generic.Dictionary`2.Add(TKey key, TValue value)
```

For this, we can prepare ourselves, by checking if a value already exists in the dictionary, and only if it does not, we add the new value:

```cs
Dictionary<string, string> postalCodes = new Dictionary<string, string>();
postalCodes.Add("00710", "Helsinki");
postalCodes.Add("90014", "Oulu");
postalCodes.Add("33720", "Tampere");
postalCodes.Add("33014", "Tampere");
postalCodes.Add("67100", "Kokkola");
postalCodes.Add("99999", null);

if (!postalCodes.ContainsKey("67100"))
{
  postalCodes.Add("67100", "Karleby");
}
```

This way our program does not crash, when we try to change the value for "67100". To see what our dictionary contains, we can use a foreach-loop for **KeyValuePair** objects:

```cs
foreach (KeyValuePair<string, string> kvp in postalCodes)
{
  Console.WriteLine("Key = {0}, Value = {1}",
      kvp.Key, kvp.Value);
}
```

And it prints like this:

```console
Key = 00710, Value = Helsinki
Key = 90014, Value = Oulu
Key = 33720, Value = Tampere
Key = 33014, Value = Tampere
Key = 67100, Value = Kokkola
Key = 99999, Value = 
```

As you can see, we can also give a **null** as a value. We cannot, however, give null as a key, or we will get **ArgumentNullException**.

## A Reference Type Variable as a Dictionary Value

Let's take a look at how a spreadsheet works using a library example. You can search for books by book title. If a book is found with the given search term, the library returns a reference to the book. Let's begin by creating an example class Book that has its name, content and the year of publication as instance variables.

```cs
public class Book
{
  public string name { get; set; }
  public string content { get; set; }
  public int published { get; set; }

  public Book(string name, int published, string content)
  {
    this.name = name;
    this.published = published;
    this.content = content;
  }

  public override string ToString()
  {
    return "Name: " + this.name + " (" + this.published + ")\n"
        + "Content: " + this.content;
  }
}
```

Let's create a dictionary that uses the book's name as a key, i.e., a string-type object, and the book we've just created as the value.

```cs
Dictionary<string, Book> directory = new Dictionary<string, Book>();
```

The dictionary above uses **string** as a key. Let's expand the example so that two books are added to the dictionary, "Sense and Sensibility" and "Pride and Predujice".

```cs
Book senseAndSensibility = new Book("Sense and Sensibility", 1811, "...");
Book prideAndPredujice = new Book("Pride and Prejudice", 1813, "....");

Dictionary<string, Book> directory = new Dictionary<string, Book>();
directory.Add(senseAndSensibility.name, senseAndSensibility);
directory.Add(prideAndPredujice.name, prideAndPredujice);
```

Books can be retrieved from the directory by book name. A search for "Persuasion" will not produce any results, in which case the dictionary gives an error. The book "Pride and Prejudice" is found, however. Let's play it safe, and put both inside an if:

```cs
if (directory.ContainsKey("Persuation"))
{
  Console.WriteLine(directory["Persuasion"]);
}
else
{
  Console.WriteLine("Book not found!");
}

Console.WriteLine();
if (directory.ContainsKey("Pride and Prejudice"))
{
  Console.WriteLine(directory["Pride and Prejudice"]);
}
```

```console
Book not found!

Name: Pride and Prejudice (1813)
Content: ....
```

## When Should Dictionaries Be Used?

The dictionary is implemented in such a way that searching by a key is very fast. The dictionary  generates a "hash value" from the key, i.e., a piece of code, which is used to store the value a specific location. When a key is used to retrieve information from a dictionary, this particular code identifies the location where the value associated with the key is. In practice, it's not necessary to go through all the key-value pairs in the dictionary when searching for a key; the set that's checked is significantly smaller. 

Consider the library example that was introduced above. The whole program could just as well have been implemented using a list. In that case, the books would be placed on the list instead of the directory, and the book search would happen by iterating over the list.

In the example below, the books have been stored in a list and searching for them is done by going through the list.

```cs
List<Book> books = new List<Book>();
Book senseAndSensibility = new Book("Sense and Sensibility", 1811, "...");
Book prideAndPrejudice = new Book("Pride and Prejudice", 1813, "....");
books.Add(senseAndSensibility);
books.Add(prideAndPrejudice);

// searching for a book named Persuasion
foreach (Book book in books)
{
  if (book.name == "Persuation")
  {
    Console.WriteLine(book);
    break;
  }
}

Console.WriteLine();
// searching for a book named Sense and Sensibility
foreach (Book book in books)
{
  if (book.name == "Sense and Sensibility")
  {
    Console.WriteLine(book);
    break;
  }
}
```

```console

Name: Sense and Sensibility (1811)
Content: ...
```

Now the program works quite the same as our Dictionary version, right?

Functionally, yes. Let's however, consider the performance of the program. C#'s DateTime() has property **Ticks**, which represents the given date and time of a DateTime instance. A Tick is one hundred nanoseconds.

```cs
List<Book> books = new List<Book>();

// Add 10 million books to the list

Book senseAndSensibility = new Book("Sense and Sensibility", 1811, "...");
Book prideAndPrejudice = new Book("Pride and Prejudice", 1813, "....");
books.Add(senseAndSensibility);
books.Add(prideAndPrejudice);

DateTime start = DateTime.Now;

// searching for a book named Persuasion
foreach (Book book in books)
{
  if (book.name == "Persuation")
  {
    Console.WriteLine(book);
    break;
  }
}

Console.WriteLine();

// searching for a book named Sense and Sensibility
foreach (Book book in books)
{
  if (book.name == "Sense and Sensibility")
  {
    Console.WriteLine(book);
    break;
  }
}
DateTime end = DateTime.Now;
Console.WriteLine("Time elapsed: " + (end.Ticks - start.Ticks)/10000.0 + " milliseconds");
``` 

```console
Name: Sense and Sensibility (1811)
Content: ...
Time elapsed: 27.753 milliseconds
```

With 10 million books, it takes almost a second to find two books. Of course, the way in which the list is ordered has an effect. If the book being searched was first on the list, the program would be faster. On the other hand, if the book were not on the list, the program would have to go through all of the books in the list before determining that such book does not exist.

Let's consider the same program using a dictionary.

```cs

Dictionary<string, Book> directory = new Dictionary<string, Book>();

// Add 10 million books to the dictionary

Book senseAndSensibility = new Book("Sense and Sensibility", 1811, "...");
Book prideAndPredujice = new Book("Pride and Prejudice", 1813, "....");
directory.Add(senseAndSensibility.name, senseAndSensibility);
directory.Add(prideAndPredujice.name, prideAndPredujice);

DateTime start = DateTime.Now;

if (directory.ContainsKey("Persuation"))
{
  Console.WriteLine(directory["Persuasion"]);
}
else
{
  Console.WriteLine("Book not found!");
}

Console.WriteLine();
if (directory.ContainsKey("Pride and Prejudice"))
{
  Console.WriteLine(directory["Pride and Prejudice"]);
}

DateTime end = DateTime.Now;
Console.WriteLine("Time elapsed: " + (end.Ticks - start.Ticks)/10000.0 + " milliseconds");
```