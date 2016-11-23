# Await & Async

`async` `await` are currently Stage 3 ("Candidate") but will most probably be finalized soon. [Full spec](https://tc39.github.io/ecmascript-asyncawait/).

Expected in Node 8
Chrome 55
Firefox 52 Nightly
Microsoft Edge has supported it since 2015, which is only fitting since the `async`/`await` syntax originated with Microsoft C#.


But we can write code with it now:

```js
import { server, msg } from 'supercolliderjs';

// To use await you have to be running inside an async function
(async function() {
  // Now anything that returns a Promise can be simply awaited
  // rather than server.boot().then((s) => { }, console.error)
  let s = await server.boot();

  let g = await s.group();
  let def = await s.synthDef('noiseburst', `
    SynthDef("noiseburst", { |out, amp=0.1, sustain=0.01, pan|
    	var snd = PinkNoise.ar(1.0);
    	var amp2 = amp * AmpComp.ir(1.max(50)) * 0.5;
    	var env = EnvGen.ar(Env.sine(sustain, 1.0), levelScale: amp2, doneAction: 2);
    	OffsetOut.ar(out, Pan2.ar(snd * env, pan));
    }, \ir ! 5)
  `);

  let y = await s.synth(def, {sustain: 0.1, pan: 0.2});

})();  // calling the async function
```

This transpiles to something ugly like this:

```js
'use strict';
var _regenerator = require('babel-runtime/regenerator');
var _regenerator2 = _interopRequireDefault(_regenerator);
var _asyncToGenerator2 = require('babel-runtime/helpers/asyncToGenerator');
var _asyncToGenerator3 = _interopRequireDefault(_asyncToGenerator2);
var _supercolliderjs = require('supercolliderjs');

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { default: obj }; }

(0, _asyncToGenerator3.default)(_regenerator2.default.mark(function _callee() {
  var s, spawnGroup;
  return _regenerator2.default.wrap(function _callee$(_context) {
    while (1) {
      switch (_context.prev = _context.next) {
        case 0:
          spawnGroup = function spawnGroup() {
            s.send.bundle(0.03, [_supercolliderjs.msg.groupNew(s.state.nextNodeID())]);
          };
          _context.next = 3;
          return _supercolliderjs.server.boot();

        case 3:
          s = _context.sent;
          s.send.msg(_supercolliderjs.msg.dumpOSC(1));
          setInterval(spawnGroup, 2000);

        case 6:
        case 'end':
          return _context.stop();
      }
    }
  }, _callee, this);
}))();
```

http://kangax.github.io/compat-table/es2016plus/

https://tc39.github.io/ecmascript-asyncawait/

https://spion.github.io/posts/es7-async-await-step-in-the-wrong-direction.html
