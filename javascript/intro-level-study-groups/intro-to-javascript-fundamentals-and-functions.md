# Intro to JavaScript Fundamentals and Functions

> **Beth Schofield on 01/25/20**

## **Data Types**

* Primitives
  * `number`
  * `string` \(`' '`, `" "`, ``` ```\)
  * `boolean` \(`true`, `false`\)
  * `undefined`
* Complex is the opposite of Primitive
  * `object`
    * `null`
    * `array` \(`[ ]`\)
    * `object` \(`{ }`\)
  * `function`
* `typeof` → Checks the data type

## **Hoisting**

* `var` → Scoped at global and function levels
  * Can be declared without assigning a value \(i.e. the value can be assigned later\)
    * Can store anything as its value
  * Gets hoisted
* `let` → Scoped at global, function, and block levels
  * Can be declared without assigning a value \(i.e. the value can be assigned later\)
  * Doesn't get hoisted
* `const` → Scoped at global, function, and block levels
  * Must be assigned a value when it's declared
    * Value can't be reassigned after it's been declared
  * Doesn't get hoisted
* `function`
  * Gets hoisted
  * Watch out for functions that are saved to variables as they only get hoisted if they are declared a `var` and then their value is `undefined` until the execution phase

> **Beth Schofield on 03/03/20**

## Functions

* Anonymous functions are usually used in callbacks
  * Iterators oftentimes use callback functions

{% tabs %}
{% tab title="ES5" %}
```javascript
// Standard function

function doStuff() {
  console.log("doing stuff");
}


// Anonymous function

function() {
  console.log("doing stuff");
}


// Anonymous function used in a callback

const stuff = ["remote", "piano", "pillow"];

stuff.forEach(function(thing) {
  console.log(thing);
});


// Anonymous function expression stored in a variable

var doStuff = function() {
  console.log("doing stuff");
};
```
{% endtab %}

{% tab title="ES6" %}
```javascript
// Standard function

function doStuff() {
  console.log("doing stuff");
}

function whatData() {
  console.log("what?");
}

// Anonymous arrow function with implicit return

() => console.log("doing stuf");


// Anonymous arrow function with explicit return

() => { return console.log("doing stuff") };


// Anonymous arrow function used in a callback

const moreThings = [doStuff, whatData];

moreThings.forEach(item => item());
```
{% endtab %}
{% endtabs %}

* Arrow functions allow you to pass an implicit argument
  * Also works with `console.log`

{% tabs %}
{% tab title="implicitArguments" %}
```javascript
const tooHype = thing => thing.toUpperCase();
const phrases = ["hey there", "wassssup", "good day sir"];
// const hypePhrases = phrases.map(phrase => tooHype(phrase));
const hypePhrases = phrases.map(tooHype);
console.log(hypePhrases);
//=> LOG: ["HEY THERE", "WASSSSUP", "GOOD DAY SIR"]
//=> undefined
```
{% endtab %}
{% endtabs %}

