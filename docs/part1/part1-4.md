---
title: "Conditional and comparison"
parent: "Part 1 - The beginning"
permalink: /part1/4/
nav_order: 4
published: true
---

# Conditionals and and alternatives

So far, our programs have been quite linear, going step-by-step in order, without any options or alternatives. We do often want options in our software, meaning that functionality is dependant on the state of variables in the program. 

For the program to **branch** with for example user input, we will need a **conditional statement** in the program. The most simple conditional is

```cs
Console.WriteLine("Hello world!");
if (true) 
{
    Console.WriteLine("This is always printed!");
}
```

```console
Hello world!
This is always printed!
```

On the other hand, we could make a part of our code unreachable:

```cs
Console.WriteLine("Hello world!");
if (true) 
{
    Console.WriteLine("This is never printed!");
}
```

```console
Hello world!
```

This is, of course, quite unnecessary, even though possible.

A conditional statement begins with a keyword **if**, which is followed by **brackets ( )**. Inside the brackets is the expression that is evaluated. The result of the evaluation is a truth value. In the examples above there was no need for evaluation, as they were already truth values.

The brackets are followed by a code block, enclosed in **{ }**. The code inside the block is run, if the expression inside the brackets is evaluated as true.

Let us examine an example, where we compare integers.

```cs
int number = 11;
if (number > 10) 
{
    Console.WriteLine("The number was larger than 10");
}
```

If the expression in the conditional statement is evaluated as true, above in the line of "if the value in the variable number is greater than 10", the code execution moves inside the block defined within the conditional statement.

If the statement would be false, the code execution moves to the next line after the closing **}** of the code block.

Notice, that there is no semicolon after the if-clause, as the statement does not end after the conditional part.

### Reminder of code indent

The code inside a block should be indented. For example, the code inside an if statement should be indented more than the keyword **if** in the code. The ending **}** should be at the same level as the if.

```cs
int number = 11;
if (number > 10) 
{
Console.WriteLine("This indention is wrong");
}
```

```cs
int number = 11;
if (number > 10) 
{
    Console.WriteLine("This indention is right");
}
```

## Relational operators

The following are relational operators:

|Sign| Meaning |
|:--:|:---|
| >  | greater than |
| >= | greater than or equal to |
| <  | less than |
| <= | less than or equal to |
| == | equal to |
| != | not equal to |


```cs
int number = 55;

if (number != 0) 
{
    Console.WriteLine("The number was not equal to zero");
}

if (number >= 1000) 
{
    Console.WriteLine("The number was at least 1000");
}
```

```console
The number was not equal to zero
```

## Else

If the expression inside the if-clause evaluates as false, the code execution continues to the next statement. This is not always desired, but we want to have an option for the cases, when the if is evaluated as false.

This can be achieved with an else-statement, that is combined to the if-statement.

```cs
int number = 4;

if (number > 5) 
{
    Console.WriteLine("Your number is greater than five!");
} 
else 
{
    Console.WriteLine("Your number is 5 or less!");
}
```

```console
Your number is 5 or less!
```

If the conditional statement has an else branch, the code block defined for the else is run, if the if-clause is evaluated as false. Notice the indentation!