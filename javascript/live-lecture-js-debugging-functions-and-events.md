# Live Lecture: JS Debugging, Functions, & Events

> **Z Drake on 08/11/20**

## JS Functions

### Procedural vs. Object Oriented vs. Functional

* Procedural — a series of steps to be executed in order where each step relies on the previous
* Functional — a group of functions \(or methods\) that can all act independently but also work together
* Object Oriented — templates \(classes\) that allow us to group together related methods and properties

### What Are Functions?

* In Ruby, we have methods that can be run to perform certain tasks
* In JavaScript, we have function that can be executed to perform certain tasks
* Functions are actually types of objects which means they can me treated as we would treat any other object, and they can be:
  * Passed as arguments to other functions
  * Returned from other functions
  * Assigned to variables
  * Stored in objects and arrays

### Ruby Lambdas

* In Ruby, we cannot pass methods as arguments to other methods or store them in arrays or objects
* Instead, we have procs and lambdas which can be treated similarly to how we treat JS functions
* When we are working in OO Ruby, we will see...

### JS Functions vs. Methods

* JS methods are just functions that belong to a specific object
* **Technically** most javascript methods are going to be called on some sort of object
  * Even if we define it globally, it will be a method of the global object
* Remember: the default return value of a JS function is **undefined**
  * Unlike in Ruby, we must explicitly return

## JS Events

### Listening for Events

* JS can listen for things that happen in the browser
* What are some of the most common events?
  * Click
  * Key press
  * Form submission
  * Scroll
* We can use JS's listening skills to make things happen when a user interacts with our application

### JS Event Flow

* Unlike in Rails, things will NOT automatically happen in JS
* If we want to listen for an event we must:
  * First select an element that we want to add the event listener to
  * Call the addEventListener method
  * Pass that method the event type and a callback function to be executed when that event occurs
* This callback function will NOT be executed until the event occurs
* When an event is triggered, we will always have access to that event inside the callback function if we pass it an argument

### Capturing and Bubbling

* Bubbling and capturing are what happen when you have the same type of event listener on nested elements
  * If the event bubble, the inner element's listener will fire first
  * If the event captures, the outer element's listener will fire first
  * By default, most events bubble
* Because the innermost listener function will be executed first, we do not usually need to stop events from bubbling

## Example Notes

* Node is to JS as irb is to Ruby

