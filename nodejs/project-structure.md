# global versus local

Node package can be either installed globally or locally—just for the project you are working on.

The main reason to install something globally is because it supplies new commandline commands that are available to you in the terminal regardless of what folder you are in.

```
npm install --global supercolliderjs
```

or

```
npm install supercolliderjs
```


By `locally` we mean that you have a folder with a `package.json` file in it.

Simplest folder layout:

```sh
.
├── index.js
├── node_modules
└── package.json
```

So as soon as their is a package.json file, then it becomes a package, and can install other packages as dependencies. `npm` installs those into the `node_modules` folder.

You can create a package file with `npm init`:

```sh
code ❯ mkdir myproject
code ❯ cd myproject
myproject ❯ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg> --save` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
name: (myproject)
version: (1.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to /Users/crucial/Downloads/myproject/package.json:
```
```json
{
  "name": "myproject",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```
```sh
Is this ok? (yes)
```

## Installing packages

Now you can add dependencies—packages that your project will use.

You can do this with:

```sh
npm install --save supercolliderjs
```

`install` tells it to install the package into node_modules

`--save` tells it to also alter the package.json file and add supercolliderjs as a dependency for this project.

```sh
myproject ❯ npm install --save supercolliderjs

> dryadic@0.3.0 postinstall /Users/crucial/Downloads/myproject/node_modules/dryadic
> node -e "require('fs').stat('lib', function (e, s) { process.exit(e || !s.isDirectory() ? 1 : 0) })" || npm run build


> supercolliderjs@0.13.0 postinstall /Users/crucial/Downloads/myproject/node_modules/supercolliderjs
> node -e "require('fs').stat('lib', function (e, s) { process.exit(e || !s.isDirectory() ? 1 : 0) })" || npm run build

myproject@1.0.0 /Users/crucial/Downloads/myproject
└─┬ supercolliderjs@0.13.0
  ├── bluebird@3.4.6
  ├─┬ chalk@1.1.3
  │ ├── ansi-styles@2.2.1
  │ ├── escape-string-regexp@1.0.5
  │ ├─┬ has-ansi@2.0.0
  │ │ └── ansi-regex@2.0.0
  │ ├── strip-ansi@3.0.1
  │ └── supports-color@2.0.0
  ├─┬ commander@2.9.0
  │ └── graceful-readlink@1.0.1
  ├─┬ cuid@1.3.8
  │ ├── browser-fingerprint@0.0.1
  │ ├── core-js@1.2.7
  │ └── node-fingerprint@0.0.2
  ├─┬ dryadic@0.3.0
  │ ├─┬ is-plain-object@2.0.1
  │ │ └── isobject@1.0.2
  │ └── underscore@1.8.3
  ├── immutable@3.8.1
  ├─┬ js-yaml@3.6.1
  │ ├─┬ argparse@1.0.9
  │ │ └── sprintf-js@1.0.3
  │ └── esprima@2.7.3
  ├── lodash@4.16.6
  ├── ncp@2.0.0
  ├─┬ osc-min@1.1.1
  │ └── binpack@0.1.0
  ├── rx@4.1.0
  ├─┬ temp@0.8.3
  │ ├── os-tmpdir@1.0.2
  │ └── rimraf@2.2.8
  └── untildify@3.0.2

npm WARN myproject@1.0.0 No description
npm WARN myproject@1.0.0 No repository field.
```

Now that it is installed, if you open a node REPL you can now require (import) that package. When ou run node, it can import anything that is in the node_modules directory.

```sh
myproject ❯ node
> let sc = require('supercolliderjs')
```

`sc` is an `Object` (like a Dictionary) with all the functionality that supercollider.js exports.

```sh
> sc
{ lang:
   { SCLang: { [Function: SCLang] boot: [Function: boot] },
     boot: [Function: boot] },
  server: { Server: [Function: Server], boot: [Function: boot] },
  scapi: { SCAPI: [Function: SCAPI] },
  resolveOptions: [Function: resolveOptions],
  map:
   { midiToFreq: [Function: midiToFreq],
     freqToMidi: [Function: freqToMidi],
     linToLin: [Function: linToLin],
     linToExp: [Function: linToExp],
     expToLin: [Function: expToLin],
     ampToDb: [Function: ampToDb],
     dbToAmp: [Function: dbToAmp],
     linear: [Function: linear],
     exp: [Function: exp],
     dB: [Function: dB],
     fader: [Function: fader],
     unmapLinear: [Function: unmapLinear],
     unmapExp: [Function: unmapExp],
     unmapDb: [Function: unmapDb],
     unmapFader: [Function: unmapFader],
     unmapWithSpec: [Function: unmapWithSpec],
     mapWithSpec: [Function: mapWithSpec] },
  msg:
   { AddActions: { HEAD: 0, TAIL: 1, BEFORE: 2, AFTER: 3, REPLACE: 4 },
     quit: [Function: quit],
     notify: [Function: notify],
     status: [Function: status],
     cmd: [Function: cmd],
     dumpOSC: [Function: dumpOSC],
     sync: [Function: sync],
     clearSched: [Function: clearSched],
     error: [Function: error],
     defRecv: [Function: defRecv],
     defLoad: [Function: defLoad],
     defLoadDir: [Function: defLoadDir],
     defFree: [Function: defFree],
     nodeFree: [Function: nodeFree],
     nodeRun: [Function: nodeRun],
     nodeSet: [Function: nodeSet],
     nodeSetn: [Function: nodeSetn],
     nodeFill: [Function: nodeFill],
     nodeMap: [Function: nodeMap],
     nodeMapn: [Function: nodeMapn],
     nodeMapAudio: [Function: nodeMapAudio],
     nodeMapAudion: [Function: nodeMapAudion],
     nodeBefore: [Function: nodeBefore],
     nodeAfter: [Function: nodeAfter],
     nodeQuery: [Function: nodeQuery],
     nodeTrace: [Function: nodeTrace],
     nodeOrder: [Function: nodeOrder],
     synthNew: [Function: synthNew],
     synthGet: [Function: synthGet],
     synthGetn: [Function: synthGetn],
     synthNoid: [Function: synthNoid],
     groupNew: [Function: groupNew],
     parallelGroupNew: [Function: parallelGroupNew],
     groupHead: [Function: groupHead],
     groupTail: [Function: groupTail],
     groupFreeAll: [Function: groupFreeAll],
     groupDeepFree: [Function: groupDeepFree],
     groupDumpTree: [Function: groupDumpTree],
     groupQueryTree: [Function: groupQueryTree],
     ugenCmd: [Function: ugenCmd],
     bufferAlloc: [Function: bufferAlloc],
     bufferAllocRead: [Function: bufferAllocRead],
     bufferAllocReadChannel: [Function: bufferAllocReadChannel],
     bufferRead: [Function: bufferRead],
     bufferReadChannel: [Function: bufferReadChannel],
     bufferWrite: [Function: bufferWrite],
     bufferFree: [Function: bufferFree],
     bufferZero: [Function: bufferZero],
     bufferSet: [Function: bufferSet],
     bufferSetn: [Function: bufferSetn],
     bufferFill: [Function: bufferFill],
     bufferGen: [Function: bufferGen],
     bufferClose: [Function: bufferClose],
     bufferQuery: [Function: bufferQuery],
     bufferGet: [Function: bufferGet],
     bufferGetn: [Function: bufferGetn],
     controlBusSet: [Function: controlBusSet],
     controlBusSetn: [Function: controlBusSetn],
     controlBusFill: [Function: controlBusFill],
     controlBusGet: [Function: controlBusGet],
     controlBusGetn: [Function: controlBusGetn],
     nonRealTimeEnd: [Function: nonRealTimeEnd] },
  Dryad: [Function: Dryad],
  dryads:
   { SCServer: [Function: SCServer],
     SCLang: [Function: SCLang],
     Group: [Function: Group],
     Synth: [Function: Synth],
     AudioBus: [Function: AudioBus],
     SCSynthDef: [Function: SCSynthDef],
     SynthControl: [Function: SynthControl],
     SynthStream: [Function: SynthStream],
     SynthEventList: [Function: SynthEventList],
     layer: { middleware: [Object], classes: [Object] },
     dryadic: [Function: dryadic],
     play: [Function: play],
     h: [Function: h] },
  dryadic: [Function: dryadic],
  play: [Function: play],
  h: [Function: h]}
```

You can read the full API documentation for all of those functions here: (coming...)

Note that in JavaScript classes are printed to the console as: `[Function: Server]` where Server is the name of the class. So that Server class actually has a lot of functionality in it, but here you only see it listed as [Function: Server]. 

This will be explained more in [Classes](../javascript/classes.md)

## main

```json
{
  "main": "index.js"
}
```

The "main" setting is for packages that are intended to be published and used by other packages and projects.

It is the file that exports all the functionality. This could be a single function (for very simple packages) or like supercollider.js it could be an Object.

```javascript
// index.js
module.exports = {
  lang: {
    SCLang: SCLang,
    boot: boot
  }
  // etc.
};
```

In ES2015 this looks even cleaner:

```js
// src/index.js
export server from './server/server';
export lang from './lang/sclang';
```

To use this style you'll first want to learn about transpiling and Babel.


## scripts and bin
