[Semester:: 3]   •   [Year:: 2]   •   [ECT:: 9]• [Completed:: ✅]
# HTTP and Node.js:

# JavaScript on the Server-side:

## Modularity: Require and Exports

```javascript
var module = require('module'); // Libary module
var my_module = require('./my_module'); // local module
console.log(my_module.f('hello'));
```

Import modules with **require.**

```javascript
var msg = "x:"; // private
var f = function(x) {
	return msg + " " + x;
}
module.exports.f = f; // public
```

Export module functions making them part of **module.exports**

## Yarn

```javascript
yarn init
```

interactively create a new package.json

```javascript
yarn install
```

download and install the dependencies

```javascript
yarn add package
```

download and install the **package** and add it to the dependencies listed in package.json
 
# Server-Side Web Apps and APIs: