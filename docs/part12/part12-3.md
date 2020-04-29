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

```cs
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace src
{
  static class Program
  {
    /// <summary>
    ///  The main entry point for the application.
    /// </summary>
    [STAThread]
    static void Main()
    {
      Application.SetHighDpiMode(HighDpiMode.SystemAware);
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form1());
    }
  }
}
```

Our **Main** now has quite much more than we have created with text interfaces. The concept is still quite the same: The main functionality of Main is to trigger the program into running. The last line is the most interesting, with **Application.Run(new Form1());**. Let's look at that Form1 now.

There are some parts of the code we have not handled yet, and won't handle in this course, such as the comments with \<summary\>. Those are parts for Windows Fields Designer and its comments, and we shall not worry about them.

We do have to care about [**[STAThread]**](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-3.0/ms182351(v=vs.80)?redirectedfrom=MSDN). *"This attribute must be present on the entry point of any application that uses Windows Forms; if it is omitted, the Windows components might not work correctly. If the attribute is not present, the application uses the multithreaded apartment model, which is not supported for Windows Forms."*

```cs
// Form1.cs
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace src
{
  public partial class Form1 : Form
  {
    public Form1()
    {
      InitializeComponent();
    }
  }
}
```

Nothing much happens in this file, except we call the method **InitializeComponent();**. You might notice, that the call is done as the class would call its own method, and that is quite true. This class is called a **partial class**, and it inherits **Form**. This means, that it implements some of the parts of Form, but not all. It is calling for a method from another partial class. This time, it is partial of **Form1** itself. Let's have a look.

```cs
// Form1.Designer.cs
namespace src
{
  partial class Form1
  {
    /// <summary>
    ///  Required designer variable.
    /// </summary>
    private System.ComponentModel.IContainer components = null;

    /// <summary>
    ///  Clean up any resources being used.
    /// </summary>
    /// <param name="disposing">true if managed resources should be disposed; otherwise, false.</param>
    protected override void Dispose(bool disposing)
    {
      if (disposing && (components != null))
      {
        components.Dispose();
      }
      base.Dispose(disposing);
    }

    #region Windows Form Designer generated code

    /// <summary>
    ///  Required method for Designer support - do not modify
    ///  the contents of this method with the code editor.
    /// </summary>
    private void InitializeComponent()
    {
      this.components = new System.ComponentModel.Container();
      this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
      this.ClientSize = new System.Drawing.Size(800, 450);
      this.Text = "Form1";
    }

    #endregion
  }
}
```

Once again, we see quite much of the comments created by the designer, but also a different comment, starting with a **#**. Those are for collapsing code out of view if certain options are enabled, but for us, yet another part not to worry about. Let's clean up the file:

```cs
namespace src
{
  partial class Form1
  {
    private System.ComponentModel.IContainer components = null;

    protected override void Dispose(bool disposing)
    {
      if (disposing && (components != null))
      {
        components.Dispose();
      }
      base.Dispose(disposing);
    }

    private void InitializeComponent()
    {
      this.components = new System.ComponentModel.Container();
      this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
      this.ClientSize = new System.Drawing.Size(800, 450);
      this.Text = "Form1";
    }
  }
}
```

Much more readable. Now we can see we have two mehtods, **Dispose** and **InitializeComponent**, and we recognize the latter was called by the other partial. Let's look at that first.

The method contains several lines, which each have a specific function for creating our program window:
```cs
this.components = new System.ComponentModel.Container();
```

* Is used for storing elements which do not have a visual representation during the runtime, but might be needed otherwise, such as a timer running in the background.

```cs
this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
```

* Is used to define, which kind of method is used for scaling. By default, the scaling is Font, but could be also Dpi, Inherit or None.

```cs
this.ClientSize = new System.Drawing.Size(800, 450);
```

* Is quite self-explanatory, defining the size of the window we draw.

```cs
this.Text = "Form1";
```

* Defines the text in the up-left corner of our window.

Our other method, **protected override void Dispose(bool disposing)**, is automatically created, and takes care of disposing (or handing over to garbage collection) the elements of our program. It is used for example when we close the program window. For our intents and purposes, we don't have to touch it.

## First functionality

As always, we start with a classic "Hello World" in our code. Let's add some content to our window.

```cs
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace src
{
  public partial class Form1 : Form
  {
    // Added TextBox1
    private TextBox textBox1;
    public Form1()
    {
      InitializeComponent();
    }
  }
}

```

As our other form is a partial for this one, we want to create the priave TextBox here. We could, just as well, create it in the next file, and bring the correct namespace with it. Let's keep it here, though, for at least now.

```cs
namespace src
{
  partial class Form1
  {

    private System.ComponentModel.IContainer components = null;
    protected override void Dispose(bool disposing)
    {
      if (disposing && (components != null))
      {
        components.Dispose();
      }
      base.Dispose(disposing);
    }

    private void InitializeComponent()
    {
      this.components = new System.ComponentModel.Container();
      this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
      this.ClientSize = new System.Drawing.Size(800, 450);
      // More meaningful text
      this.Text = "Hello World Application";

      // Call this.textBox1 and initialize
      this.textBox1 = new System.Windows.Forms.TextBox();
      // Give the textbox some content
      this.textBox1.Text = "Hello World";
      // Make it ReadOnly, so it cannot be edited by the users
      this.textBox1.ReadOnly = true;
      // Center to the screen
      this.textBox1.Location = new System.Drawing.Point((this.Width - textBox1.Width) / 2, (this.Height - textBox1.Height) / 2);
      // Add to controls
      this.Controls.Add(this.textBox1);
    }
  }
}
```

That's a lot of code for a simple string.

```cs
this.textBox1 = new System.Windows.Forms.TextBox();
```

* We initialize a standard textbox object by getting it from the correct namespace. As you might notice, we do not have any **using directives** in this part of the form, but we could just as well have them here.

```cs
this.textBox1.Text = "Hello World";
```

* Creates the text content inside the textbox.

```cs
this.textBox1.ReadOnly = true;
```

* Prevents the users from editing the textbox. You can take this line away and see what happens.

```cs
this.textBox1.Location = new System.Drawing.Point((this.Width - textBox1.Width) / 2, (this.Height - textBox1.Height) / 2);
```

* Not required, but nice to have. We center an item by giving it a new **Point** as **Location**. Location is the top-left corner of the item.

```cs
this.Controls.Add(this.textBox1);
```

* Earlier we mentioned components, which have the non-displayable components. In **Controls**, we store everything we want to show to the user.

![Winform2](https://github.com/centria/basic-coding/raw/master/assets/images/part12/winform2.png)