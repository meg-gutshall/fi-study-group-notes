# Fetch API

> **Annabel Wilmerding on 11/19/19**

* Synchronous → the code is in-sync with each other
* Asynchronous → the code is out of sync
  * It runs while other code runs in the background
* A `fetch` request returns a `Promise`
* A `Promise` is a _promise_ of information
  * It takes time to complete a fetch request so this is telling the DOM that there _will_ be information to display once the fetch is done
  * A `Promise` is an `Object`
* Once the `Promise` is resolved, we follow up with `then()`
  * `then()` is also an asynchronous function
  * Always pass a function to `then()` with the argument being the return value of the previous request
  * Will always get a response back from a `Promise`, whether or not it was resolved
    * Unresolved promises can be taken care of with a `catch()`
* If using curly brackets, you need to explicitly return the object, otherwise the return is implicit



