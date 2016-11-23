# Generators

Essentially the same as SuperCollider's `Routine`

```js
// GeneratorFunction
function *Pseq(list, repeats=1) {
  for (let i = 0; i < repeats; i++) {
    for (let value of list) {
      yield value;
    }
  }
}

// Calling the function produces a Generator
let p = Pseq([60, 72, 71, 67, 69, 71, 72, 60, 69, 67], 2);

// iterate
for (let v of p) {
  console.log(v);
}
```

## yield *

```js
function *Pseq(list, repeats=1) {
  for (let i = 0; i < repeats; i++) {
    for (let value of list) {
      yield value;
    }
  }
}

let pseqs = [
  Pseq([60, 72, 71, 67, 69, 71, 72, 60, 69, 67], 2),
  Pseq([60, 60, 69, 67], 1),
  Pseq([60, 69, 67], 3)
];

function *Pseqs(pseqs) {
  for (let p of pseqs) {
    // embedInStream  - delegate the stream to generator p
    // till it runs out
    yield *p;
  }
}

for (let v of Pseqs(pseqs)) {
  console.log(v);
}

```

[Much more about Generators](https://github.com/getify/You-Dont-Know-JS/blob/master/async%20%26%20performance/ch4.md)
