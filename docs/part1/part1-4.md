---
title: "Conditional and comparison"
parent: "Part 1 - The beginning"
permalink: /part1/4/
nav_order: 4
published: true
---

# Conditionals and comparison

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
if (false) 
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

## Options, or Else!

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

If the conditional statement has an else branch, the code block defined for the else is run, if the if-clause is evaluated as false. Notice the indentation and lines!

## More options, else if

If you want to have more than one option, use **else-if-structure**. It is similar to else, but has an if-conditional. There can be multiple of them, and they come after if, before else.

```cs
int number = 3;

if (number == 1) 
{
    Console.WriteLine("Number is one!");
} 
else if (number == 2) 
{
    Console.WriteLine("Number is two!");
} 
else if (number == 3) 
{
    Console.WriteLine("Number is three!");
} 
else 
{
    Console.WriteLine("Number is something else!");
}
```

```console
Number is three!
```

In the example above, we first check if the number is equal to 1. As it is not, we move to the first else-if and compare the number to value of 2. As this is not the case, we move forward, and compare our variable's value to 3. As this is true, we execute the code inside the code block, and print the message shown above. We do not go into the else-statement, because an earlier statement evaluated as true.

## Order of comparison

As any code, the comparisons are done in order, from top to bottom, left to right. When we reach a conditional which evaluates to **true**, we execute that block and end comparison.

```cs
int number = 42;

if (number == 0) 
{
    Console.WriteLine("The number is 0.");
} 
else if (number > 0) 
{
    Console.WriteLine("The number is greater than 0.");
} 
else if (number > 2) 
{
    Console.WriteLine("The number is greater than 2.");
} 
else 
{
    Console.WriteLine("The number is smaller than 0.");
}
```

```console
The number is greater than 0.
```

In the example, the condition **number > 0** is evaluated as **true**, so we execute the code block related to that, and end comparison. Even if the next statement would also evaluate to true, we do not reach that part of the code (and never can).

## Conditional statement and boolean variable

The evaluated value of an expression inside the if-clause's brackets must be a **boolean**. Boolean is a representation of a truth-value, and is either **true** or **false**.

```cs
bool truthValue = true;
Console.WriteLine("The value of truthValue is " + truthValue);
```

```console
The value of truthValue is True
```

Or with a conditional,

```cs
bool truthValue = true;
if (truthValue)
{
    Console.WriteLine("This is awesome!");
}
```
```console
This is awesome!
````

Comparison can be used outside statements, as well. Then the value of a boolean is stored into a boolean variable until further use.


```cs
int first = 1;
int second = 3;
bool isFirstLargerThanSecond = first > second;
```

Now the value of **isFirstLargerThanSecond** is **false**. Let's change the example a bit and continue:

```cs
int first = 1;
int second = 3;
bool isFirstSmallerThanSecond = first < second;

if (isFirstSmallerThanSecond)
{
    Console.WriteLine("1 is less than 3!");
}
```

```console
1 is less than 3!
```

## Remainder

Remainder is not used as frequently, but is a nice tool, especially if we want to check if something is divisible by some other number.

```cs
int remainder = 7 % 2;
Console.WriteLine(remainder); // prints 1
Console.WriteLine(5 % 3); // prints 2
Console.WriteLine(7 % 4); // prints 3
Console.WriteLine(8 % 4); // prints 0
Console.WriteLine(1 % 2); // prints 1
```

As remainder is an operation similar to other calculations, we can use it in for example an if clause

```cs
string userInput = Console.ReadLine();

int number = Convert.ToInt32(userInput);


if ((number % 400) == 0) 
{
    System.out.println("The number " + number + " is divisible by four hundred");
} 
else 
{
    System.out.println("The number " + number + " is not divisible by four hundred");
}
```

## Conditionals an equality of variables

In most programming languages, including C#, string is of reference type, and for example integer, boolean and double are value types. 

In some of the programming languages, this means that string comparison has to be done differently from other variables. **C# is more forgiving.** We can compare two strings with **==** operator, at least in this point of the course.

For example the following works in C#, while in most other languages it would not:

```cs
string a = "word";
string b = "word";
Console.WriteLine(a == b);
```

```console
True
```

Other way to compare strings, is with **equals-method**. The method compares the value of an object. We will go deeper into that later, now it is enough for you to know such a method exists.

```cs
string a = "word";
string b = "word"; 

Console.WriteLine(a.Equals(b));
```

```console
True
```

**You can now do the exercises for conditionals**