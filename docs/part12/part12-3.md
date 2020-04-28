---
title: "Graphical interfaces"
parent: "Part 12 - Using, Namespaces and Graphical interfaces"
permalink: /part12/3/
nav_order: 2
published: true
---

# Graphical interfaces

So far, all our programs have used the console, or terminal, as their interface. But in modern operating systems, graphical interfaces are more common. C# has a variety of choices built in for creating graphical programs for Windows environment, and on this course, we'll take a quick glance of one of the options.

## Creating a new Windows Forms project

When we created our console projects, we used the command **dotnet new ...**. We can create a graphical project in the same manner. This time, the command is **dotnet new winforms**. 

**NOTICE!** If you are unable to create a project with the command above, you might have to change your Terminal in VSC to be **PowerShell**. Windows Forms programs can only be created and run through a Windows based terminal.

The program can be run with same commands as a console program, i.e. **dotnet run**. One major difference is in our **csproj** file, where we decide we are creating a Windows application.

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

As you can see, the OutputType is now **WinExe**, meaning a Windows Executable file, and will have a file type **.exe**. With this, we will also find an executable file from our folders.

Windows Forms is one type of graphical interface that can be created with C#. We will be using it in our examples in this course.

Let's create our first project.

NOTICE! This, and all the examples in this part, only work on Windows!

* Create a folder where you want your project. The example will be in a folder called **GuiProject**.

* To keep the folder structure neat, create a folder **src** in the project folder, and navigate there.

* Run the command **dotnet new winforms** inside the src folder.

You will get a project structure something like this:

```console
.
└── src
    ├── Form1.Designer.cs
    ├── Form1.cs
    ├── Program.cs
    ├── obj
    └── src.csproj
```

You can now test out your project, with **dotnet run**. You should get an program that looks like this:

![Winform1](https://github.com/centria/basic-coding/raw/master/assets/images/part12/winform1.png)

Hooray, the program opens! It does not do anything quite yet. Let's look into our files, and then start adding some functionality.