---
title: "Processing files"
parent: "Part 11 - Random, files and exceptions"
permalink: /part11/3/
nav_order: 3
published: true
---

# Processing files

We have already learned some strategies to read text files. If your memories of the subject are hazy, take a look at the relevant parts of the **fourth part of the course material**. In that material, we used **ReadAllLines** and **ReadAllText** methods. They have writing versions as well, [**you can read more about those in here**](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/file-system/how-to-write-to-a-text-file). In this section how ever, we concentrate on **StreamReader and StreamWriter**.


## StreamReader and StreamWriter

Next, let's take a look at writing data to files. The [**StreamWriter **](https://docs.microsoft.com/en-us/dotnet/api/system.io.streamwriter?view=netframework-4.8) class offers the functionality to write to files. The constructor of the StreamWriter class receives as its parameter a string that represents the location of the target file.

```cs
namespace sandbox
{
  using System;
  using System.IO;

  class Program
  {
    public static void Main(string[] args)
    {
      StreamWriter writer = new StreamWriter("file.txt");
      writer.WriteLine("Hello file!"); //writes the string "Hello file!" and line change to the file
      writer.WriteLine("More text");
      writer.Write("And a little extra"); // writes the string "And a little extra" to the file without a line change
      writer.Close(); // closes the file
    }
  }
}
```

In the example above we write to the file "file.txt" the string "Hello file!", followed by a line change and some additional text. Take notice that when writing to the file the method **Write** does not add line changes, and you have to add them yourself. In contrast, the method **WriteLine** adds a new line change at the end of the parameter string it receives.

The constructor of the **StreamWriter** class might throw an exception that must be either handled or thrown so that it is the responsibility of the calling method. Here is what a method that receives as its parameters a file name and the text contents to write into it could look like.

```cs
namespace sandbox
{
  using System;
  using System.IO;
  public class Storer
  {

    public void WriteToFile(string fileName, string text)
    {
      try
      {
        StreamWriter writer = new StreamWriter(fileName);
        writer.WriteLine(text);
        writer.Close();
      }
      catch (Exception e)
      {
        Console.WriteLine(e.Message);
      }
    }
  }
}
```

In the **WriteToFile** method above we begin by creating a **StreamWriter** object. It writes data the the file that is located at the path that the string **fileName** indicates. After this we write the text to the file by calling the **WriteLine** method. The possible exception that the constructor throws has to be handled with a try-catch block or the handling responsibility has to be transferred elsewhere. In the WriteToFile method we have used the try-catch block.

Let's create a **Main** method that calls the WriteToFile of a Storer object.

```cs
Storer storer = new Storer();
storer.WriteToFile("diary.txt", "Dear diary, today was a good day.");
```

By calling the method above we create a file called "diary.txt" and write the text "Dear diary, today was a good day." into it. If the file already exists, the earlier contents are erased when we store the new text.