# JavaScript Debugging Deep Dive

> **Alice Balbuena on 04/08/20**

How to Debug post: [https://blog.regehr.org/archives/199](https://blog.regehr.org/archives/199)

## **Debugging Steps**

* **Verify the bug and determine the correct behavior**
  * Bug: Robot is catching on fire after two hours of use
  * Correct: Robot should not be on fire
* **Stabilize, isolate, and minimize**
  * Can we make the bug trigger faster? \(We don't want to wait two hours for the robot to catch on fire.\)
  * Can I determine what
* **Construct a hypothesis based on assumptions of code**
  * Has there been anything else recently added/changed in our code?
  * Is this part of our code relying on any other code? The bug may actually be in that _other_ code instead.
* **Devise and run an experiment**
  * One simple way
* **Iterate until the bug is found**
  * Repeat steps 3–4
* **Fix the bug and verify the fix**
  * Write/change the code to fix the bug \(I found an infinite loop caused by changes I made\).
  * Ensure nothing else is broken.
* **Undo changes**
  * ...
* **Write tests**
  * ...
* **Find the bug's friends and relatives \(optional but can be important\)**
  * What error in thinking led to the bug?
    * I assumed the code would exit correctly.
  * This might have caused other bugs that haven't shown up yet.

## Debugger Tools

* Recommend Firefox over Chrome for browser tools

### Performance

* Runs tests against everything on your page and will show what is slowing it down

### Elements

* Shows the HTML document as well as:
  * CSS styles applied to the component selected in the HTML document.
    * Will even show styles that are crossed out because they've been overridden by specificity rules
  * Event listeners
  * Accessibility and how the page will be read by a screen reader
* Can right click on an element and select 'Store as global element'

### Console

* Best to `console.log()` values as objects so you have labels for each value
  * If dealing with an array, use `console.table()` instead of `console.log()`
* Can add inline CSS to a `console.log()`
  * See screenshot
* Use `console.trace()` to show a stack trace of where the function was called from
* Use `$` to quickly query from the DOM
  * Example: $\(\#header\)
* Can call `console.dir()` on a variable to show that variable's JavaScript code

### Sources

* Find the navigator on the left hand side to see the files being applied the that web page
  * Add snippets under the navigator in sources and then run them in the console by pressing `Cmd` + `p` followed by `!` and the name of your snippet file
* `debugger` isn't triggered unless the devtools are open
* You have the option to deactivate breakpoints

