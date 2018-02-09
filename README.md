#omelo-loader - loader module for omelo

Load codes for omelo based on the convention over configuration rules.

omelo-rpc could load modules in batch but not load the sub-directory recursively.

+ Tags: node.js

##Regulation
Module name

Module would use the filename by default. For example: load ```lib/a.js``` and the return result would be: ```{a: require('./lib/a')}```

It would use the name if the module with a name property. For example

```javascript
a.js
exports.name = 'test';
```
the return result would be: ```{test: require('./lib/a')}```

Module definiation

If the module exported as a function, omelo-loader would take it as a factory method and generate a new instance of module by calling the function. And it would return the module directly for other situation.

```javascript
module.exports = function(context) {
	return {};	// return some module instance
};
```

##Installation
```
npm install omelo-loader
```

##Usage
``` javascript
let Loader = require('omelo-loader');

let res = Loader.load('.');
console.log('res: %j', res);
```

##API
###Loader.load(path, context)
Load all modules in the path.
####Parameters
+ path loaded path
+ context if the module provides a factory method, the context would be pass as a parameter as the factory method.
