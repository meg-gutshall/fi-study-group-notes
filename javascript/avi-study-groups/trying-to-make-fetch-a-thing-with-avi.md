# Trying to Make Fetch a Thing with Avi

> **Avi Flombaum on 02/27/20**

* 15 years ago the web sucked
  * Mainly due to AJAX and Flash
* `setTimeout` creates a new `Promise`
* The word `await` tells JavaScript "this is synchronous code"
* `async`/`await` is the new paradigm
  * Much preferred over `.then()` syntax

{% tabs %}
{% tab title="Asynchronous IIFE" %}
```javascript
(async function() {
  // await (Promise)
})();
```
{% endtab %}
{% endtabs %}

