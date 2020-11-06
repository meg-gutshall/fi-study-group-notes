# Intro to Object-Oriented JavaScript

> **Annabel Wilmerding on 11/14/19**

* Object orientation allows you to DRY up code via inheritance

## **`this`**

* When using arrow function syntax, the value of `this` is the scope of the function
* When using standard \(non-arrow\) function syntax, the value of `this` is the object the function is being called on‌

## **Prototypes**

* All JavaScript objects inherit properties and methods from a prototype
  * The `Object.prototype` is on the top of the prototype inheritance chain
  * All other objects inherit from `Object.prototype`
* The JavaScript `prototype` property allows you to add new properties and methods to object constructors

## **Factory Method**

* Create a function that returns an object of key/value pairs
  * These can contain functions
  * Can set variables outside of the return object to be used in the return functions

## **Constructor Function**

* Invoke using the `new` keyword
* Be sure to declare a variable to save the new object

## **Classes**

* Use the keyword `class` with the constructor method

{% tabs %}
{% tab title="ES5 Syntax" %}
```javascript
// Method A

function Person(attributes) {
  this.name = attributes.name;
  this.age = attributes.age;
}

Person.prototype.introduceSelf = function() {
  console.log(`Hello, me name is ${this.name}.`);
};

let meg = new Person({name: "Meg", age: 29});


// Method B

function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.introduceSelf = function() {
  console.log(`Hello, me name is ${this.name}.`);
};

let meg = new Person("Meg", 29);

// Method A is safer than Method B because the order
// in which the arguments are passed in to the function
// doesn't matter since they're key/value pairs.

```
{% endtab %}

{% tab title="ES6 Syntax" %}
```javascript
class Rectangle {
  constructor(width, length) {
    this.width = width;
    this.length = length;
  }
  
  // Instance methods
  checkForSquare() {
    if (this.width === this.length) {
      console.log("I am a square!");
    } else {
      console.log("I am not a square!");
    }
  }
  
  sayHi() {
    console.log("Hi!");
  }
  
  // Class methods
  static createSquare(side) {
    return new Rectangle(side, side);
  }
}


// Invoke instance methods
let myRec = new Rectangle(4, 5);
//=> undefined
myRec;
//=> Rectangle { width: 4, length: 5 }
myRec.sayHi();
//=> LOG: Hi!
//=> undefined
myRec.checkForSquare();
//=> LOG: I am not a square!
//=> undefined

// Invoke class method
let mySq = Rectangle.createSquare(3);
//=> undefined
// Invoke instance methods
mySq;
//=> Rectangle { width: 3, length: 3 }
mySq.sayHi();
//=> LOG: Hi!
//=> undefined
mySq.checkForSquare();
//=> LOG: I am a square!
//=> undefined
```
{% endtab %}
{% endtabs %}

> **Ayana Zaire Cotton on 02/27/20**

## **Woof Woof OOJS App**

{% embed url="https://github.com/AyanaZaire/woof-woof-oojs" %}

* `index.js` is no longer attached to the app, it's just a reference for Vanilla JS functionality
* This app uses a `static` method to get each `dog` instead of a `fetch` request
* `static` methods are useful ways to create utility methods for your data
  * A utility method does some sort of labor/logic for you by encapsulating a function that is used often throughout the code

### CodeSandbox

{% embed url="https://codesandbox.io/s/woof-woof-oojs-gxwbt" %}

