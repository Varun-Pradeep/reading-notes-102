# JavaScript

## Overview

JavaScript is a language that runs primarily in the browser, but can be run locally with Node. JavaScript is an **interpreted language**, as opposed to being compiled. This means that the raw machine code isn't available ahead of time, but is "compiled" by the browser on the spot. This makes JavaScript slower, but more versatile. It gets crazy enough that there's a function to write JavaScript *inside* JavaScript using the `eval()` function. JavaScript is dynamically typed, which means variables can contain anything, and has prototypal inheritance. That means that objects in JavaScript can have multiple ancestors to inherit methods and constants from. Aside from primitive data types like numbers, **everything** in JavaScript is an object.

## Objects

JavaScript objects are like a house. If you know where to look, you gain access to everything inside the house. JavaScript objects have methods associated with them, which allow you to do cool things. For example, consider the following code that prints "Hello, World!".

```js
console.log("Hello, World!");
```

The "house" in this example is `console`. It provides a ton of useful methods to interact with the JavaScript console. Now, consider the actual code needed to print something:

```js
// Copyright Joyent, Inc. and other Node contributors.
//
// Permission is hereby granted, free of charge, to any person obtaining a
// copy of this software and associated documentation files (the
// "Software"), to deal in the Software without restriction, including
// without limitation the rights to use, copy, modify, merge, publish,
// distribute, sublicense, and/or sell copies of the Software, and to permit
// persons to whom the Software is furnished to do so, subject to the
// following conditions:
//
// The above copyright notice and this permission notice shall be included
// in all copies or substantial portions of the Software.
//
// THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS
// OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
// MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN
// NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM,
// DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR
// OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE
// USE OR OTHER DEALINGS IN THE SOFTWARE.

'use strict';

var util = require('util');

function Console(stdout, stderr) {
  if (!(this instanceof Console)) {
    return new Console(stdout, stderr);
  }
  if (!stdout || !util.isFunction(stdout.write)) {
    throw new TypeError('Console expects a writable stream instance');
  }
  if (!stderr) {
    stderr = stdout;
  }
  var prop = {
    writable: true,
    enumerable: false,
    configurable: true
  };
  prop.value = stdout;
  Object.defineProperty(this, '_stdout', prop);
  prop.value = stderr;
  Object.defineProperty(this, '_stderr', prop);
  prop.value = Object.create(null);
  Object.defineProperty(this, '_times', prop);

  // bind the prototype functions to this Console instance
  var keys = Object.keys(Console.prototype);
  for (var v = 0; v < keys.length; v++) {
    var k = keys[v];
    this[k] = this[k].bind(this);
  }
}

Console.prototype.log = function() {
  this._stdout.write(util.format.apply(this, arguments) + '\n');
};


Console.prototype.info = Console.prototype.log;


Console.prototype.warn = function() {
  this._stderr.write(util.format.apply(this, arguments) + '\n');
};


Console.prototype.error = Console.prototype.warn;


Console.prototype.dir = function(object, options) {
  this._stdout.write(util.inspect(object, util._extend({
    customInspect: false
  }, options)) + '\n');
};


Console.prototype.time = function(label) {
  this._times[label] = Date.now();
};


Console.prototype.timeEnd = function(label) {
  var time = this._times[label];
  if (!time) {
    throw new Error('No such label: ' + label);
  }
  var duration = Date.now() - time;
  this.log('%s: %dms', label, duration);
};


Console.prototype.trace = function trace() {
  // TODO probably can to do this better with V8's debug object once that is
  // exposed.
  var err = new Error;
  err.name = 'Trace';
  err.message = util.format.apply(this, arguments);
  Error.captureStackTrace(err, trace);
  this.error(err.stack);
};


Console.prototype.assert = function(expression) {
  if (!expression) {
    var arr = Array.prototype.slice.call(arguments, 1);
    require('assert').ok(false, util.format.apply(this, arr));
  }
};


module.exports = new Console(process.stdout, process.stderr);
module.exports.Console = Console;
```

Clearly, it's far too much work to type all that everytime you just want to say hello. That's why methods/functions exist in the first place. They exist to save time, reduce bugs, and make code easier to read. This is a proccess called **abstraction**. It means to simplify away much of the complexity of code, and delegate the jobs to libraries or other pieces of code. For example, in english, this is how you would order the computer to print "Hi" 100 times.

```eng
Print "Hi" 100 times
```

Unfortunately, that won't actually work, but it's a good high level abstraction of what we want to happen. Consider the next example, that actually works.

```js
let message = "Hi";

for (let i = 0; i < 100; i++) {
    console.log(message);
}
```

It works! It's still a high level abstraction though. We could get lower, closer to the machine's hardware by writing raw machine code, but it would be slow and difficult. That's why abstraction exists; to simplify tasks down as much as possible.
