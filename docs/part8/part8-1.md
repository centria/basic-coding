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