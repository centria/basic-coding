---
title: "Calculations"
parent: "Part 1 - The beginning"
permalink: /part1/3/
nav_order: 3
published: true
---

# Calculations with numbers

Calculations as such should be quite familiar to you already. They are done with same operators in code, as they are in mathematics: addition with **+**, substraction with **-**, multiplication with **\*** and division with **/**. The order of calculation is also very traditional. From left to right, taking into account any brackets, and multiplication and division before addition or substraction.

```cs
int first = 2;
Console.WriteLine(first); // prints 2
int second = 4;
Console.WriteLine(second); // prints 4

int sum = first + second; // variable sum is set with the value of the sum from variables first and second
Console.WriteLine(sum); // prints 6
```

## Calcuation order with brackets.

You can change the order of calculation with brackets, if you wish.

```cs
int calcWithBrackets = (1 + 1) + 3 * (2 + 5);
Console.WriteLine(calcWithBrackets); // prints 23

int calcWithoutBrackets = 1 + 1 + 3 * 2 + 5;
Console.WriteLine(calcWithoutBrackets); // prints 13
```

