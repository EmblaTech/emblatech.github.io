---
layout: post
title: "The Importance of Code Quality"
quote: "Good quality code can be considered as an essential property of software. If the code quality is not good enough, it could lead to financial losses or waste of time due to maintenance, modification or adjustments."
image:
      url: /media/medium/denise-jans-1203943-unsplash.jpg
video: false
comments: true
author_name: Sugandika Jayasinghe
author_url: https://github.com/EmblaTech
author_pic: istockphoto-836272842-612x612.jpg
---

<style type="text/css"> #post-info { background-color: rgba(0,0,0,.5); padding: 10px; } </style>


> # *“Measuring programming progress by lines of code is like measuring aircraft building progress by weight.” — Bill Gates*

Good quality code can be considered as an essential property of software. If the code quality is not good enough, it could lead to financial losses or waste of time due to maintenance, modification or adjustments. Characteristics of a good quality code are efficiency, reliability, robustness, portability, maintainability and readability. **Efficiency** is directly related to the software performance and speed. Software quality can be evaluated with the efficiency of the source code. Nobody likes to use software which takes a long time to perform an action. Efficiency can be improved by writing reusable code and removing unnecessary or redundant code. And also it is important to reduce resource consumption and using appropriate data types, functions and looping in appropriate places. **Reliability** is the ability to perform the operations consistently without any failures, every time it runs. The software would be less useful if the code functions differently every time it runs even though same input is given in the same environment. Reliability can be increased by frequent code reviews and thorough testing of code in every possible way. Proper error handling and exception handling leads to making reliable software.

**Robustness** can be described as the ability to cope up with the errors during the program execution in spite of the unusual conditions. End users feel uncomfortable if they get a strange unfamiliar message when they do something wrong. Typically software is fragile and can be buggy, but the error handling needs to be done gracefully. In order to achieve robustness software has to be testes with every condition: both usual and unusual. Clear and understandable error messages have to be provided for the end users so that they can easily understand the system. **Portability** is the ability of the source code to be run in different machines and platforms as much as possible. When the software is transferred from one environment to another and in case if the programmers have to re-write the same code again, it would be a definite waste of time and effort. Multiple platform support can be planned at the beginning of developing the software. Code can be written that could work on every possible environment.

**Maintainability** is about writing code in a way which is easy to add new features, modify existing features or fix issues with a minimum effort without the risk of affecting other related modules and functionalities. Obviously software needs new features and bug fixes. So it is important that the source code to be easy to understand, easy to find what needs to be modified, easy to do changes and easy to check that the changes do not introduce any new issues. Maintainability can be achieved by following the best practices of coding such as following proper naming convention for class names, methods and variables. Proper indentation, formatting style and better technical documentation help to understand the code easily. Appropriate comments or summary descriptions can be written at the top of the files, classes or functions. **Readability** can be considered as the ability of allowing the easily, quickly and clearly understandable by someone new or someone that hasn’t seen it a while. It is important to ensure that everybody can understand the code written by everyone else. If the code is crappy and badly written, it would be very hard to figure out what the code actually does and where changes need to be taken place. More time could be wasted when trying to figure out how it all fits together before making any action and even end up re-writing the coding assuming it is buggy and carelessly written. Readability can also be improved by following proper naming conventions, indentation styles and using appropriate comments.

### **Improving Code Readability**

As explained before, readability can be improved by use of comments, appropriate naming and proper indentation. Use of comments provides the developers some additional information about the written code which helps them to understand the code easily and quickly. Comments may consist of the purpose and reason behind the piece of code and expected functionally. Comments help the developers to discuss about business needs, special case behaviors, remaining tasks and temporary solutions. Proper use of comments improves the code maintainability and supports issue investigation. It reduces the time and effort required to understand an existing code base. Without comments, a developer can be easily got lost in the code and won’t understand the purpose of the code.

Appropriate naming has a significant naming in program readability. It helps the programmers to quickly understand what the code is doing, and to fix issues or do modifications. Reckless names for variables, classes or methods can lead to confusion about the roles that these components play. Using meaningless names such as a,b,c is not recommended. Instead the developers can always choose meaningful names. Proper indentation of code lines is also important. Proper indentation make the code structure look more obvious and making it easier to follow improving the readability of the code. If the code is poorly indented, other programmers will have a difficult time going through the existing code and understanding its functionality. Proper code indentation improves readability, understandability, maintainability and extensibility.

**References**
[**Writing readable source code | Software Sustainability Institute**
*It's recommended that projects adopt a set of coding conventions. Not only does this promote readable code, it helps…*software.ac.uk](https://software.ac.uk/resources/guides/writing-readable-source-code)
[**Importance of code indentation**
*Indentation is one of the most important aspects in any programming domain. But this is often the most neglected part…*mrbool.com](http://mrbool.com/importance-of-code-indentation/29079)
[**What is Code Efficiency? - Definition from Techopedia**
*Code Efficiency Definition - Code efficiency is a broad term used to depict the reliability, speed and programming…*www.techopedia.com](https://www.techopedia.com/definition/27151/code-efficiency)
