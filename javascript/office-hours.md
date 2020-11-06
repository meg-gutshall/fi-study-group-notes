# JavaScript Office Hours

* Search different projects on GitHub to see how you want to build your project
* Good idea to mirror the models between Rails and JS

## **Debugging**

* Debugger & breakpoints → Pauses execution of JS code as it's run and will evaluate the lines with return values

## **Event Listeners**

* Anytime you have an event listener, if you provide a reference to an existing function, JavaScript will automatically pass that event on to that existing function
  * This is where the event argument comes in
  * Event handlers are the function that the event gets passed to
* [Introduction to Events \(MDN\)](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events)
* [GlobalEventHandlers \(MDN\)](https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers)

{% tabs %}
{% tab title="implicitEventListener" %}
```javascript
let costumeForm = document.createElement("form");

costumeForm.addEventListener("submit", handleSubmit);
function handleSubmit(event) {
  // Event handler code here
}
```
{% endtab %}

{% tab title="explicitEventListener" %}
```javascript
let costumeForm = document.createElement("form");

costumeForm.addEventListener("submit", (event) => handleSubmit(event, id));
function handleSubmit(event, id) {
  // Event handler code here
}
```
{% endtab %}
{% endtabs %}

## **Making an API Request**

* `fetch()` is actually an API, not a method
  * Use it to get objects `fetch(URL)`
* The `finally()` method returns a `Promise`
  * When the `Promise` is settled, i.e either fulfilled or rejected, the specified callback function is executed
  * This provides a way for code to be run whether the `Promise` was fulfilled successfully or rejected once the `Promise` has been dealt with
* [Using Fetch \(MDN\)](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

{% tabs %}
{% tab title="fetch" %}
```javascript
function getCostumes() {
  fetch(URL)
    .then(resp => resp.json())
    .then(costumes => console.log(costumes));
}
```
{% endtab %}
{% endtabs %}

## **Asynchronous Code**

* Lets multiple actions happen at once
  * Example: If you put a pot of water on the stove, you down have to stand there and wait for it to boil. You can chop up ingredients and do other things in the meantime until it's ready.
* Use asynchronous functions when the order of the information matters
  * If something needs to finish loading before it can be passed to another function
  * Use `async/await` syntax

## **Data Interpolation**

* `object.innerHTML +=` adds following content to the object's HTML
* `object.innerHTML =` replaces the object's HTML with the following content

## **JavaScript Primitives**

* A primitive is an irreducible data type
  * It has no class or properties and it can't be broken down into smaller bits
  * It's like an atom; a building block of programming
* JavaScript has six primitive data types plus objects
* JavaScript uses prototype inheritance as opposed to Ruby's class inheritance

## **Functions**

* Functions are objects
  * This means they can be saved into variables
* In a function declaration, the function keyword begins the line of code \(this **must** be present\), followed by the function's name, a set of parentheses containing zero or more parameters, and then curly brackets containing the function body
  * Some features of functions created as function declarations:
    * They are hoisted
    * They are scoped globally if declared globally and otherwise function-scoped

{% tabs %}
{% tab title="functionDeclaration" %}
```javascript
function greetDeclaration(greeting = "hello", name = "anonymous life form") {
  console.log(`${greeting} there ${name}`);
}
greetDeclaration();
//=> LOG: hello there anonymous life form
//=> undefined
```
{% endtab %}
{% endtabs %}

* A function expression is any function that is defined, but not as a function declaration
  * Most often these function expressions are anonymous \(unnamed\)
* Arrow functions give an implicit return if the function body isn't encased in curly brackets
  * If an arrow function returns an object, it needs to wrapped in curly braces and explicitly returned
  * They also allow you to pass in references to higher-order functions as arguments \(without initializing\)

{% tabs %}
{% tab title="IIFE" %}
```javascript
// IFEE - Immediately Invoked Function Expression
let yay = (function greetExpression(
  greeting = "hello", 
  name = "anonymous life form"
) {
  console.log(`${greeting} there ${name}`);
  return "YEAAAY";
})();
//=> undefined
yay;
//=> LOG: hello there anonymous life form
//=> undefined
```
{% endtab %}

{% tab title="constExpression" %}
```javascript
const constGreet = function greetExpression(
  greeting = "hello",
  name = "anonymous life form"
) {
  console.log(`${greeting} there ${name}`);
};
//=> undefined
constGreet();
//=> LOG: hello there anonymous life form
//=> undefined
```
{% endtab %}

{% tab title="letExpression" %}
```javascript
let letGreet = function greetExpression(
  greeting = "hello",
  name = "anonymous life form"
) {
  console.log(`${greeting} there ${name}`);
};
//=> undefined
letGreet();
//=> LOG: hello there anonymous life form
//=> undefined
```
{% endtab %}

{% tab title="arrowFunction" %}
```javascript
const arrowGreet = (greeting, name) => `${greeting} there ${name}`;
//=> undefined
```
{% endtab %}
{% endtabs %}

```javascript
const Baby = (function() {
  let allBabies = [];
  // Effectively private space that the class can see
  
  return class {
    constructor(attrs) {
      this.name = attrs.name;
      this.ageInMonths = attrs.ageInMonths;
      allBabies.push(this);
    }
    
    static get all() {
      return allBabies;
    }
  };
})();
//=> undefined
```

## **Running JavaScript Code**

* Compilation \(or creation\) phase looks for variable and function declarations
* Execution phase runs the code

## **Testing Frameworks**

* Kent C. Dodds
* Mocha
* Jest
* Jasmine

## **CRUD**

* When editing, you destroy the current HTML element and replace it with the newly created object
  * [https://repl.it/@AliceBalbuena/PrudentOpaqueListener](https://repl.it/@AliceBalbuena/PrudentOpaqueListener) \(below\)

```javascript
// NOTE: The code below is buggy.

// During this study group we were recreating the Dog CEO Fetch lab using
// object-oriented JavaScript and adding a form that searched the dog
// database by name.

class Dog(){
  this.dogs = []
  constructor({name: "wall-e"}){
    this.id = this.dogs.length + 1;
    this.name = name;
  }
}

Dog.prototype.displayName() {
  return `<p data-id="${dog.id}"> ${dog.name} </p>`;
}

const dog = new Dog();
Dog.dogs.push(dog);
const dogHtml = dog.displayName();


document.getElementById('dogDiv').innerHtml = dogHtml;

//-------------------------------------------------------------

const dogId = document.getElementsByTagName('p')[0].dataset.id;
const dogAgain = Dog.dogs.find(dog => dog.id == dogId);

dogAgain.name = "Fido";
const dogHtml = dogAgain.displayName();


document.getElementById('dogDiv').innerHtml = dogHtml;
```

## **HTML `script` Tag**

* `script` tags are loaded top down in the `index.html` file, meaning they execute from the bottom up
* The `defer` keyword in an HTML `script` tag means wait until the DOM has loaded to fire off the JavaScript file

## **`bind()`, `call()`, and `apply()`**

* These functions run code in a different context
* `bind(fn)` gives you access to the function
* `call(fn)` and `apply(fn)` run the function for you
  * `call()` requires the function's arguments to be listed explicitly
  * `apply()` lets the function's arguments be listed as an array
  * [What is the difference between call and apply? \(Stackoverflow\)](https://stackoverflow.com/questions/1986896/what-is-the-difference-between-call-and-apply/1986909#1986909)

## **Prototypes**

* `[[Prototype]]` is the same as `__proto__`
  * `__proto__` is a JavaScript class setter and getter

> **Howard DeVennish on 12/17/19**

```javascript
myGreet = greet;
// f greet(greeting="hello", name="anonymous life form") {
//  console.log(`${greeting} there ${name}`);
// }
myGreet === greet;
//=> true
myGreet;
// f greet(greeting="hello", name="anonymous life form") {
//  console.log(`${greeting} there ${name}`);
// }
myGreet();
//=> LOG: hello there anonymous life form
//=> undefined
myGreet("Howdy", "Frank", 4, {}, [1, 2, 3, 4], greet);
//=> LOG: Howdy there Frank
//=> undefined
```

## JWT \(JSON Web Tokens\)

* JSON objects we create on the backend that are encrypted
  * Similar to salting and hashing a password
  * Then your frontend decrypts those JSON objects
* In the real world, it's best to use both cookies and JWT
* As opposed to using Rails sessions --&gt; they have to also be stored in the frontend to process fetch requests and can be easily hacked
* JSON is a language that's agnostic for both Ruby and JavaScript so it works well for Rails API backends with JavaScript frontends

## Import/Export

* A way to only use certain code when you need it
* Separation of concerns, modularization

## `Element.insertAdjacentHTML()`

This method of the [`Element`](https://developer.mozilla.org/en-US/docs/Web/API/Element) interface parses the specified text as HTML or XML and inserts the resulting nodes into the DOM tree at a specified position. It does not reparse the element it is being used on, and thus it does not corrupt the existing elements inside that element. This avoids the extra step of serialization, making it much faster than direct [`innerHTML`](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML) manipulation.

### Syntax

```javascript
element.insertAdjacentHTML(position, text);
```

### Parameters

#### `position`

A [`DOMString`](https://developer.mozilla.org/en-US/docs/Web/API/DOMString) representing the position relative to the `element`; must be one of the following strings:

* `'beforebegin'`: Before the `element` itself.
* `'afterbegin'`: Just inside the `element`, before its first child.
* `'beforeend'`: Just inside the `element`, after its last child.
* `'afterend'`: After the `element` itself.

#### `text`

The string to be parsed as HTML or XML and inserted into the tree.

### Visualization of Position names

```markup
<!-- beforebegin -->
<p>
  <!-- afterbegin -->
  text
  <!-- beforeend -->
</p>
<!-- afterend -->
```

{% hint style="info" %}
**NOTE:** The `beforebegin` and `afterend` positions work only if the node is in the DOM tree and has a parent element.
{% endhint %}

