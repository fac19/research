# Errors

## How should we handle errors in our Express apps?

---

## Questions to consider

- What kinds of errors can we attempt to recover from? When should we not attempt to recover?

    * Operational errors
    * Programmer errors


---

## Operational errors

* Run-time errors
* Not issues with the programme per se but could relate to the system itself, the system's configuration or network
![image alt](https://media1.tenor.com/images/2ff04b32395b3958d9c2fb6ea3f7b957/tenor.gif?itemid=12232216 =400x250)

---

* Here are some examples:
    * failed to connect to server
    * invalid user input
    * request time out

---

## How to deal with operational errors

---

### Deal with the issue directly
* Sometimes, it's clear what the issue is

![image alt](https://media.giphy.com/media/l2RnB2zd7hxtNimxa/giphy.gif =250x250)


---

### Send the error to your client

* Stop the operation, clear what you've started
* Best thing to do when you know whatever caused the error isn't going to change anytime soon

![image alt](https://media1.tenor.com/images/0cb81f500f8200e4bf2d4f88417ce7de/tenor.gif?itemid=9259882 =400x)

---

### Retry the operation

* For network errors, it helps to retry an operation that returns an error
* Good practice: document how many times you're going to retry, how many times it's going to fail etc
![image alt](https://media1.tenor.com/images/47c87d23e40f52d6420b04a583d33cd0/tenor.gif?itemid=15094960 =400x200)

---

### Log the error
* For when you've tried everything else.

![image alt](https://media.giphy.com/media/26BGIqWh2R1fi6JDa/giphy.gif =400x)

---

## Programmer errors
* Bugs in the program 🐛
* Things that can be avoided by changing the code
* Should not be handled or recovered from
* The code is broken and the program should not be allowed to keep handling requests 

---

## Examples of Programmer Errors
* Missing or invalid arguments
* Tried to read property of “undefined”
* Called an asynchronous function without a callback
* Passed a “string” where an object was expected

---

## Cross-over

Example scenario:
1. A program tries to connect to a server
2. The program crashes
3. The program gets this error: `ECONNREFUSED`

**Operational error:** Connection failure
**Programmer error:** Failure to handle operational error (the socket's error event)

---

## 🧠 QUICK QUIZ: 
1. What kind of error is "File Not Found"?
2. What kind of error do you get when you mistype a variable name?

---

## ANSWERS BEYOND...
![](https://media.giphy.com/media/TvLuZ00OIADoQ/giphy.gif =400x)

---

## 🧠 QUICK QUIZ ANSWERS: 
"File Not Found"
1. Operational Error - The file is just missing and it needs to be created.

Mistyping a variable name
2. Programmer Error - YOU NEED TO CORRECT THE SPELLING IN THE CODE!!!

---

## 4 ways to handle errors in Node.js 
- Throw the error (making it an exception).
- Pass the error to a callback, a function provided specifically for handling errors and the results of asynchronous operations
- Pass the error to a reject Promise function
- Emit an "error" event on an EventEmitter

---

## EXAMPLES

---

## Synchronous Error Handler

Errors that occur in synchronous code inside route handlers and middleware require no extra work.

```JavaScript
app.get('/', function (req, res) {
  throw new Error('BROKEN') 
// ^Express will catch this on its own.
})
```

---

## Asynchronous Error Handler
 
For errors returned from asynchronous functions invoked by route handlers and middleware, you must pass them to the next() function.
```JavaScript 
app.get('/', function (req, res, next) {
  fs.readFile('/file-does-not-exist', function (err, data) {
    if (err) {
      next(err) // Pass errors to Express.
    } else {
      res.send(data)
    }
  })
})
```

---

```JavaScript
app.get('/', function (req, res, next) {
  setTimeout(function () {
    try {
      throw new Error('BROKEN')
    } catch (err) {
      next(err)
    }
  }, 100)
})
```

---

## We can write our own promises for async errors

```JavaScript
app.get('/', function (req, res, next) {
  Promise.resolve().then(function () {
    throw new Error('BROKEN')
  }).catch(next) // Errors will be passed to Express.
})
```

---

## Useful resources
[Node Production Practices - Error Handling](https://www.joyent.com/node-js/production/design/errors)
[Express JS - Error handling](https://expressjs.com/en/guide/error-handling.html)

