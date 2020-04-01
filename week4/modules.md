# Modules

![machine](https://media.giphy.com/media/oWQzTz2A4fp1m/giphy.gif)

---

## What are they?

> A module in Node.js is a simple or complex functionality organized in single or multiple JavaScript files which can be reused throughout the Node.js application.

---

To include a module in your code, use `require(module-name);`. Modules you want to use must contain a method for *exposing* its contents to you:

1) `module.exports = thing` will expose whatever that thing is (and only that thing will be the value of the `exports` object);
2) `module.exports.thingName = thing` will expose an element of the `exports` object that contains all the elements assigned to it.

---

### Built-in: core modules

|Core Module |Description|
|------------|-----------|
|http| http module includes classes, methods and events to create Node.js http server |
|url| url module includes methods for URL resolution and parsing.|
|querystring| querystring module includes methods to deal with query string.|
|path| path module includes methods to deal with file paths.|

---

```javascript=1
var http = require('http');

var server = http.createServer(function(req, res){

  //write code here

});

server.listen(5000);
```

---

### DIY: 'local' modules
You can do *whatever you want* in a module if you build it yourself - all you need to do is export it at the end and to `require("./modulename")` in any script intending to use it. The dot and slash are required. You can use other modules when making your own; these are referred to as dependencies. devDependencies are modules which are only required during development, while dependencies are modules which are also required at runtime.

---

### Pre-made: '3rd party' modules
3rd party modules, created by other people / organisations, are packaged up and published online.

npmjs.com is the official source for these, and can be sorted by *popularity*, *quality* or *maintenance*.

![pqm](https://i.imgur.com/i2xojN1.png)

---

#### Some of them are fun
![tetris](https://i.imgur.com/5vfHQAs.gif)


---

#### A wild package.json appeared!

```json=1
{
  "name":"tetris",
  "version":"0.1.6",
  "description":"play tetris in your terminal",
  "repository":"git@github.com:mafintosh/tetris.git",
  "keywords":["tetris","terminal","cli"],
  "bin":{
    "tetris":"./index.js"
  },
  "dependencies":{
    "clivas":"0.1.x",
    "keypress":"0.1.x"
  }
}
```

---

## package.json

![info](https://media.giphy.com/media/3o7TKSx0g7RqRniGFG/giphy.gif)

---

A module is a single JavaScript file that has some reasonable functionality.

A package is a directory with one or more modules inside of it and a package.json file which has metadata about the package.

---

### A list of all of the package's metadata

- Created with `npm init`
- Is JSON - The correct syntax is vital
- Is an Object - key value pairs, properties & values
- Keeps project metadata: name, version, license etc.
- Keeps versions of all the projects dependencies
- Keeps a list of useful CLI commands
- Keeps anything else you want to keep track of!

---

### Some key properties
- **name**: string
  only lowercase letters, hyphens (-) and underscores (_)
- ***main**: string
  The project's entry point i.e. the first file to run e.g. src/main.js
- **author**: string or object
  Your name and email or an object with the keys name, email and url.
- **scripts**: Object { string: string }
  a collection of command line commands runable with `npm run`
- **start**: string - optional command to run your package
- keys are what you want to type, values are command line strings

---

### Managing dependencies

Adding a package with `npm install xyz` or `yarn add xyz` automatically adds package xyz to package.json's dependencies property.

Packages that are only required by developers (testing stuff, transpilers etc) should be installed with the `-D` flag e.g. `npm install -D xyz`.

Dependencies aren't always shipped with the package. Anyone consuming your package outside of npm can install them by typing `npm install`. They can skip installing dev dependencies with the `--production` flag.

---

## `npm` 

![packages](https://media.giphy.com/media/3o751VW13telqaPuuY/giphy.gif)

---

### What is `npm`

npm stands for Node Package Manager. 
* Install and uninstall packages
* Version Management
* Dependency Management

---

### Why are `npm` scripts useful?

```terminal
$ ./node_modules/.bin/your-package
```

``` Javascript
{
  "name": "your-application",
  "version": "1.0.0",
  "scripts": {
    "your-package": "your-package"
  }
}
```

---

### What does `npx` do?

- `npx` makes possible to execute a local package as if it's global. 

- Without npx, to execute a package we would have to do it by running it from its local path, or define it as a separate script in the scripts section in the package.json file and then run it with npm run my-package.
With `npx`, we can do this easily by just running:

```terminal
$ npx my-package
```

---

![](https://miro.medium.com/max/640/1*soo6Uu6ZOZpTiedY996Htg.gif)

It’s not a typo, it’s `npx`, not `npm`! 😃
`npM` - Manager
`npX` - eXecute

---


# Cool / useful packages
|package name|description|
|-|-|
|[Nodemailer](https://www.npmjs.com/package/nodemailer)|Send e-mail from javascript|
|[React](https://www.npmjs.com/package/react)|The webs most popular UI framework|
|[React](https://www.npmjs.com/package/react)|The other super popular front end framework|
|[Webpack](https://webpack.js.org/api/node/) | Allows you to use node modules in web pages|
|[JIMP](https://www.npmjs.com/package/jimp)|Process images in JS|
|[JSDom](https://www.npmjs.com/package/jsdom)|Emulate a browser's DOM in node, good for testing|
|[This list](https://github.com/bsonntag/cool-node-modules)| Has a bunch more cool modules to explore |


