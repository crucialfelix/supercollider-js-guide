# Destructuring

```js
let list = [1, 2];
let [a, b] = list;
// a == 1
// b == 2
```

```js
let object = {
  freq: 440,
  amp: 0.9
};
let { freq, amp } = object;
// freq == 440
// amp == 0.9
```

```js
import { server, map } from 'supercolliderjs';
```


## Deep destructuring

```js
let options = {
  server: {
    host: '43.5.3.2',
    port: '12345'
  }
};
let { server: { host, port } } = options;
// host == '43.5.3.2'
// port == '12345'

// Functions can destructure their arguments
function boot({ server: { host, port } }) {
  // let host = options.server.host;
  // let port = options.server.port;
  connectToHost(host, port);
}

boot(options);
```

## Spread

```js
let iterableObj = [1, 2, 3];
myFunction(...iterableObj);
let newList = [...iterableObj, 4, 5, 6];

let obj = {key: 'value', freq: 440, amp: 0.9};
let newObj = {thing: 'thong', ...obj};
```

```js
let freq = 440;
let obj = {
  amp: 0.8,
  freq
};
// very short creation of object:
let params = {freq};
```

## Rest args

```js
function(a, b, ...theArgs) {
  // theArgs is an Array
}
```
