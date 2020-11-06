# Scope, Closures, and Composition

> **Sophie Cruetz on 11/03/19**

**Repl.it:** [https://repl.it/repls/OrnateOpaqueSequences](https://repl.it/repls/OrnateOpaqueSequences)

Example of a function composition taking the form `f(g(x))`

```javascript
function multiplyThenDo(n1, n2, callback) {
  let product = n1 * n2;
  return callback(product);
}

function addFive(num) {
  return num + 5;
}

function square(num) {
  return num * num;
}

multiplyThenDo(2, 3, addFive);
//=> 11

multiplyThenDo(2, 3, square);
//=> 36
```

## **Iterators**

* `for` loop
* `while` loop
* `forEach()` → implies that we pass in every element in the array that we're iterating through
  * Acts on the object but does not return it as part of the function
* `map()` → iterates over each element, performs an operation on each element \(dictated by the callback/function\), and returns a new array
  * Takes three arguments → callback, index, array
  * Only callback is required
* `filter()`

## Arrow Functions

* Boilerplate example: `parameter => function expression`
  * There's an implicit return in all arrow functions that do not use curly brackets \(`{}`\) in their declaration
  * If an arrow function returns an object, it needs to wrapped in curly braces and explicitly returned

## **Higher Order Functions**

* A higher order function accepts or returns another function
  * Aka it uses a callback
  * Look at the return value to see the function that is being returned and if any arguments are required

## **Closures**

* A closure is a higher order component that makes use of the lexical environment within its function
* One way to use a closure is to create a variable that holds a function, then call the variable to invoke the function
* IIFEs \(Immediately Invoked Function Expressions\) are closures as well
  * Wrap the whole function in parentheses and assign it a variable, then the function can be invoked by calling the variable
* Placing parentheses at the end of the function invokes the function

{% tabs %}
{% tab title="Closure" %}
```javascript
function generateCounter() {
  let counter = 0;
  console.log(`Initializing counter at ${counter}.`);
    return function() {
      console.log(++counter);
    }
}

let counterOne = generateCounter();
//=> Initializing counter at 0.
counterOne();
//=> 1
counterOne();
//=> 2
counterOne();
//=> 3
let counterTwo = generateCounter();
//=> Initializing counter at 0
counterOne();
//=> 4
counterOne();
//=> 5
counterTwo();
//=> 1
counterOne();
//=> 6
counterTwo();
//=> 2
counterTwo();
//=> 3
```
{% endtab %}

{% tab title="IIFE" %}
```javascript
let counterFunc = (function() {
  let counter = 0;
  console.log(`Initializing counter at ${counter}.`);
  return function() {
    console.log(++counter);
  }
})()
//=> Initializing counter at 0.

counterFunc();
//=> 1
counterFunc();
//=> 2
counterFunc();
//=> 3
counterFunc();
//=> 4
counterFunc();
//=> 5
```
{% endtab %}
{% endtabs %}

