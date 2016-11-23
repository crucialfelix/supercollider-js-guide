
# Promises


```js
let supercolliderjs = require('supercolliderjs');

let promise = supercolliderjs.lang.boot();

promise.then((sclang) => {
  // sclang is booted and ready for use
}, (error) => {
  // something went wrong !
  console.error(error);
});
```


```js
let supercolliderjs = require('supercolliderjs');

supercolliderjs.lang.boot().then((sclang) => {
  sclang.interpret(`
    (1..8).pyramid;
  `).then((result) => {
    console.log(result);
  }, (error) => {
    console.error(error);
  });
});
```

## Promise chaining

```js
let { lang } = require('supercolliderjs');

lang.boot()
  .then(sclang => sclang.interpret(`(1..8).pyramid;`))
  .then(console.log, console.error);
```


```js
let sc = require('supercolliderjs');

sc.server.boot().then((server) => {
  let def = server.loadSynthDef('formant', './formant.scd');
  let group = server.group();

  function randFreq() {
    return sc.map.linToExp(0.0, 1.0, 100, 5000, Math.random());
  }

  return server.synth(def, {
    fundfreq: randFreq(),
    formantfreq: randFreq(),
    bwfreq: randFreq(),
    pan: sc.map.linToLin(0, 1, -1, 1, Math.random()),
    timeScale: dur
  }, group);
});
```

## Call and response OSC messages can return Promises

Many server OSC commands reply with a return OSC command.
`server.callAndResponse()` makes these very simple to do.

```js
let path = require('path');
let sc = require('supercolliderjs');
let { msg } = sc;

sc.server.boot().then((server) => {

  let bufId = server.state.allocBufferID(2);
  let cr = msg.bufferAllocRead(bufId, path.join(__dirname, './soundfile.aiff'));
  server.callAndResponse(cr).then((ok) => {
    // buffer is now loaded
  }, (error) => {
    // failed to load the sound file
  });

  // Much easier way:
  // let b = server.readBuffer('./soundfile.aiff', 2);
});
```


## Making Promises

```js
function giveMe(options) {}
  return new Promise((resolve, reject) => {
    // do something asynchronous, fetch a URL,
    //   resolve({some: "result"})
    // or
    //   reject(new Error('Oh dear...'))
  });
}
```

- `giveMe().then(onSuccess, onError)`
- `giveMe().catch(onError)` - don't forget to catch errors
- `giveMe().finally(onComplete)` - always runs
- `Promise.all([giveMe({thing: 1}), giveMe({thing: 2})]).then(...)`
- `Promise.resolve({some: "result"})` - make an already resolved Promise
- `Promise.reject(new Error('Oh dear'))` - make an already rejected Promise
