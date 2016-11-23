# Babel, ES2015 and Beyond

written in:
http://node.green/ ES2015 features

with flow
but compiled to ES5


## As of Nov 2016, ES2015 runs on:

- Chrome
- Safari
- Firefox
- Edge
- Node 6

Compatability Tables:

- [kangax es6](https://kangax.github.io/compat-table/es6/)
- [node.green](http://node.green/)


Babel takes source code like this:

```js
class Synth extends Group {
  set(settings:Object) {
    this.server.send.msg(msg.nodeSet(this.id, settings));
  }
}
```

and transpiles it for older browsers:

```js
var Synth = function (_Group) {
  _inherits(Synth, _Group);

  function Synth() {
    _classCallCheck(this, Synth);

    return _possibleConstructorReturn(this, (Synth.__proto__ || Object.getPrototypeOf(Synth)).apply(this, arguments));
  }

  _createClass(Synth, [{
    key: 'set',
    value: function set(settings) {
      this.server.send.msg(msg.nodeSet(this.id, settings));
    }
  }]);

  return Synth;
}(Group);
```
