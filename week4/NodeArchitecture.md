# Node architecture
How does Node handle lots of requests despite running on a single processor thread?

---

## The Node.js Event Loop

When you start your node process, for example by running `node index.js` in your terminal, this happens:
1. The V8 engine reads through and processes your `index.js` file, requires the modules and executes any code in it.
2. The V8 engine then immediately starts up an “Event Loop”.

---

### The Event Loop makes Node.js run successfully

- Node.js code runs on a single JavaScript thread with just one thing happening at a time.
- You need to avoid blocking this thread with code that takes too long to return, otherwise the rest of your JavaScript will not execute.
- This is where the event loop comes in: it allows Node.js to perform non-blocking I/O operations.

---

### The Call Stack

- The callstack is a LIFO (Last In, First Out) queue.
- The event loop continuously checks the callstack, adds any functions it finds and executes them in order.

---

### The Job Queue

- Introduced in ES6, the Job Queue is used by Promises.
- It enables the execution of an async function ASAP, rather than being put at the end of the call stack.
- Promises that resolve before the current function ends will be executed right after the current function.

---

### Why should we use Async?

- Async functions run parallel to the main thread
- Can improve application performance and responsiveness

![](https://media.giphy.com/media/UFNDkegIOiU4o/giphy.gif)

---

![](https://www.vbatelemetry.com/wp-content/uploads/2018/03/Asynchronous-vs-Synchronous.png =800x)

---

### When is it best to use Async?

- Processing of a large amount of data e.g. 
- Tasks can be performed mostly independent of each other

---

### Async/Await

- enable asynchronous code to behave more synchronously
- await pauses the async function and waits for the promise to be resolved before continuing

![](https://media.giphy.com/media/Y0wppNXGvipzobCIfy/giphy.gif)


---

```javascript=
 const makeRequest = () => {
  return promise1()
    .then(value1 => {
      // do something
      return promise2(value1)
        .then(value2 => {
          // do something          
          return promise3(value1, value2)
        })
    })
}

```

---

```javascript=
  const makeRequest = async () => {
      const value1 = await promise1()
      const value2 = await promise2(value1)
      return promise3(value1, value2)
    }
```

---

## How does Node use callbacks to manage asynchronous code?

---

### Reminder - What is callback?
![](https://media1.tenor.com/images/efb6e4531ef509e3b438233b483a8800/tenor.gif?itemid=14220209)

A callback function is a function that is passed as an argument to another function, to be “called back” at a later time.

---


### Why are they useful in node?

- servers fetch data from different sources, this is time consuming 
- passing a function as a callback allows for data to be fetched and/or manipulated before it's passed as an argument to the callback function 

---

### Pros:
- Handy for single async operations. Allow easy data and error control.
- Should work on every node version and almost all packages of node. As callbacks are functions, they don’t need any transpilers.

### Cons:
- For multiple nested async operations this creates a callback hell
- Error handling has to be done for each operation (no global exception handler)

---

### Callback #hell

![](https://s3.amazonaws.com/com.twilio.prod.twilio-docs/original_images/31orCejQRkSvmchYeZC2GKswNtst-d_xEoSPoP3X-bAm9RRe8hxz59vVZrrRm78VvJgVbuUo5R.png)

---

### What is callback hell

- chaining too many callback functions
- functions need to be executed in a certain order
- can be avoided by "modularizing" your code i.e

---

#### Refactoring this:

```javascript=
var form = document.querySelector('form')
form.onsubmit = function formSubmit (submitEvent) {
  var name = document.querySelector('input').value
  request({
    uri: "http://example.com/upload",
    body: name,
    method: "POST"
  }, function postResponse (err, response, body) {
    var statusMessage = document.querySelector('.status')
    if (err) return statusMessage.value = err
    statusMessage.value = body
  })
}

```

---

#### Into this

```javascript=
document.querySelector('form').onsubmit = formSubmit

function formSubmit (submitEvent) {
  var name = document.querySelector('input').value
  request({
    uri: "http://example.com/upload",
    body: name,
    method: "POST"
  }, postResponse)
}

function postResponse (err, response, body) {
  var statusMessage = document.querySelector('.status')
  if (err) return statusMessage.value = err
  statusMessage.value = body
}
```

---

### Don't always use callbacks

- Async/await
    - "cleaner code"
- promises 
    - easy chaining 

[See pros and cons of all in this freeCodeCamp article - click](https://www.freecodecamp.org/news/moving-from-callbacks-to-async-await-in-node-c3da26460dd1/)

---

### new keyword

- new constructor(argument1, argument2, ...);
The constructor "specifies the type of the object"

- used in async/callback. e.g. new Error,  new Promise.

---

- "new Foo(arguments....)"
-- Creates a blank JavaScript object, (inheriting from Foo.prototype); and the object comes with a "this" keyword. 
-- Sets the constructor of this object to another object (i.e. links it to another object). 
-- The constructor function Foo is called with the specified arguments. 
-- Returns "this" if the function doesn't return its own object.
-- (Normally constructors don't return a value, but they can choose to do so)

---

```javascript=
new Promise(function(resolve, reject){
    if(){
        resolve()
    }else{
        reject() 
    }
})
```
(goes in job queue)

![](https://mdn.mozillademos.org/files/15911/promises.png)

---

