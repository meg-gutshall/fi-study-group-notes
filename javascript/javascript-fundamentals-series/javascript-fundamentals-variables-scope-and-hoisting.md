---
description: >-
  Started as a one-on-one rundown of the JS/Rails project assessment held when
  no other students came to a study group (JavaScript Building Blocks on
  02/20/20) and later became a JS Fundamentals group
---

# JavaScript Fundamentals: Variables, Scope, & Hoisting

> **Beth Schofield on 02/20/20, 03/31/20, & 04/28/20**

* The main topics are scope and hoisting
  * May include `this` as well
* What are the two phases of running a JavaScript file?
  * Compilation phase
  * Execution phase

## Variables and Scoping

* There are three good ways to declare a variable and one **really bad** one:
  * Good: `const`, `let`, `var`
  * Bad: no variable type
* `var` is able to be overwritten \(or "redeclared"\), `let` and `const` are not

## Scope

* Scope is what we have access to at any given time
  * The context and our access rights
* Lexical scope involves the ability to extrospect \(look outwards\) but the inability to introspect \(look inwards\)
  * The order in which you visually see the code written
  * Where in the code variables and functions are declared
* Scope levels → How do the variable types relate to them?
  * Global scope
  * Functional scope
  * Block scope

{% tabs %}
{% tab title="Scope 1" %}
```javascript
function telescope() {
  var a = "near";
  let b = "near";
  const c = "near";
  d = "near";
  
  if (true) {
    var a = "far";
    let b = "far";
    const c = "far";
    d = "far";
  }
  
	console.log(`The (var) a will be ${a}.`);
	console.log(`The (let) b will be ${b}.`);
	console.log(`The (const) c will be ${c}.`);
	console.log(`The (no variable type) d will be ${d}.`);
  
  return "Function executed";
}

telescope();

// Predictions:
// var a = far
// let b = near
// const c = near
// no variable type d = far

// What are our predictions and why?
// What was the console output and why?
```
{% endtab %}

{% tab title="Scope 2" %}
```javascript
function telescope() {
  var a = "near";
  let b = "near";
  const c = "near";
  d = "near";
  
  if (true) {
    var a = "far";
    let b = "far";
    const c = "far";
    d = "far";
      
	  console.log(`The (var) a will be ${a}.`);
	  console.log(`The (let) b will be ${b}.`);
	  console.log(`The (const) c will be ${c}.`);
	  console.log(`The (no variable type) d will be ${d}.`);
  }
  
  return "Function executed";
}

telescope();

// Predictions:
// var a = far
// let b = far
// const c = far
// no variable type d = far

// What are our predictions and why?
// What was the console output and why?
```
{% endtab %}

{% tab title="Scope 3" %}
```javascript
function telescope() {
  var a = "near";
  let b = "near";
  const c = "near";
  
  if (true) {
    a = "far";
    b = "far";
    c = "far";
  }
  
	console.log(`The (var) a will be ${a}.`);
	console.log(`The (let) b will be ${b}.`);
	console.log(`The (const) c will be ${c}.`);
  
  return "Function executed";
}

telescope();

// Predictions:
// var a = far
// let b = far
// const c = Type Error: Assignment to constant variable

// What are our predictions and why?
// What was the console output and why?
```
{% endtab %}

{% tab title="Scope 4" %}
```javascript
function telescope() {
  var a = "near";
  const b = "near";
  
  if (true) {
    var a = "far";
    const b = "far";
    var c = "far";
    var d;
  }
  
	console.log(`The (var) a will be ${a}.`);
	console.log(`The (const) b will be ${b}.`);
	console.log(`The (var) c will be ${c}.`);
	console.log(`The (var) d will be ${d}.`);
  
  return "Function executed";
}

telescope();

// Predictions:
// var a = far
// const b = near
// var c = far
// const d = Reference Error: d is not defined

// What are our predictions and why?
// What was the console output and why?
```
{% endtab %}

{% tab title="Lexscope" %}
```javascript
var a = "hello!";  

function mathsTime() { 
  var b = "Welcome to Maths Class."  ;
  
  function problem(x) { 
    var c = "the answer is.." ;
      console.log(a) ;
      console.log(b) ;
      console.log(c) ;
      console.log(answer);
      return timesByTwo(x) ;
  }  
  
  var startWith = 5  ;
  var answer = problem(startWith);
}  

function timesByTwo(num) { 
  return num * 2 ;
}

  mathsTime();
```
{% endtab %}
{% endtabs %}

* Scope 4: `undefined` is different than not defined
* Scope 3: You can't reassign the value a `const`, but you can manipulate the content of a `const`

## Hoisting

* `var` vs. `let` vs. `const` → These all trigger a read
  * Not declaring `status` will not trigger a read

### Error Messages

* Cannot access `status` before initialization \(for let and const variables\)
* If you `console.log` a variable of type `var` that is not defined, an error will not be thrown

{% tabs %}
{% tab title="Hoisting 1" %}
```javascript
function whatAmI() {
  console.log("I am so", status)
  
  var status = "in shape"
  
  let status = "in shape"
  const status = "in shape"
  
  function status() {
    return "in shape"
  }
  
  var status = () => {
    return "in shape"
  }

  status = "in shape"
      
  console.log("I am so", status)
  
  return "Function executed"
}

whatAmI()

// What is logged when we comment out line 4?
// What is logged when we comment line 4 back in?

// Describe what is happening during hoisting (i.e. the two phases).

// What are the differences in our console outputs for each time we run the function?

/* ERROR MESSAGES */
// let, const => 'Cannot access variable before initialization'
// const => 'Missing initializer in const declaration'

```
{% endtab %}

{% tab title="Hoisting 2" %}
```javascript
function whatAmI() {
  console.log("I am so", status)
  
  var status = "in shape"
  
  let status = "in shape"
  const status = "in shape"
  
  function status() {
    return "in shape"
  }
  
  var status = () => {
    return "in shape"
  }

  status = "in shape"
      
  console.log("I am so", status)
  
  return "Function executed"
}

whatAmI()

// What is logged when we comment out line 4?
// What is logged when we comment line 4 back in?

// Describe what is happening during hoisting (i.e. the two phases).

// What are the differences in our console outputs for each time we run the function?

/* ERROR MESSAGES */
// let, const => 'Cannot access variable before initialization'
// const => 'Missing initializer in const declaration'

```
{% endtab %}

{% tab title="Hoisting 3" %}
```

```
{% endtab %}
{% endtabs %}

