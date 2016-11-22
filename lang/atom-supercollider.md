# atom-supercollider

Atom SuperCollider is a mini-IDE for the SuperCollider language running in the Atom editor.

https://atom.io/packages/supercollider

atom-supercollider is powered by supercollider.js. The interpreter, process and error handling are all here in supercollider.js.

This means that atom-supercollider focuses just on things to do with the Atom editor and interface, and supercollider.js focuses on working with sclang and scsynth.

Other IDEs could also use this, and this package could also be used to embed SuperCollider REPLs in other projects like multi-user live coding.


## paths and config

If you are using the .supercollider.yaml config feature in atom-supercollider then you may wish to later run that code outside of Atom.

Install supercolliderjs globally and use the supercollider command::

    supercollider my-piece.scd

Paths and configuration settings will be identical inside or outside of atom.
If you wish to switch easily back and forth with the SC IDE then you may wish to do your config using startup.scd and sclang_conf.yaml
