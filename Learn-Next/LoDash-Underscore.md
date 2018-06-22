Why Lodash?
Lodash makes JavaScript easier by taking the hassle out of working with arrays, numbers, objects, strings, etc.
Lodash’s modular methods are great for:

Iterating arrays, objects, & strings
Manipulating & testing values
Creating composite functions

---

Installation

Download:

[LoDash](https://lodash.com/)

In a browser:

```
<script src="lodash.js"></script>
```

Using npm:

```
$ npm i -g npm
$ npm i --save lodash
```

In Node.js:

```
// Load the full build.
var _ = require('lodash');
// Load the core build.
var _ = require('lodash/core');
// Load the FP build for immutable auto-curried iteratee-first data-last methods.
var fp = require('lodash/fp');

// Load method categories.
var array = require('lodash/array');
var object = require('lodash/fp/object');

// Cherry-pick methods for smaller browserify/rollup/webpack bundles.
var at = require('lodash/at');
var curryN = require('lodash/fp/curryN');
```
