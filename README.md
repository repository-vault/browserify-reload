browserify-reload is a browserify plugin that reload your client side bundle everytime it gets updated (e.g. through watchify)


[![Version](https://img.shields.io/npm/v/browserify-reload.svg)](https://www.npmjs.com/package/browserify-reload)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](http://opensource.org/licenses/MIT)


# Motivation
I really cannot rely on express interceptor / proxy or whatever, *browserify-reload* provides the slimest overhead to reach an interactive client / server sync & reload.

It use tiny [WS server](https://www.npmjs.com/package/ws) (listening on random port) and inject, through [browserify-wrap](https://www.npmjs.com/package/browserify-wrap) a tiny boostrap prefix on your browserify bundle so it listen for a "reload" event.

For convenience, you can also register additionnal file paths to be watched (once modified, they'll also trigger the client reload signal).

# API

```
const reload = require('browserify-reload');

var b = bundle();
b.plugin(reload [, opts])

b.bundle().pipe(somewhere);
```

## Options
* { deferred : false }
Do not signal the client to reload once the bundle stream ends (so you might apply additionnal, non browserify-compliant processing afterwards BEFORE notifying the client), see opts.xfiles

* { xfiles : [file_path1, file_path2 ] }
Monitor file paths and trigger client reload signal every time they are modified.


# Credits
* [131](https://github.com/131)



# Keywords / shout box
browserify, prefix, suffix, wrapper, plugin, browserify-plugin

