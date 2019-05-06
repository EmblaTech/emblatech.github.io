---
layout: post
title: "JavaScript concepts & best practices"
quote: "JavaScript is a technology that has become essential in the IT industry. Simply as it’s the base language to develop most of the popular languages we use today."
image:
      url: /media/medium/denise-jans-1203943-unsplash.jpg
video: false
comments: true
author_name: Rohan Fernando
author_url: https://github.com/EmblaTech
author_pic: istockphoto-836272842-612x612.jpg
---

<style type="text/css"> #post-info { background-color: rgba(0,0,0,.5); padding: 10px; } </style>


JavaScript is a technology that has become essential in the IT industry. Simply as it’s the base language to develop most of the popular languages we use today. It’s used in both front-end (Angular) and back-end (NodeJS) development. Knowing the core concepts in JavaScript is always better when writing a cleaner and more readable code in JavaScript and best practices are always good to know. JavaScript is a single threaded language since execution is done one line at a time.

JavaScript is actually based on the ECMAScript standard but JavaScript also has other additional features that are not in the ECMA specifications/standard like DOM APIs i.e. : document.getElementById(‘id’);

## Closures

A closure is an inner function that has access to the outer (enclosing) function’s variables. The inner function has access to not only to the outer function’s variables, but also to the outer function’s parameters. When writing some JavaScript code closures are used all over when callback functions are passed (function that is passed to another function as a parameter and executed with the context of the calling function).

One example could be passing a function to the success and error methods. JavaScript can have functions that are nested within other functions and that function can be nested within another. JavaScript can also access outer function’s variables even though the outer function’s execution got completed. This ability comes from JavaScript Closures. So even when the current function ended its execution, the callback function is still able to reference those current function’s variables with the use of closures.

An example of a closure is as follows:

<iframe src="https://medium.com/media/778ed6403e4903ded85da95b619cfc59" frameborder=0></iframe>

In the above example when the “addTo” method is executed with the parameter 100, the “passed” parameter in the “addTo” will have a value of 100 and the add method is the closure accessing the outer function’s “passed” parameter and function scoped ‘funcVar’ variable. After executing the addTo with the 100, it will send an add method as a return value but it’s still not executed since we need pair of brackets for the function to get execute. After that the returned inner function will be called with the value 3. Then the functVar value of 10 + the earlier passed value of 100 to addTo function + inner variable with 3 is added together and returned back. This is a basic example of what can be achieved through the use of closures.

Another real example where it creates an event trigger function with outer function’s variable is as follows.

<iframe src="https://medium.com/media/7e0322936c87ec02b94e9179514903bc" frameborder=0></iframe>

### Variable declarations

JavaScript is a dynamically typed language, meaning that when a variable is created, that variable does not have any particular type of value that it can be assigned to it and it may have any type of value in the later parts of the code. There are two ways to declare variables in JavaScript. Common way is using “var” keyword.

When declaring a variable using the “var” keyword, that variable will be defined in the function scope but when declaring with let keyword it is bound to the scope of the specific scope it was declared.

Eg:

Using ‘var’ keyword

<iframe src="https://medium.com/media/80ca15e4cfe88896dea7521a165b4cb2" frameborder=0></iframe>

Using ‘let’ keyword

<iframe src="https://medium.com/media/e6df22a23bfe4db7688f50e15ae2371b" frameborder=0></iframe>

In the above example using the “var” keyword in the for loop, normally it is expected to have the variable to be only within the “for loop” but it is actually created for the function itself, so the “console.log(i);” below will print the a value that the “for loop” has ended up with. If it is necessary to use the variable “i” only for the “for loop” scope, then use let keyword to declare the variable and the “console.log(i);” will print undefined since we have used let and its created only for the for loop and will not be accessible outside of it.

A variable without using var or let keyword but it is a bad practice since JavaScript will go through the current scope to find it and if it does not then it will go to the parent function scope and so on until it finds. If JavaScript engine could not find anything and once it searches it in the global scope, it will create a variable with the name and give back the reference for it and will pollute the global scope when variables are created without using “var” or “let” but if it is referring to a variable that was declared in a parent function scope, that will be okay.

### Function Declaration vs. Function Expression vs. Immediately-Invoked Function Expression (IIFE)

* **Function Declaration**

    function foo() { ... }

When declaring a function it gets hoisted to the top so if it is written at the bottom and then call it at the top it will actually call without any errors since all the function declaration are moved to the top. This is called **function hoisting**. These functions can be called both after and before the definition.

i.e.:

* **Function Expression**

1. Named Function Expression

var foo = function bar() { … }

2. Anonymous Function Expression

var foo = function() { … }

foo() can be called only after creation. i.e.:

functionOne(); // TypeError: undefined is not a function 
 var functionOne = function() { console.log(“Hello!”); };

It’s always better to give a name to functions and avoid using anonymous functions since when some error occurs. it will be harder to debug when the error message is “cannot access somevariable1 from undefined in anonymous function line:1234”

* Immediately-Invoked Function Expression (IIFE)

As the name implies, it executes immediately after its created and global scope it not polluted. There are two ways of defining these kind of method but no difference between them and it is okay to use either of them.

First way:

    (function(){

    })();

Second way:

    (function(){

    }());

JavaScript also enables us to pass some variables to the IIFE function and get a local copy inside the function and use it there,

<iframe src="https://medium.com/media/fde36f64e1026467bb05bccd17abec91" frameborder=0></iframe>

### Hoisting

In JavaScript, all variable and function declarations are hoisted to the top of their scope. Scope can be a particular function or the global scope.

Eg:

<iframe src="https://medium.com/media/a19e11bded256146b20fe887a9d5ebdf" frameborder=0></iframe>

Actually what is happening in this is variable “name” declaration is moved to the top of the function and initially if it doesn’t have any assigned value for the variable, it will be undefined at execution. If the “name variable wasn’t declared inside the function, it will actually take the name value that is declared in the global scope and print “Original name was Baggins” instead of “Original name was undefined”. The actual order the JavaScript executes the above code is given below.

<iframe src="https://medium.com/media/cb797970e4026819baaeebfe68a6356d" frameborder=0></iframe>

Order of the execution in JavaScript is given below

![](https://cdn-images-1.medium.com/max/2000/1*6AUcJ-aYjPti0U1RWBbz5Q.png)

### Truthy and falsy

In JavaScript, a truthy value is a value that is considered true when evaluated in a Boolean context. All values are truthy unless they are defined as falsy (i.e., except for false, 0, “”, null, undefined, and NaN).

Eg:

<iframe src="https://medium.com/media/cbeb4e45b2bc88c8092b56e3c95602b0" frameborder=0></iframe>

In the above example a string with some content is actually a truthy value, so the condition will evaluate to true and print out “First Name is John”

### Variable Comparison

In JavaScript, there are two ways to compare two values or variables.

* Strict Equality Comparison / Strict equality (===) operator

* Abstract Equality Comparison / Loose equality (==) operator

The Strict equality operator behaves identically to the loose equality operator except no type conversion is done, and the types must be the same to be considered equal. The == operator will compare for equality after doing any necessary type conversions. The === operator will not do the conversion, so if two values are not the same type === will simply return false. It is always a best practice to compare with the strict equality

eg:

0 == ‘0’ // true 
 0 === ‘0’ // false

### Ternary assignment

JavaScript can assign values based on their truthy values, so when a bunch of variables are given for an assignment that are separated with an OR operator ( || ), JavaScript goes through each and every value from left to right and assigns the first value that is truthy.

eg:

    var firstName = “”;
    var lastName = “Stallone”;
    var someVar = firstName || lastName;

In the above example, since firstName is an empty string and is a falsy value it will evaluate the next value lastName and will assign it. If all of the values evaluate to false, then the last falsy value will be the assigned.

**References**
[**Variable and Function Hoisting in JavaScript - A Drip of JavaScript**
*One of the trickier aspects of JavaScript for new JavaScript developers is the fact that variables and functions are…*adripofjavascript.com](http://adripofjavascript.com/blog/drips/variable-and-function-hoisting.html)
[**What (function (window, document, undefined) {})(window, document); really means**
*In this post, we're going to explore what the title suggests, and offer explanations as to what this self invoked…*toddmotto.com](https://toddmotto.com/what-function-window-document-undefined-iife-really-means/)
[**When is JavaScript synchronous?**
*I have been under the impression for that JavaScript was always asynchronous. However, I have learned that there are…*stackoverflow.com](https://stackoverflow.com/questions/2035645/when-is-javascript-synchronous)
[**JavaScript Best Practices: Tips & Tricks to Level Up Your Code | Codementor**
*Learning new things everyday is part of what makes being a rational human being great. And as developers, it is part of…*www.codementor.io](https://www.codementor.io/johnnyb/javascript-best-practices-du107mvud)
[**getify/You-Dont-Know-JS**
*You-Dont-Know-JS - A book series on JavaScript. @YDKJS on twitter.*github.com](https://github.com/getify/You-Dont-Know-JS)
[**Advanced JavaScript Programming | Tutorials | Webucator**
*This Advanced JavaScript Programming tutorial is based on Webucator's Advanced JavaScript Programming course.*www.webucator.com](https://www.webucator.com/tutorial/advanced-javascript/index.cfm)
[**What is the difference between JavaScript and ECMAScript?**
*What's the difference between ECMAScript and JavaScript? From what I've deduced, ECMAScript is the standard and…*stackoverflow.com](https://stackoverflow.com/questions/912479/what-is-the-difference-between-javascript-and-ecmascript)
[**Understand JavaScript Closures With Ease**
*Closures allow JavaScript programmers to write better code. Creative, expressive, and concise. We frequently use…*javascriptissexy.com](http://javascriptissexy.com/understand-javascript-closures-with-ease/)
[**What is the difference between a function expression vs declaration in JavaScript?**
*What is the difference between the following lines of code? //Function declaration function foo() { return 5; }…*stackoverflow.com](https://stackoverflow.com/questions/1013385/what-is-the-difference-between-a-function-expression-vs-declaration-in-javascrip)
[**Which equals operator (== vs ===) should be used in JavaScript comparisons?**
*I'm using JSLint to go through JavaScript, and it's returning many suggestions to replace == (two equals signs) with…*stackoverflow.com](https://stackoverflow.com/questions/359494/which-equals-operator-vs-should-be-used-in-javascript-comparisons)
