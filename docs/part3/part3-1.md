---
title: "Discovering errors"
parent: "Part 3 - Arrays"
permalink: /part3/1/
nav_order: 1
published: true
---

We've so far been practicing the fundamentals of the language, such as variables, conditionals, loops, and methods. Let's now move on to look at some of the factors affecting the understandability of programs, and how errors are found.

# A Programmer Is Blind to Their Own Code

A programmer often becomes blind to their code. Let's familiarize ourselves with this effect with the aid of the short video below. Count how many times the white-shirted players pass the ball between each other. The video contains instructions in English.

[![Link to video: http://www.youtube.com/watch?v=Ahg6qcgoay4](http://img.youtube.com/vi/Ahg6qcgoay4/0.jpg)](http://www.youtube.com/watch?v=Ahg6qcgoay4)

There's something else that also happens in the video that may go unnoticed at first. This effect is known as perceptual blindness, and is explained by the fact that as we focus on a specific task, our brains tend to filter out information that is irrelevant to that task. However, we don't always know what information is, in fact, essential and what is not - an example of this being when we study. Concentrating on a specific part of a study exercise can lead to relevant information being filtered out.

Fortunately, applying oneself to a given task lessens the occurrence of perceptual blindness. In other words, practice develops one's ability to distinguish between relevant and irrelevant information.

One way in which perceptual blindness manifests itself in programming practice is when concentrating on a specific part of a program draws attention away from seemingly correct, yet erroneous parts. For instance, while inspecting the correctness of a program's output, a programmer may fixate on the print statements, and mistakenly neglect some aspects of the logic.

Likewise, a programmer may focus on the most complicated aspect of a program featuring a loop, when in fact the error lies somewhere else completely. An example of this is the program below, which is used to calculate the average of user-inputted values. It contains an error, and when searching for it, the loop is typically the first target of focus.