# Intro to Event Listeners and Manipulating the DOM

> **Alice Balbuena on 01/17/20**

{% embed url="https://github.com/Alicekb/pokedex?ts=4" %}

* Event listeners usually use the syntax of "on" \(`onsubmit`, `onclick`, `onload`, etc.\)
* `e.stopPropagation` prevents an event from bubbling up through their parent\(s\)
* `e.preventDefault` stops the default action from happening
  * Usually used when submitting a form
  * Can also be used form customization purposes when working with a framework or a library
* `e.target` means "whatever triggered this event, I want to have access to it"
* Bubbling is another term for event propagation
  * Bubbles always go up
* `window` refers to everything on the screen \(HTML, CSS, and JS\)
* `document` refers to just the HTML

## Video Recording

{% embed url="https://www.youtube.com/watch?v=5sE1Bz0JFW0" caption="" %}

## Resources

* [Event Reference \(MDN\)](https://developer.mozilla.org/en-US/docs/Web/Events)

