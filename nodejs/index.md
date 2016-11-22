# Installation

## Node.js

To do anything with supercollider.js, whether from the commandline or for building apps to be used in a browser, you will need Node.js.

As of this writing Node 6.x is the most current LTS (Long Term Support) version and the one I recommend using.

This supports all of ES2015 syntax which is a significantly improved version of JavaScript.

But as you shall see it doesn't matter so much anymore what your interpreter supports becasue we can use whatever language features we want and then transpile the source code to a version of the source code that your interpreter can use.

You can even get generators and `async/await` syntax to run on your granny's IE8.

So we live in the future and we compile it for the past.

(See [Babel, ES2015 and Beyond](./javascript/babel-and-beyond))

Node 7 is out, but does not add that much new language support.

Node 8 will support `import` which will be very important (see [JavaScript: require vs import](./javascript/require-vs-import))

All the examples here are written for Node 6.x and do not require transpiling except where noted.

### installing node

I recommend using `nvm` - Node Version Manager to install Node.js. This let's you easily update to the latest version or switch between multiple versions.

[Install NVM](./installation/nvm.md)

You can also just download a prebuilt Node.js from: https://nodejs.org/en/download/

## Does it work ?

You should now be able to start a node REPL from the command line:

```sh
supercolliderjs-guide ❯ node
> console.log("hello?")
hello?
undefined
> 1 + 1
2
> const say = (what) => console.log(what);
undefined
> say("hello")
hello
undefined
> let obj = { data: { one: 1, two: 2 }}
undefined
> let {data: { one, two }} = obj
undefined
> one
1
> two
2
>
(To exit, press ^C again or type .exit)
```

You might have noticed that that JavaScript looks a bit fancy.

We'll get to that in [Arrow functions](./javascript/arrow-functions) and [Destructuring](./javascript/destructuring)


## Basic usage

Using the REPL is fine for simple tests and experimentation, but it isn't like SuperCollider where you have a bunch of text in a file and then execute lines and blocks here and there.
