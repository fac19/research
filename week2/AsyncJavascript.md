
# A'sync (Javascript)

![](https://s1.r29static.com/bin/entry/17f/720x864,85/1946653/image.webp)

---

## Call stacks 

- JS is a single-threaded programming language (only 1 call stack)

- A call stack records where in the program we are. (e.g. function)

![](https://image.slidesharecdn.com/sonlejs-event-loop-160805060652/95/javascript-event-loop-13-638.jpg?cb=1470377352)

---

# Problems

## Blocking Code! 

is code which prevents the execution of further code until that chunk of code finishes.

![](https://media.giphy.com/media/3osxYACfOYULLSpNjG/giphy.gif)


### Code Example:
- E.g. huge for/while loops which block user from interacting with the browser.

---
# What is Async? 

- Sync = single lane country road where nobody can overtake.

![](https://media.giphy.com/media/xT5LMuHy92KbOfnd8A/giphy.gif)

---

- Async = motorway which initially only has one lane BUT drivers (e.g functions) can add their own lanes (using promises and callbacks).


![](https://www.phpmind.com/blog/wp-content/uploads/2017/05/synchronous-asynchronous-javascript.png)

---
## Async Keyword

### Code Example:

```javascript=
async function f() {
  return Promise.resolve(1);
}

f().then(alert); // 1
```

---

## Callbacks 
- Callbacks allow us to do something after something else has occurred 

- A callback is a function that is a parameter of another function 

- So callback function running depends entirely on whether or not something else happens 

- Passing a function into another function and the function that we passed in is called back, executed after something else has occurred 

---

An example of an async callback is the second parameter of the addEventListener():

```javascript=
btn.addEventListener('click', () => {
  alert('You clicked me!');
  });
```

setTimeout(callback, 1000) 

---

## Promises

![](https://gifimage.net/wp-content/uploads/2018/04/pinky-promise-gif-5.gif)

---

## Promises

- A style of **async** code used in modern Web APIs
- A promise is a **placeholder** that is expected to change to a **successful** result  or reason for **failure**.
- Promises (and all async ops) are put into an event queue, which runs after the main thread has finished processing. 
- The queued operations will complete as soon as possible then return their results to the JavaScript environment.

---

![](https://i.imgur.com/EwFRh16.jpg)

---

## Event Loop 

The event loop is a process that runs endlessly and whose only job is to monitor and transfer methods to the call stack from the event queue.

![](https://miro.medium.com/max/572/1*1zNMKZB4Tuoy68x9MoCl8A.png)

---

## Example code

---

## Questions we don't know the answer to

- What is the right time to use Async?
- Can Async be overused (e.g. having too many threads running simultaneusly may overwork the cpu)? 
- 

---

# Conclusion
- **JavaScript is a synchronous**, blocking, single-threaded language, in which only one operation can be in progress at a time.

- Async lets your code do several things at the same time without stopping or blocking your main thread

- Whether we want to run code synchronously or asynchronously will depend on what we're trying to do.

___

## References: 
- https://github.com/getify/You-Dont-Know-JS/tree/2nd-ed/sync-async  (nice book on Async)
- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Concepts
- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Introducing
- https://2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html
- https://stackify.com/when-to-use-asynchronous-programming/

Nice links provided by Ivo:
- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous
- https://www.youtube.com/watch?v=8aGhZQkoFbQ
- https://blog.bitsrc.io/understanding-asynchronous-javascript-the-event-loop-74cd408419ff
