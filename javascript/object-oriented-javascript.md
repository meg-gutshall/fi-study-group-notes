# Object-Oriented JavaScript

> **Howard DeVennish on 12/19/19**

* Use an IIFE \(immediately invoked function expression\) to cut down on global variables

## **Prototypal Inheritance**

* Instead of making a whole new copy of that holds the characteristics of a parent \(like in class-based inheritance\), the new copy references something else to describe its own functionality

```javascript
let allThePeople = [];

class Person {
  constructor(attrs) {
    this.name = attrs.name;
    this.age = attrs.age;
    this.save();
  }
  
  introduceSelf() {
    console.log(
      `Hello, my name is ${this.name} and I'm ${this.age} years old!`
    );
  }
  
  save() {
    allThePeople.push(this);
  }
  
  static all() {
    return allThePeople;
  }
}

const chris = new Person({
  name: "Chris",
  age: 22
});
```

## **Variable Assignment**

* Pass by value is all primitive data types
* Pass by reference is all complex data types \(objects, arrays, null, functions\)

## **Model Class**

* Break out JavaScript code pertaining to a singular model in a separate JavaScript file
* In the HTML index head, add model/class JavaScript files first, then controller JavaScript files, then index JavaScript files so code will load in the correct order

## Video

{% embed url="https://www.youtube.com/watch?v=QIZyQHmqlb8&feature=emb\_title" %}

> **Alice Balbuena on 01/29/20**

## **Pass By Reference vs. Pass By Value Memory**

* Complex data types pass the reference from where they are in the memory versus primitive data types which pass the actual value
* Prototypal inheritance uses pass by reference memory
* Pass by reference memory can lead to side effects in JavaScript
  * Avoid this by cloning the object to a new variable
* Avoid side effects with primitive data types by assigning arguments to new variables before manipulating them inside functions

## **Pure vs. Impure Functions**

* Pure functions → Predictable result for every time you run it
* Impure functions → Can't reliably predict the return of the function
  * Anytime you need to talk to a database, it's always an impure function \(since you can't predict the specific data you'll get back\)
* Run into these a lot in Redux
* The difference between the two is the predictability of the output

> **Alice Balbuena on 02/07/20**

* `null` is usually a good filler for variables that you don't want to have a value yet

## **Boolean Values**

* `!!` is just a shortcut for `Boolean()`
  * `!!` **always** returns the boolean value of the object that follows
* `null` and `false` evaluate to `false`
* `undefined`, `0`, and almost everything else evaluate to `true`

## **The Ternary Operator**

* The ternary operator functions slightly differently in JavaScript than in Ruby

### Boilerplate Example

```javascript
conditional expression ? expression when conditional evaluates to true : expression when conditional evaluates to false;
```

* You can construct a ternary like: `conditional expression ? true : false`, but in this case, using `!!(conditional expression)` is drier
* Any of the expressions can be encapsulated in parentheses as needed
* If you want to create a conditional that only takes action if it is truthy, set the third expression \(to the right of the colon\) to `null`
  * Set the second expression \(to the left of the colon and right of the question mark\) to `null` if you want to create a conditional that only takes action if it is falsy
* You can also write it like: `if (conditional expression) { expression when conditional evaluates to true }`
  * The curly brackets aren't necessary if it's a one-liner; plus then it will be an implicit return
* You **cannot** write: `{ expression when conditional evaluates to true } if (conditional expression)` like in Ruby
  * JavaScript will execute the first half of this statement before reading the second half so the condition will not hold true

> **Ayana Zaire Cotton on 02/13/20**

## **Woof Woof OOJS App**

> _Get notes from Intro to Object-Oriented JavaScript file and add here_

* The back-end is the `db.json` file
* `static` methods are class-level methods
  * Can only be called on the class itself, not instances of the class
* Class instances are stored in the class file \(i.e. `Dog` is stored in `allDogs`\)
  * The only thing that accesses the database is a `fetch`
* `fetch` the individual `dog` info from the database and provide it as an argument to instantiate a new instance of the `Dog` class
* Use a serializer for model associations
  * [ActiveModel::Serializer](https://github.com/rails-api/active_model_serializers)
  * [Fast JSON:API](https://github.com/fast-jsonapi/fast_jsonapi)
  * [Active Model Serializer vs Fast JSON API Serializer](https://medium.com/@raj.b.stretz/active-model-serializer-vs-fast-json-api-serializer-8338b939f01f)

