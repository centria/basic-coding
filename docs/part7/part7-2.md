---
title: "Introduction to testing"
parent: "Part 7 - Projects"
permalink: /part7/2/
nav_order: 2
published: true
---

# Testing

Let's take our first steps in the world of program testing.

## Error Situations and Step-By-Step Problem Resolving

Errors end up in the programs that we write. Sometimes the errors are not serious and cause headache mostly to users of the program. Occasionally, however, mistakes can lead to very serious consequences. In any case, it's certain that a person learning to program makes many mistakes.

You should never be afraid of or avoid making mistakes since that is the best way to learn. For this reason, try to break the program that you're working on from time to time to investigate error messages, and to see if those messages tell you something about the error(s) you've made.

The report in the address [http://sunnyday.mit.edu/accidents/MCO_report.pdf](http://sunnyday.mit.edu/accidents/MCO_report.pdf ) describes an incident resulting from a more serious software error and also the error itself.

The bug in the software was caused by the fact that the program in question expected the programmer to use the [International System of Units](https://en.wikipedia.org/wiki/International_System_of_Units) (meters, kilograms, ...) in the calculations. However, the programmer had used the [American Measurement System](https://en.wikipedia.org/wiki/English_Engineering_units) for some of the system's calculations, which prevented the satellite navigation auto-correction system from working as inteded.

The satellite was destroyed.

As programs grow in their complexity, finding errors becomes even more challenging. The debugger integrated into NetBeans can help you find errors. The use of the debugger is introduced with videos embedded in the course material; going over them is always an option.

## Stack Trace

When an error occurs in a program, the program typically prints something called a stack trace, i.e., the list of method calls that resulted in the error. For example, a stack trace might look like this: