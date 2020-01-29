---
title: "Strings"
parent: "Part 3 - Lists and Arrays"
permalink: /part3/4/
nav_order: 4
published: true
---

## Strings

Let's first revise what we already know about strings and see how to split them. Below we create a string variable magicWord, that contains value "abracadabra".

```cs
string magicWord = "abracadabra";
```

Passing a string as a parameter to a print command (or, for that matter, any method that takes a string parameter) happens in the familiar way:

```cs
string magicWord = "abracadabra";
Console.WriteLine(magicWord);
```

```console
abracadabra
```

## Reading and Printing Strings

You can read a string using the ReadLine-method offered by Console. The program below reads the name of the user and prints it:

```cs
Console.WriteLine("What's your name?");
// reading a line from the user and assigning it to the name variable
string name = Console.ReadLine();

Console.WriteLine(name);
```

```console
What's your name?
> Hank
Hank
```

Strings can also be concatenated. If you place a +-operator between two strings, you get a new string that's a combination of those two strings. Be mindful of any white spaces in your variables!

```cs
string greeting = "Hi ";
string name = "Lily";
string goodbye = " and see you later!";

string phrase = greeting + name + goodbye;

Console.WriteLine(phrase);
```

```console
Hi Lily and see you later!
```

## String comparisons

Strings can be compared with **==** just like any other variable.

```cs
string text = "Hello";
string word = "Hullo";

if (text == word)
{
  Console.WriteLine("Hooray!");
}
else
{
  Console.WriteLine("Boo");
}
```

```console
Boo
```

As we've come to know, a boolean value can be inverted through negation - **!**.

```cs
string text = "Hello";
string word = "Hullo";

if (!(text == word))
{
  Console.WriteLine("Boo!");
}
else
{
  Console.WriteLine("Hooray!");
}
```

Or by negating the comparison

```cs
string text = "Hello";
string word = "Hullo";

if (text != word)
{
  Console.WriteLine("Boo!");
}
else
{
  Console.WriteLine("Hooray!");
}
```

## Splitting a String

You can split a string to multiple pieces with the **Split-method** of the string class. The method takes as a parameter a string denoting the place around which the string should be split. The split method returns an array of the resulting sub-parts. In the example below, the string has been split around a space.

```cs
string text = "first second third fourth";
string[] pieces = text.Split(" ");
Console.WriteLine(pieces[0]);
Console.WriteLine(pieces[1]);
Console.WriteLine(pieces[2]);
Console.WriteLine(pieces[3]);

// For empty line print
Console.WriteLine();

for (int i = 0; i < pieces.Length; i++)
{
  Console.WriteLine(pieces[i]);
}
```

```console
first
second
third
fourth

first
second
third
fourth
```

## Data of Fixed Format

Splitting strings is used particularly when the data is of a fixed format. This refers to data that adheres to some predefined format. An example of this of this is the comma-separated values (csv) format, where commas are used to separate values. Below you'll find an example of data in csv form containing names and ages. The first column contains names and the second one ages. The columns are separed by a comma.

```console
sebastian,2 
lucas,2 
lily,1
```

Let's assume the user enters the data above row by row, ending with an empty line.

A program to print the names and ages looks like the following:

```cs
while (true)
{
  string input = Console.ReadLine();
  if (input == "")
  {
    break;
  }
  string[] pieces = input.Split(",");
  Console.WriteLine("Name: " + pieces[0] + ", age: " + pieces[1]);
}
```

```console
> sebastian,2 
Name: sebastian, age: 2 
> lucas,2 
Name: lucas, age: 2 
> lily,1 
Name: lily, age: 1
```

## Using Diverse Text

We've printed strings in the examples above. Some of the data contained in a fixed-format string can be numerical. In the previous data we used that contained names and ages, the ages were integers.

```console
sebastian,2 
lucas,2 
lily,1
```

Splitting a string always produces an array of strings. If the text is of fixed format, we can assume the data in a specific index to always be of the a specific type -- e.g., in the example above, age at index 1 is an integer.

The program below computes the sum of ages in this fixed format data. In order to compute the sum, the age must first be converted to a number (the familiar command Convert.ToInt32).

```cs
int sum = 0;

while (true)
{
  string input = Console.ReadLine();
  if (input == "")
  {
    break;
  }
  string[] parts = input.Split(",");
  sum = sum + Convert.ToInt32(parts[1]);
}
Console.WriteLine("Sum of the ages is " + sum);
```

```console
> sebastian,2 
> lucas,2 
> lily,1

Sum of the ages is 5
```

We can write a program to compute the average of the ages in the same way:

```cs
int sum = 0;
int count = 0;

while (true)
{
  string input = Console.ReadLine();
  if (input == "")
  {
    break;
  }
  string[] parts = input.Split(",");
  sum = sum + Convert.ToInt32(parts[1]);
  count++;
}
if (count > 0)
{
  Console.WriteLine("Age average: " + ((double)sum / count));
}
else
{
  Console.WriteLine("No input");
}
```

```console
> sebastian,2
> lucas,2
> lily,1

Age average: 1.6666666666666667
```

**You can now do the exercises for strings**