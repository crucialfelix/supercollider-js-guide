
# npm

[`npm`](https://www.npmjs.com/) is the Node Package Manager.

- It is an executable that comes with node for installing packages.
- As well as a registery and host for those packages.
- You can publish packages quite easily.
- It is also a bit slow sometimes.

There are various sites for searching and exploring what's out there:

- https://www.npmjs.com/search?q=music
- https://npmsearch.com/?q=music
- http://nipstr.com/#music

## yarn

[`yarn`](https://yarnpkg.com/) is a new alternative to npm from facebook.

It is much much faster, uses a local cache to avoid re-downloading and can even work offline. Since some packages may compile c++ for your system, it can save a significant amount of time to have a local cache.

yarn uses the same registery and supports the same <abbr title="command line interface">cli</abbr> features as npm. It is a drop-in replacement.

You might want to stick to `npm` until you feel confident with the eco-system. `npm` and `yarn` installed together can sometimes cause some head scratching.

It's quite easy to switch a project to yarn later - just delete your `node_modules` folder and run `yarn install`
