---
tags: [javascript, runtime]
title: node
created: '2020-02-28T21:20:20.353Z'
modified: '2025-03-01T17:09:02.756Z'
---

# node

> server-side [[javascript]] runtime

## install

```sh
brew install node
```

# environment

```sh
NODE_OPTIONS          # set opts e.g. NODE_OPTIONS=--max-old-space-size=32768
```

## option

```sh
-             # alias for STDIN
--            # indicate end of cli options, pass rest of the script args
-c, --check   # check syntax without executing, exits with error code if script is invalid
-e, --eval    # string Evaluate string as js
```

## usage

```sh
node                        # start repl

node .                      # exec in current dir ?!

node --version              # get version

node -e "console.log(1)"    # evaluate string

node -e "var data = require('./FILE'); console.log(JSON.stringify(data, null, 2));" # pretty print json from js-obj
```

## repl

```js
.break    // when in the process of inputting a multi-line expression, enter the .break command (or press Ctrl+C) 
          // to abort further input or processing of that expression

.clear    // resets the REPL context to an empty object and clears any multi-line expression being input.
.exit     // close the I/O stream, causing the REPL to exit.
.help     // show this list of special commands.
.save     // save the current REPL session to a file: > .save ./file/to/save.js
.load     // load a file into the current REPL session. > .load ./file/to/load.js
.editor   // enter editor mode (Ctrl+D to finish, Ctrl+C to cancel)


process.cwd()       // current working directory of the nodejs process

process.env         // print env variables

process.version     // current nodejs version


var data = require('./FILE')   // load a FILE
```

---

## CommonJS (`module.exports = { someFunc };`)

- widely used for server-side development
- designed for synchronous loading, which is suitable for server environments but not ideal for browsers
- uses `require()` for importing modules and `module.exports` or `exports` for exporting

```js
function sayHello(name) {
    console.log(`Hello, ${name}!`);
}

module.exports = { sayHello };

> const foo = require('./hello.js');
> foo.sayHello('World');
```

## ESM/ESModules (`export function someFunc() {}`)

- standard js module system, introduced in ES6 (ECMAScript 2015)
- supports both synchronous and asynchronous module loading
- suitable for both server-side and client-side development
- uses `import` for importing modules and `export` for exporting

```js
export function someFunc() {
  console.log("This is someFunc");
}

import { someFunc } from './path/to/module.js';
```

## see also

- [[js]] `spidermonkey` cli
- [[nodejs event loop]]
- [[javascript]]
- [[npm]], [[npx]], [[nvm]]
- [[yarn]]
- [[deno]]
- [nodejs.org/api/process.html](https://nodejs.org/api/process.html)
- [nodejs.org/api/repl.html#repl_commands_and_special_keys](https://nodejs.org/api/repl.html#repl_commands_and_special_keys)
