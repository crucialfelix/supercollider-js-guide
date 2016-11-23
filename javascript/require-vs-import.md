# require vs import

`import` is not in ES2015; it is not yet implemented in Node.JS or in any browser.

When writing code for the Node.js 6 command line that you will not be transpiling,
you should not use import and export.

But modules often write using `import` and `export` which is then transpiled to `require` and `module.exports`

The syntax looks like this:

```js
import { map } from 'supercolliderjs';

export function freqMap(value) {
  return map.linToExp(0, 1, 50, 6400, value);
}

export function randomFreq() {
  return freqMap(Math.random());
}
```

Using require:

```js
let sc = require('supercolliderjs');
let { map } = sc;

function freqMap(value) {
  return map.linToExp(0, 1, 50, 6400, value);
}

function randomFreq() {
  return freqMap(Math.random());
}

module.exports = {
  freqMap,
  randomFreq
}
```


TODO: explain default
