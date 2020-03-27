---
title: "Grouping Data Using Dictionaries"
parent: "Part 8 - Dictionaries"
permalink: /part8/1/
nav_order: 3
published: true
---

# Grouping Data Using Dictionaries

A dictionary has at most one value per each key. In the following example, we store the phone numbers of people into the dictionary.

```cs
static void Main(string[] args)
{
  Dictionary<string, string> phoneNumbers = new Dictionary<string, string>();
  
  phoneNumbers["Pekka"] = "040-12348765";
  Console.WriteLine("Pekka's number " + phoneNumbers["Pekka"]);

  .A
  Console.WriteLine("Pekka's number " + phoneNumbers["Pekka"]);
}
```

```console
Pekka's number 040-12348765
Pekka's number 09-111333
```

NOTICE! The way we handled the dictionary is now a bit different. Rather than using the **Add** method, we put the values in by directly addressing the key, this time "Pekka". This way we could also update the value to which the key points to. This works when we assign a value to the key, even though the key does exist yet in the dictionary.

If we were to search for a value with a key that does not exist, however, we get an error:

```cs
static void Main(string[] args)
{
  Dictionary<string, string> phoneNumbers = new Dictionary<string, string>();

  Console.WriteLine("Pekka's number " + phoneNumbers["Pekka"]);

  phoneNumbers["Pekka"] = "09-111333";
  Console.WriteLine("Pekka's number " + phoneNumbers["Pekka"]);
}
```

```console
Unhandled exception. System.Collections.Generic.KeyNotFoundException: The given key 'Pekka' was not present in the dictionary.

[. . .]
```

Be careful, when handling data!

What if we wanted to assign multiple values ​​to a single key, such as multiple phone numbers for a given person?

Since keys and values ​​in a dictionary can be any variable, it is also possible to use lists as values in a dictionary. You can add more values ​​to a single key by attaching a list to the key. Let's change the way the numbers are stored in the following way:

```cs
Dictionary<string, List<string>> phoneNumbers = new Dictionary<string, List<string>>();

// Add Pekka to the Dictionary with a new List for numbers
phoneNumbers["Pekka"] = new List<string>();
// Get Pekka's list and add a number to the list
phoneNumbers["Pekka"].Add("040-12348765");
// Get Pekka's list and add a number to the list
phoneNumbers["Pekka"].Add("09-111333");

Console.WriteLine("Pekka's numbers:");
// Get Pekka's list and use the list's ForEach to print content
phoneNumbers["Pekka"].ForEach(Console.WriteLine);
```

This exactly the same as

```cs
Dictionary<string, List<string>> phoneNumbers = new Dictionary<string, List<string>>();

// Add Pekka to the Dictionary with a new List for numbers
phoneNumbers.Add("Pekka", new List<string>());
// Get Pekka's list and add a number to the list
phoneNumbers["Pekka"].Add("040-12348765");
// Get Pekka's list and add a number to the list
phoneNumbers["Pekka"].Add("09-111333");

Console.WriteLine("Pekka's numbers:");
// Get Pekka's list and use the foreach loop to print content
foreach (string phone in phoneNumbers["Pekka"]) {
  Console.WriteLine(phone);
}

```

```console
Pekka's numbers:
040-12348765
09-111333
```

We define the type of the phone number as Dictionary\<string, List\<string\>\>. This refers to a dictionary that uses a string as a key and a list containing strings as its value. As such, the values added to the dictionary are concrete lists.

```cs
// Add Pekka to the Dictionary with a new List for numbers
phoneNumbers.Add("Pekka", new List<string>());
```

We can implement, for instance, an exercise point tracking program in a similar way. The example below outlines the **TaskTracker** class, which involves user-specific tracking of points from tasks. The user is represented as a string and the points as integers.