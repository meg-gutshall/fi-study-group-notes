# Intro to JavaScript with Avi

> **Avi Flombaum on 02/21/20**

* The DOM is there so you can manipulate the web page after it's been loaded
* JavaScript is not interesting because of React, it's interesting because of the DOM
* Understanding the DOM gives you granular control over higher-level abstractions \(JavaScript libraries\)
* A node console is the irb of JS

## Functions as Objects

* In Ruby, the method itself is not an object
* Ruby is an expression-oriented language --&gt; every expression returns a value
* In JS, the function itself is an object
* Using node console, type `function_name.` to get all it's methods

## Types of Functions

* A declared function is the "normal" way of declaring a function
  * "F better be the first line of that code if you want it to be a declared function." —Avi Flombaum
* A function expression is when you assign the function declaration to a variable or when you create a method on an object
  * o = {}
  * o.greeting = function\(\) { return "Hi!" }
* An anonymous function is a function without a name
  * Can be wrapped in parentheses
* An IIFE is a parentheses-wrapped anonymous function followed immediately by another invoking parentheses

