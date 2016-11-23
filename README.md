# Introduction

Work in progress.

The JavaScript client library for SuperCollider.

SuperCollider is an environment and programming language for real time audio synthesis and algorithmic composition. It provides an interpreted object-oriented language which functions as a network client to a state of the art, realtime sound synthesis server.

This library, SUPERCOLLIDER.JS provides functionality for working with:

- scsynth (the synthesis server)
- sclang (supercollider language interpreter)

## Features

- Send and receive OSC messages
- Comprehensive support for calling all commands the server understands
- Call async commands on the server receive results as Promises
- Synth/Group/Bus/Buffer allocators with clean immutable state implementation
- Server state and synth/group tracking
- Just-in-time OSC scheduler
- Codebase written with Flow (type checking)
- High unit test coverage


See also:

[API](https://crucialfelix.github.io/supercolliderjs/api/)
