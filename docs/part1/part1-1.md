---
title: "Printing and reading"
parent: "Part 1 - The beginning"
permalink: /part1/1/
nav_order: 1
published: trues
---

## Printing and reading

The basic structure of a program is following:


```cs  
public class Program {  
    public static void Main(string[] args) {  
        // Add your statements here  
    }  
}   
```


The program execution starts from the first line after `public static void Main(string[] args) {` and ends at the closing `}` bracket. Everything in between is run one row at a time. For example, the most common first program of any programmer, the `Hello World`, would go like this:

```cs  
public class Program {  
    public static void Main(string[] args) {  
        Console.WriteLine("Hello World");  
    }  
}   
```

In this example, the only runnable statement is `Console.WriteLine("Hello World");`, which prints out 



```console
Hello World!
```


We will later focus on the terms `public class` and `public static void`, no need to worry about them yet.

In the material the whole structure might not be shown, unless purposefully needed. The example above could be represented also as


```cs  
Console.WriteLine("Hello World");  
```


in the future. In the exercises, for the first weeks the basic structure is given, so you do not have to worry about memorising it.

## Printing

As mentioned earlier, programming languages have statements built in them. `Console.WriteLine` is one of them. The statement is quite self-explanatory. It tells the computer to `write a line to the console`. You can change the `Hello World` to any text you wish, as long as the command itself is not changed, and it will work.

**With this information, you should be able to do the first exercise.**

The requirements in the exercises are very precise. If for example the line needs to end with an exclamation mark, it cannot be left out.

Programs are created (and read) command by command, where every command has to be on their own line. In the next example, we are calling `Console.WriteLine` twice, which means the print command is executed twice.

```cs  
public class Program {  
    public static void Main(string[] args) {  
        Console.WriteLine("Hello World!");
        Console.WriteLine("... and Pietarsaari!"); 
    }  
}   
```

This would print


```console
Hello World!
... and Pietarsaari!
```


**With this information, you should be able to do the second exercise.**