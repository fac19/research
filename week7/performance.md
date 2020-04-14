# Perfomance

![bolt](https://media.giphy.com/media/11pEf1ZMBCxoe4/giphy.gif)

---

## How can we make our servers go faster? -K

![two](https://media.giphy.com/media/aQAxiVPS1dAdy/giphy.gif)

**Our code (the dev part)**

**Our environment (the ops part)**

---

# Our Code

![code](https://media.giphy.com/media/dU2wVNftAEvAI/giphy.gif)

---

### GZIP
![zip](https://media.giphy.com/media/efP7HmNYpIiJxxQDI4/giphy.gif)

---

#### What is gzip? -K

- gzip is a file format, and a software application used for file **compression** and **decompression**
- Using gzip will reduce the file size of your pages and stylesheets 
- Basically makes it go faster!!!  :racing_car: 


![compress](https://media.giphy.com/media/l2Sq8ITu4aB7Utj7a/giphy.gif =400x )

---

#### How Gzip Works -K
[YouTube Video, start at 0.40secs | end at 1.05](https://youtu.be/Mjab_aZsdxw?t=40)
- When a server receives a request for a web page, the server checks the header of the request to determine if the browser supports gzip
- The server generates the markup for the page before applying gzip
- Gzip converts the markup into a compressed data stream which is then delivered to the end user
- Then the browser decompresses it

---

#### Setting-up gzip compression -C
npm install compression

```javascript=
const compression = require('compression');
const express = require('express');
const server = express();

server.use(compression());
```
If it is working you'll see a drop in the size of files served in the network tab in dev tools

---

### Minimise synchronous code -C
Many Node modules offer both synchronous and asynchronous versions of their functions, so make sure you are always going asynchronous in production. 
- --trace-sync-io command-line flag

Synchronous code includes...

---

**Console.log()**
![logging](https://media.giphy.com/media/rOWcwUZGcbSnK/giphy.gif =400x)

---

### Debugging
Console.log() is synchronous so avoid using it.

![log survey](https://hackernoon.com/hn-images/0*kXpzbvVMwrsvxbbP.png =600x)

---

Perhaps try using module 'debug' instead
![](https://user-images.githubusercontent.com/71256/29091486-fa38524c-7c37-11e7-895f-e7ec8e1039b6.png =700x)

---

### Handle exceptions properly -K

![](https://media.giphy.com/media/IgsXOXGPxfT3O/giphy.gif)

---

#### Don't Use: -K
```javascript=
process.on('uncaughtException'(?) => {
    // Blah
}
```
- Adding an event listener for uncaughtException will change the default behavior
- The process will continue to run despite the exception
- This might sound like a good way of preventing your app from crashing, but running after an uncaught exception is a DANGEROUS:warning: 


---

### Use Try-Catch -K
To catch exceptions in synchronous code
```javascript=
app.get('/idontknow', function (req, res) {
  // Simulating async operation
  function blah() {
    try {} 
    catch (e) {}
  }
})
```

---

### Use Promises -K
To catch exceptions in asynchronous code
```javascript=
app.get('/maybeso', function (req, res, next) {
  // do some sync stuff
  queryDb()
    .then()
    .then()
    .catch(next)
})
```

---

### Remove unnecessary Middleware
Make sure you only create and require middleware that is used

![](https://media.giphy.com/media/30pxUsK4pnIG9BgKgw/giphy.gif)

---

# Our Environment :evergreen_tree: 

![love your environment](https://media.giphy.com/media/l4EoTOUIVjRa8QBW0/giphy.gif)

---

### Cache request results :tanabata_tree: 

<!--- If we have a complex + heavy page which may take 2 seconds to generate the HTML output, is it rational to ask the web server to render this page for each different user? --->

Server side caching responds to the same content for the same request independently of the client's request. 

Caching stores the result of CPU-intensive operations so the next execution returns a result from storage instead of performing the resource-heavy operation again. 

<!--- In the above example, the first request will always take 2 seconds, but the following requests will activate the cache and send a response in a few ms. --->

---

Performing and storing caching within middleware: if the route has been cached return this result, otherwise move on to the next middleware module. 

To run with "memory-cache" package

[npm memory-caching package](https://www.npmjs.com/package/memory-cache)

---

![Cached code](https://i.imgur.com/UGlim6t.png)

---

This looks for cached values using the request URL as the key. If found, it's sent directly as the response, if not, Express' send function is wrapped around to cache the response before sending to the client. 

PUT, DELETE + POST methods should not be cached! 

In general, the more high-use items you can cache the better performance will be. 

---

This example uses an npm module to cache content in memory (there are other npm caching modules that store content elsewhere)
- In-memory caching is the fastest available option
- Cached content is lost if the server/ process goes down
- Cached content not shared between multiple node.js processes 

---


## Non-caching environment methods 

### NODE_ENV :deciduous_tree: 
Express can run in several modes. By default, it presumes development.

---

`export NODE_ENV="production"` makes express:
- Cache view templates
- Cache CSS files generated from CSS extensions
- Generate less wordy error messages
- Ultimately, increase efficiency by *three times*


---

### Automatic app restart :christmas_tree: 
A node app will crash if it encounters an uncaught exception. 
In production the app will need to restart if either the full app or the server crashes
- Use a process manager to restart app and Node after crashes
    - Popular PMs: StrongLoop Process Manager, PM2, Forever
- Use init sytem to restart the process manager when the OS crashes 
    - Popular ISs: systemd, Upstart

---

### Load balancing :palm_tree:

A load balancer takes HTTP requests and forwards these to one of a collection of servers. Load balancers are usually used for performance purposes: if a server needs to do a lot of work for each request, one server might not be enough, so 2 servers alternating will help.

```javascript=
server1.listen(3000);
server2.listen(3001);
```

---

## Questions anyone??

![](https://media.giphy.com/media/26uf9wbBnV2eppZ4c/giphy.gif)

---

## Reference links

Make express more efficient
- https://www.sitepoint.com/5-easy-performance-tweaks-node-js-express/
- http://mrbool.com/optimizing-performance-in-express-js/34368

Don't use sync code
- https://expressjs.com/en/advanced/best-practice-performance.html#dont-use-synchronous-functions

Don't use console.log for debugging
- https://peterlyons.com/js-debug/
- https://hackernoon.com/please-stop-using-console-log-its-broken-b5d7d396cf15

Middleware best practice
- https://www.moesif.com/blog/engineering/middleware/What-Is-HTTP-Middleware/
