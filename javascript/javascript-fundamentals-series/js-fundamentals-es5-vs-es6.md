# JS Fundamentals: ES5 vs ES6

> **Beth Schofield on 04/07/20 & 05/05/20**

See a list of new features added in ECMAScript 6 here: [http://es6-features.org/](http://es6-features.org/)

## Import/Export

### ES5 Syntax

```javascript
var es5Translator = require('./es5exports');
```

### ES6 Syntax

```javascript
import catTranslator from './es6exports'
import { catTranslator, dogTranslator } from './es6exports'
import * from './es6exports'
```

If there's no default exports, we use named exports by inserting curly braces \({}\) around the object name.

You can import/export any data type \(variables, classes, functions, etc.\).

You can't export default a variable inline, only a class or a function. However you can export default a variable at the end of the file.

### index.js

If a folder has an index.js in it, we can add named exports here.

In the import, it implicitly looks for the index.js within the folder. The order in which you write the imports does not matter.



## Array & Object Destructuring



## Async

{% embed url="https://gist.github.com/Gingertonic/3040e6bafb5643fdd0ced1df3dacbe95" %}

## Video

{% embed url="https://www.youtube.com/watch?v=wd4TFxq3kwc" %}



