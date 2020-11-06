# JS Fundamentals: Binding & Closures

> **Beth Schofield on 04/15/20 & 05/12/20**

## Binding

In which context was the function invoked? That is how we will know what `this` is.

### Implicit Binding

Let it figure out its own context.

```javascript
const thisCat = {
  name: "Zelda",
  age: 2,
  coloring: "calico",
  sayMiau: function() {
    console.log(`Miau! I'm ${this.name} and I am a ${this.coloring} kitty!`)
  }
}
```

```javascript
const thatCat = {
  name: "Princess Tigerlilly",
  age: 7,
  coloring: "ginger",
  sayMiau: () => console.log(`Miau! I'm ${this.name} and I am a ${this.coloring} kitty!`)
  owner: {
    name: "Beti",
    sayHi: function() { console.log(`Hi! I'm ${this.name} and I love my kitty!`) }
  }
}
```

### Explicit Binding

Give it the context yourself.

#### `.call()` Method

**How do we...** call `thisCat.sayMiau` and get back Ziggy's data?

{% tabs %}
{% tab title="Ziggy Says Miau" %}
```javascript
const thisCat = {
  name: "Zelda",
  age: 2,
  coloring: "calico",
  sayMiau: function() {
    console.log(`Miau! I'm ${this.name} and I am a ${this.coloring} kitty!`)
  }
}

const ziggy = {
  name: "Ziggy",
  age: 1,
  coloring: "grey"
}

thisCat.sayMiau.call(ziggy);
// LOG: Miau! I'm Ziggy and I am a grey kitty!
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="What Sam Ate" %}
```javascript
function todayIAte(breakfast, lunch, dinner) {
  console.log(`I'm ${this.name} and today I ate ${breakfast}, ${lunch}, and ${dinner}!`)
}

const sam = {
  name: "Sam",
  age: 12,
  coloring: "black"
}

const whatSamAte = ["kibble", "tuna", "more kibble"];
const [b, l, d] = whatSamAte;

todayIAte.call(sam, b, l, d);
// LOG: I'm Sam and today I ate kibble, tuna, and more kibble!
```
{% endtab %}
{% endtabs %}

#### `.apply` Method

### `new` Binding

Give it context upon construction.

{% tabs %}
{% tab title="Dog Factory" %}
```javascript
const Dog = function(name, age, coloring) {
  this.name = name;
  this.age = age;
  this.coloring = coloring;
  this.sayWoof = function() { console.log(`Woof! I'm ${this.name}!` };
  this.sayAge = () => console.log(`This dog is ${this.age} years young!`);
}
```
{% endtab %}
{% endtabs %}

### Arrow Functions

Only take context from the parent scope.

{% tabs %}
{% tab title="Bird Class" %}
```javascript
class Bird {
  constructor(name, age, coloring) {
    this.name = name;
    this.age = age;
    this.coloring = coloring;
  }
  
  sayChirp() {
    console.log(`Chirrup! I'm ${this.name}!`);
  }
  
  sayAge = () => console.log(`This bird is ${this.age} years young!`);
}
```
{% endtab %}
{% endtabs %}

### `window`

Try this is in the browser console.

## Closures

"The combination of a function bundled together with references to its surrounding state."

"A closure is the combination of a function and the lexical environment in which \[it\] was declared."

* Lexical scoping is scope chaining so the lexical environment is a level of the scope chain

```javascript
function stuffAndNonsense() {
  const stuff = "This stuff";
  
  function nonsense() {
    console.log(`${stuff} is great.`)
  }
  
  return nonsense
}

function doSomethingElse() {
  console.log(`${stuff} is great.`)
}

const stuff = "That stuff";
const doSomething = stuffAndNonsense();

console.log(doSomething)
// f nonsense
doSomething();
// LOG: This stuff is great.
doSomethingElse();
// LOG: That stuff is great.
```

Any change with an arrow?

```javascript
const nonsenseAndStuff = () => {
  const nonsense = "This nonsense";
  
  const stuff = () => console.log(`${nonsense} is atrocious!`);
  
  return stuff
}

const stuff = "That nonsense";
const doThis = nonsenseAndStuff();

doThis()
// LOG: This nonsense is atrocious.
```

Something a bit fancier

```javascript
// A multiplier factory
const matilda = multiplier => num => multiplier * num;

function matildaDec(multiplier) {
  return function(num) {
    return multiplier * num;
  }
}

const timesBySeven = matilda(7);
const timesByFourteen = matilda(14);
const timesBySixHundredAndFour = matilda(604);

// console.log(timesBySeven(3));
// console.log(timesBySixHundredAndFour(3));
```

Something **well** fancy!

```javascript
const theFunctionCombinator = (funcName1, funcName2) => {
  return arg => {
    const stepOneResult = arg[funcName1]();
    const stepTwoResult = stepOneResult[funcName2]();
    return stepTwoResult;
  }
}

const flipItAndReverseIt = theFunctionCombinator("reverse", "toString");
const result = flipItAndReverseIt(["!", "load", "over", "Comma"]);
console.log(result);
// LOG: Comma,over,load,!
```

### Lexical Environment

{% hint style="warning" %}
**Still need to read the articles below**
{% endhint %}

{% embed url="https://medium.com/@5066aman/lexical-environment-the-hidden-part-to-understand-closures-71d60efac0e0" %}

{% embed url="https://hackernoon.com/javascript-execution-context-and-lexical-environment-explained-528351703922" %}

{% embed url="https://dev.to/shoupn/javascript-code-nesting-and-lexical-environments-explained-3bi4" %}



