# this with Avi

> **Avi Flombaum on 03/20/20**

* In Ruby, it's hard to change the value of `self`
* In JavaScript, it's easy to change what the value of `this` is going to be in the context of another function

## `call()`, `apply()`, and `bind()`

```javascript
function hello() {
  console.log(this, "From inside");
}

hello();
//=> Window
// LOG: From inside

hello.call("Will this be this?");
//=> String: "Will this be this?"
// LOG: From inside
```

* The default behavior of `this` within a function is that it inherits whatever `this` was outside of the function.
* `apply()` does the same thing as `call()`; it's just a way to splat the arguments.
  * Use `apply()` when you don't know how many arguments you have.

{% hint style="info" %}
In Ruby, the splat operator \(`*`\) placed before an array separates that array into individual arguments.
{% endhint %}

