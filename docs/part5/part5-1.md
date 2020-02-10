---
title: "Object Oriented revision"
parent: "Part 5 - Objects continued"
permalink: /part5/1/
nav_order: 1
published: false
---

# Object Oriented programming revisited

What is object-oriented programming all about? We'll rewind a little.

Let's inspect how a clock works. The clock has three hands: hours, minutes and seconds. The second hand increments once every second, the minute hand once every sixty seconds, and the hour hand once in sixty minutes. When the value of the second hand is 60, its value is set to zero and the value of the minute hand is incremented by one. When the minute hand's value is 60, its value is set to zero and the hour hand value is incremented by one. When the hour hand value is 24, it is set to zero.

Time is always printed in the form **hours: minutes: seconds**, where the hours are represented by two digits (eg. 01 or 12), minutes by two digits, and seconds also by two digits.

Below is an implementation of the clock with integer type variables (the printing could be isolated into its own method, but that has not been done here).


```cs
static void Main(string[] args)

int hours = 0;
int minutes = 0;
int seconds = 0;

while (true)
{
  // 1. Printing the time
  if (hours < 10)
  {
    Console.Write("0");
  }
  Console.Write(hours);

  Console.Write(":");

  if (minutes < 10)
  {
    Console.Write("0");
  }
  Console.Write(minutes);

  Console.Write(":");

  if (seconds < 10)
  {
    Console.Write("0");
  }
  Console.Write(seconds);
  Console.WriteLine();

  // 2. The second hand's progress
  seconds = seconds + 1;

  // 3. The other hand's progress when necessary
  if (seconds > 59)
  {
    minutes = minutes + 1;
    seconds = 0;

    if (minutes > 59)
    {
      hours = hours + 1;
      minutes = 0;

      if (hours > 23)
      {
        hours = 0;
      }
    }
  }
}
```


As demonstrated by reading the example above, the functioning of a  clock made up of three **int** variables is not very clear to someone reading through the source code. It's difficult to "see" what's going on. A famous [**Programmer**](https://en.wikipedia.org/wiki/Kent_Beck) remarked *"Any fool can write code that a computer can understand .Good Programmers write code that humans can understand"*.