# JS Fundamentals: Iteration

> **Beth Schofield on 04/21/20**

{% code title="objectExamples.js" %}
```javascript
const myArray = ["chickpeas", "kidney beans", "tea cups"];
const myNums = [4.99, 5.45, 2, 7.99];

const myObject = { 
  favorite: "hummus",
  leastFavorite: "marmite",
  tolerable: "carrots"
};
const shoppingList = { bananas: 2.50, chickpeas: 0.80, wine: 8.99, antibac: 25 };
```
{% endcode %}

## `for ... of`

{% hint style="warning" %}
Use this method with arrays only.
{% endhint %}

```javascript
for (const el of myArray) {
  console.log(el);
}
// LOG: chickpeas
// LOG: kidney beans
// LOG: tea cups

for (const num of myNums) {
  console.log(num);
}
// LOG: 4.99
// LOG: 5.45
// LOG: 2
// LOG: 7.99
```

## `for ... in`

{% hint style="warning" %}
Use this method with objects only. If called with an array, it will return the indices.
{% endhint %}

```javascript
for (const key in myObject) {
  console.log(key);
}
// LOG: favorite
// LOG: leastFavorite
// LOG: tolerable

for (const item in shoppingList) {
  console.log(`${item} -- ${shoppingList[item]}`);
}
// LOG: bananas -- 2.5
// LOG: chickpeas -- 0.8
// LOG: wine -- 8.99
// LOG: antibac -- 25
```

## `forEach()`

{% hint style="warning" %}
Use this method on arrays only. Receives a callback function as an argument.
{% endhint %}

{% tabs %}
{% tab title="Study Group Example 1" %}
```javascript
const printIt = item => console.log(`I love ${item}!`);

myArray.forEach(printIt);
myArray.forEach(item => printIt(item));
// Both log the same thing:
// LOG: I love chickpeas!
// LOG: I love kidney beans!
// LOG: I love tea cups!

myArray.forEach(item => console.log(`Saved ${item}!`))
// LOG: Saved chickpeas!
// LOG: Saved kidney beans!
// LOG: Saved tea cups!

myArray.forEach(function(item) {
  console.log(`These are ${item}.`);
});
// LOG: These are chickpeas.
// LOG: These are kidney beans.
// LOG: These are tea cups.
```
{% endtab %}

{% tab title="Study Group Example 2" %}
```javascript
function addArrayElementsToDOMWithForEach() {
  array.forEach((word, index) => {
    const p = `<p>${index + 1}. ${word}</p>`;
    contentDiv.insertAdjacentHTML('beforeend', p);
  });
}
```
{% endtab %}

{% tab title="Native Example" %}
```javascript
Array.prototype.myEach = function(callback) {
  for (var i = 0; i < this.length; i++)
    callback(this[i], i, this);
};

const arr = ["apple", "orange", "banana", "peach"];

arr.myEach(function(word) {
  console.log(word);
});
// LOG: apple
// LOG: orange
// LOG: banana
// LOG: peach
```
{% endtab %}
{% endtabs %}

### Using `Object.entries()`

```javascript
const entries = Object.entries(myObject);

for (const [k, v] of entries) {
  console.log(`The key is ${k}, the value is ${v}.`);
}
// LOG: The key is favorite, the value is hummus.
// LOG: The key is leastFavorite, the value is marmite.
// LOG: The key is tolerable, the value is carrots.
```

### Using `forEach()` with objects

* Need to first convert the object to an array by passing it to `Object.entries()`
* This gives back an array of arrays
  * The return value is one big array and each key/value pair is a nested array

## `every()`, `some()`

{% hint style="info" %}
Returns `true` or `false`.
{% endhint %}

{% tabs %}
{% tab title="Study Group Every Examples" %}
```javascript
const cees = myArray.every(item => item.startsWith("c"));
console.log(cees);
// false

const ess = myArray.every(item => item.endsWith("s"));
console.log(ess);
// true
```
{% endtab %}

{% tab title="Native Every Examples" %}
```javascript
Array.prototype.myEvery = function(callback, context) {
  for (var i = 0; i < this.length; i++) {
    if (!callback.call(context, this[i], i, this))
      return false;
    }
    return true;
};

const nums = [12, 54, 18, 130, 144];

const greaterThanX = nums.myEvery(num => num > 10);
console.log(greaterThanX);
// LOG: true

const greaterThanXIII = nums.myEvery(num => num > 13);
console.log(greaterThanXIII);
// LOG: false
```
{% endtab %}

{% tab title="Study Group Some Examples" %}
```javascript
const cees = myArray.some(item => item.startsWith("c"));
console.log(cees);
// true

const ess = myArray.some(item => item.endsWith("s"));
console.log(ess);
// true
```
{% endtab %}

{% tab title="Native Some Examples" %}
```javascript
Array.prototype.mySome = function(callback, context) {
  for (var i = 0; i < this.length; i++) {
    if (callback.call(context, this[i], i, this))
      return true;
  }
  return false;
};

const nums = [12, 5, 8, 130, 144];

const greaterThanCC = nums.mySome(num => num > 200);
console.log(greaterThanCC);
// LOG: false

const greaterThanC = nums.mySome(num => num > 100);
console.log(greaterThanC);
// LOG: true
```
{% endtab %}
{% endtabs %}

## `map()`

{% tabs %}
{% tab title="Study Group Example 1" %}
```javascript
const excited = myArray.map(item => `Yay! ${item}!`);
console.log(excited);
console.log(myArray);
// LOG: ["Yay! chickpeas!", "Yay! kidney beans!", "Yay! tea cups!"]
// LOG: ["chickpeas", "kidney beans", "tea cups"]
```
{% endtab %}

{% tab title="Study Group Example 2" %}
```javascript
const excited = myArray.map(item => console.log(`Yay! ${item}!`));
console.log(excited);
console.log(myArray);
// LOG: Yay! chickpeas!
// LOG: Yay! kidney beans!
// LOG: Yay! tea cups!
// LOG: [undefined, undefined, undefined]
// LOG: ["chickpeas", "kidney beans", "tea cups"]
```
{% endtab %}

{% tab title="Native Examples" %}
```javascript
Array.prototype.myMap = function(callback) {
  const array = [];
  for (var i = 0; i < this.length; i++)
    array.push(callback(this[i], i, this));
  return array;
};

const stooges = ["Larry", "Curly", "Moe"];
const squares = [1, 4, 9];

const nothinFunc = stooges.myMap(stooge => stooge);
console.log(nothinFunc);
// LOG: ["Larry", "Curly", "Moe"]

const squareRoot = squares.myMap(num => Math.sqrt(num));
console.log(squareRoot);
// LOG: [1, 2, 3]
```
{% endtab %}
{% endtabs %}

Notice how in example 1, we're simply using string interpolation to change the value of our array element? Whereas, in example 2, we're using `console.log()` to output the new string and therefore changing the element's value to `undefined`.

## `filter()`

{% hint style="info" %}
Returns a new array containing only the elements of the original array that meet our `filter` method criteria.
{% endhint %}

{% tabs %}
{% tab title="Study Group Example 1" %}
```javascript
const cees = myArray.filter(item => item.startsWith("c"));
console.log(cees);
// LOG: ["chickpeas"]

const ess = myArray.filter(item => item.endsWith("s"));
console.log(ess);
// LOG: ["chickpeas", "kidney beans", "tea cups"]
```
{% endtab %}

{% tab title="Study Group Example 2" %}
```javascript
function addArrayElementsToDOMWithFilter() {
  const newArray = array.filter(word => word.includes("l"));
  addArrayElementsToDOMWithForEach(newArray);
}

function addArrayElementsToDOMWithForEach() {
  array.forEach((word, index) => {
    const p = `<p>${index + 1}. ${word}</p>`;
    contentDiv.insertAdjacentHTML('beforeend', p);
  });
}
```
{% endtab %}

{% tab title="Native Example" %}
```javascript
Array.prototype.myFilter = function(callback, context) {
  const array = [];
  for (var i = 0; i < this.length; i++) {
    if (callback.call(context, this[i], i, this))
      array.push(this[i]);
  }
  return array;
};

const nums = [1, 20, 30, 80, 2, 9, 3];

const greaterThanTen = nums.myFilter(num => num >= 10);
console.log(greaterThanTen);
// LOG: [20, 30, 80]
```
{% endtab %}
{% endtabs %}

## `reduce`\(\)

{% tabs %}
{% tab title="Native Examples" %}
```javascript
Array.prototype.myReduce = function(callback, initialVal) {
  const accumulator = (initialVal === undefined) ? undefined : initialVal;
  for (var i = 0; i < this.length; i++) {
    if (accumulator !== undefined)
      accumulator = callback.call(undefined, accumulator, this[i], i, this);
    else
      accumulator = this[i];
  }
  return accumulator;
};

const nums = [20, 20, 2, 3];

const total = nums.myReduce((a, b) => a + b, 10);
console.log(total);
// LOG: 55

// Reduce a nested array
const nested = [
  [0, 1],
  [2, 3],
  [4, 5]
];

const flattened = nested.myReduce((a, b) => a.concat(b));
console.log(flattened);
// LOG: [0, 1, 2, 3, 4, 5]
```
{% endtab %}
{% endtabs %}

> **Howard DeVennish on 05/19/20**

## `for` Loop

{% tabs %}
{% tab title="Study Group Example" %}
```javascript
function addArrayElementsToDOMWithFor() {
  for (let i = 0; i < array.length; i++) {
    const p = `<p>${array[i]}</p>`;
    contentDiv.insertAdjacentHTML('beforeend', p);
  }
}
```
{% endtab %}
{% endtabs %}

> Arrays are fancy objects. Functions are also fancy objects. —Howard DeVennish

## `Object.keys()`

```javascript
meg = {
  name: "Meg",
  age: 29,
  hometown: "Philly"
};

other = {};
```

