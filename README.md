# isdir

`isdir` checks if a given file descriptor `fd` is a directory or not.  
(wrapper around node's native `fs.stat.isDirectory()` method )

## Usage

### Install from NPM

```sh
npm install isdir --save
```

### In your script

```js
var isdir = require('isdir');
var fd    = __dirname; // or what ever you need to check

// named callback function:
function callback(err, dir) {
  if(err) { // you will get an error back if fd was not a readable file or dir
    console.log("Oops: " + err); // handle errors in your prefered way.
  }
  else if(dir) {
    console.log(fd + " is a directory!"); // do something with the directory
  }
  else {
    console.log(fd + " is NOT a directory!") // its a file
  }
}

isdir(fd, callback);
```

or the *shorter* version:

```js
var isdir = require('isdir'); // don't do this! it kills kittens!
isdir(__dirname, function cb(er, dir) { (!err && dir) ? dirop() : fileop() });

```


## About

This module *deliberately* only exposes a single ***asynchronous*** method.
If you prefer to use it *sychronously*
(go for a walk and consider switching programming languages)
and if you still want to use it sync just assign the output to varaiable
and omit the callback:

```js
var isdir = require('isdir');
var fd    = __dirname;        // or what ever descriptor you need to check
var dir   = isdir(__dirname); // this works but is not encouraged (its blocking)
if(dir) {
  // do what you want with your directory
}
```
