---
title: "Files and reading data"
parent: "Part 4 - Object Oriented Programming"
permalink: /part4/3/
nav_order: 3
published: true
---

A considerable amount of software is in one way or another based on handling data. Software created for playing music handles music files and those created for the purpose of image manipulation handle image files. Applications that run on the internet and mobile devices, such as Facebook, WhatsApp, and Telegram, handle user information that is stored in file-based databases. What these all have in common is that they read and manipulate data in one way or another. Also, the data being handled is ultimately stored in some format in one or more files.

## Reading From the Keyboard

We've been using the **Console.ReadLine** since the beginning of this course to read user input. The block in which data is read has been a while-true loop where the reading ends at a specific input.

```cs
while (true) {
    string line = Console.ReadLine();

    if (line == "end") {
        break;
    }

    // add the read line to a list for later
    // handling or handle the line immediately

}
```

In text-based user interfaces, the input of the user is directed into the input stream one line at a time, which means that the information is sent to be handled every time the user enters a new line.

The user input is read in string form. If we wanted to handle the input as integers, for instance, we'd have to convert it to another form. An example program has been provided below - it reads input from the user until the user inputs "end". As long as the user input is not "end" the inputs are handled as integers -- in this case, the number is simply printed.

```cs
while (true) {
    string row = Console.ReadLine();

    if (row == "end") {
        break;
    }

    int number = Convert.ToInt32(row);
    Console.WriteLine(row);
}
```

## Files and the Filesystem

**Files** are collections of data that live in computers. These files can contain, among other things, text, images, music, or any combination of these. The file format determines the content of the file as well as the program required to read the file. For example, PDF files are read with a program suited for reading PDF files, and music files are read with a program suited for reading music files. Each of these programs is made by humans, and the creators of these programs -- i.e., programmers -- also specify the file format as part of the work.

Computers have several different programs for browsing files. These programs are specific to the operating system. All programs used for browsing files make use of the filesystem of the computer in one way or another.

Our development environment provides us with the ability to browse the files of a project. In Visual Studio Code, the whole project and all files associated can be seen in the list on the left side of the screen.

Files exist on the hard drive of a computer, which is, in reality, a large set of ones and zeros, i.e., bits. Information is made up of these bits, e.g., one variable of type int takes up 32 bits (i.e., 32 ones or zeros). Modern terabyte-sized hard drives hold about 8 trillion bits (written out the number is 8,000,000,000,000). On this scale, a single integer is very small.

Files can exist practically anywhere on a hard drive, even separated into multiple pieces. The computer's **filesystem** has the responsibility of keeping track of the locations of files on the hard drive as well as providing the ability to create new files and modify them. The filesystem's main responsibility is abstracting the true structure of the hard drive; a user or a program using a file doesn't need to care about the about how, or where, the file is actually stored.

## Reading From a File

Reading a file is done by using **File class**, which can be found from **System.IO**. We will concentrate on text files, or files that include strings. 

In our examples (for now), we assume we have a files called **text.txt** and **records.csv** in the same folder as **Program.cs** is. You can once again try these in your sandbox. The text.txt contains this:

```console
This is a line
This is second line
This is 3rd
This includes a double, 3.25
This has "quotes"
```
And records.csv contains this:

```console
sebastian,22
matt,21
rebecca,23
```

There are several ways how to read a file. Here's (first) two of them:

```cs

using System.IO;

static void Main(string[] args)
{
  // Example #1
  // Read the file as one string.
  string text = File.ReadAllText("text.txt");

  // Display the file contents to the console. Variable text is a string.
  Console.WriteLine("This was done with ReadAllText.");
  Console.WriteLine(text);

  //Print empty line for easier reading
  Console.WriteLine();

  // Example #2
  // Read each line of the file into a string array. 
  //Each element of the array is one line of the file.
  Console.WriteLine("This was done with ReadAllLines.");
  string[] lines = File.ReadAllLines("text.txt");

  // Display the file contents by using a foreach loop.
  foreach (string line in lines)
  {
    Console.WriteLine(line);
  }
}
```

This program prints out

```console
This was done with ReadAllText.
This is a line
This is second line
This is 3rd
This includes a double, 3.25
This has "quotes"

This was done with ReadAllLines.
This is a line
This is second line
This is 3rd
This includes a double, 3.25
This has "quotes"
```

Let's look at both of them a bit deeper.

### File.ReadAllText()

The first example is quite self-explanatory. We declare a variable **string text** and use the method **File.ReadAllText()** to read the textfile and save it to the variable. This saves the text from the file to the variable **as it is** in the file, including all the newlines. As you can see, when we print out the variable, it will print each line from the file to a separate line, as it should.

### File.ReadAllLines()

The second example is quite similar to the first one. Rather than saving the information from the file to a single string, we now save it to an array with **File.ReadAllLines()**. Now each element in the array is a line from the text file.

So what's the difference, why do we need two ways? When we want to have easy access to each individual line of the text, we would probably use the latter one. If all the text is saved into a single variable, then finding particular part from there would be more difficult. On the other hand, if we need to have the information in one piece, we would use the first one.

There are also other ways of reading files, such as streams. We will get those later.

## Reading Data of a Specific Format From a File

The world is full of data that are related to other data -- these form collection. For example, personal information includes name, date of birth, phone number. Address information, on the other hand, includes country, city, street address, postal number, and so on.

Data is often stored in files using a specific format. One such format that's already familiar to us is comma-separated values (CSV) format, i.e., data separated by commas.

```cs
while (true)
{
  Console.WriteLine("Enter name and age separated by a comma:");
  string input = Console.ReadLine();
  if (input == "")
  {
    break;
  }
  string[] pieces = input.Split(",");
  Console.WriteLine("Name: " + pieces[0] + ", age: " + pieces[1]);
}
```

The program works as follows:

```console
Enter name and age separated by a comma:
sebastian,22
Name: sebastian, age: 22
Enter name and age separated by a comma:
matt,21
Name: matt, age: 21
Enter name and age separated by a comma:
```

Reading the same data from a file called **records.csv** would look like so:

```cs
string[] lines = File.ReadAllLines("records.csv");
foreach (string line in lines)
{
  string[] pieces = line.Split(",");
  Console.WriteLine("Name: " + pieces[0] + ", age: " + pieces[1]);
}
```

Which prints out

```console
Name: sebastian, age: 22
Name: matt, age: 21
Name: rebecca, age: 23
```

As you can see, we now used the **ReadAllLines** method, as we needed to retrieve from each line separately. 

We could have used **ReadAllText**, but we would have had to first **Split the string into an array** to be able to access all the lines... And as you can see, this way the array already exists, saving us from an extra step.

## Reading Objects From a File

Creating objects from data that is read from a file is straightforward. Let's assume that we have a class called Person, as well as the data from before.

Reading objects can be done like so:

```cs
static void Main(string[] args)
{
  List<Person> people = new List<Person>();

  string[] lines = File.ReadAllLines("records.csv");
  foreach (string line in lines)
  {
    string[] pieces = line.Split(",");
    string name = pieces[0];
    int age = Convert.ToInt32(pieces[1]);

    people.Add(new Person(name, age));
  }
  Console.WriteLine("Total amount read: " + people.Count);
}
```

```console
Total amount read: 3
```

**You can now do the exercises for files**