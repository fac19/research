# Debugging JavaScript

![](https://media.giphy.com/media/Rkis28kMJd1aE/giphy.gif)


---



How would you effectively find out where (and why) an error is occurring in your JavaScript code

![](https://media.giphy.com/media/rMS1sUPhv95f2/giphy.gif)


---

 🤯 Command+Option+I (Mac) or Control+Shift+I (Windows, Linux) or control+shift+J for console🤯 

![](https://i.imgur.com/aD4PZD8.png)


---

##  🤠General tips🤠
- If something isn't working, check if there's an error, and if there is, read the error
- You can manipulate DOM elements in your browser console to test out JavaScript
- Turbo Console Log - a VSCode plug-in that enables you to quickly introduce and comment out console.log()

---

## Console methods

+ console.log(...); //log a message or an object to console

![](https://media.giphy.com/media/m8DnDYfRwEtvG/giphy.gif]

---


### What other console methods are there?

+ console.info(...); //same as console log
+ console.warn(...); //outputs a warning ⚠️
+ console.error(...); //outputs an error ❌

```JavaScript=1
function testError() {
    console.error('error');
    console.warn('a warning - not interrupted by the error');
    console.log('this is still logged');
}
```

---

![](https://i.imgur.com/RmGauVt.png)


---

Which ones are useful?

+ console.assert(expression, message)👇
The method is used to run simple assertion tests. It takes two required arguments:
 
  + expression: A boolean expression.
  + message: A string or an object which is written to the console.

```JavaScript=1
console.assert(false, “Log me!”)
console.assert('one' === 1, "NOT TRUE ONE IS A STRING!" )
```

---

+ console.table(array)

This particular method is incredibly useful to describe an object or array content in a human-friendly table:

```JavaScript=1
let arr = ['apples', 'oranges', 'pears']
console.table(arr)
       🍏 🍊 🍐
┌─────────┬───────────┐
│ (index) │  Values   │
├─────────┼───────────┤
│    0    │ 'apples'  │
│    1    │ 'oranges' │
│    2    │  'pears'  │
└─────────┴───────────┘
```

---

```JavaScript=420
let otherArr = [['apples', 'oranges', 'pears'], ['carrots', 'celery'], ['tea', 'juice', 'ayran']]
console.table(otherArr)

┌─────────┬───────────┬───────────┬─────────┐
│ (index) │     0     │     1     │    2    │
├─────────┼───────────┼───────────┼─────────┤
│    0    │ 'apples'  │ 'oranges' │ 'pears' │
│    1    │ 'carrots' │ 'celery'  │         │
│    2    │   'tea'   │  'juice'  │ 'ayran' │
└─────────┴───────────┴───────────┴─────────┘

```

---

+ console.group & console.groupEnd() 
```Javascript=1
console.group('Javascript Debugging Spike')
console.log("James")
console.log("Hettie")
console.log("Ivo")
console.log("Cambell")
console.groupEnd()
```

![](https://i.imgur.com/JQRfgij.png)


---

+ console.time() & console.timeEnd()


```JavaScript=1
function usainBolt(metres) {
  let milisecondsPerMetre = 81.4;
  console.time('usainsSpeed');
  
  setTimeout(() => {
    console.timeEnd('usainsSpeed');
  }, metres * milisecondsPerMetre);
  
}

usainBolt(100)
```

After ~8.5 seconds this logs

```JavaScript=1
usainsSpeed: 8441.379638671875ms
```

This isn't how long Usain Bolt actually takes but whatever

---

## Debugger

![](https://media.giphy.com/media/3o6nUPPGvsKSiNqvNC/giphy.gif)

---

+ including the line
```
debugger;
```
Halts the JavaScript code and calls the debugger function (if available).

+ When the debugger statement is called, execution of the code is paused/ breaks at the debugger statement. It is like a breakpoint in the script source.


---

```JavaScript1
let a = a;
let b = b;
a = b; 
let c = b; 
debugger;
console.log(c);
```
+ Opens the debugger menu and shows you what the variables are
+ This is useful if you want to debug some code that runs as soon as you load a page


---

### Debugger in the browser

![](https://i.imgur.com/CvK6KyS.png)

---

- Step Over - Execute next function and break after
- Step Into - Next function call and break
- Step Out - Finish function and break after
- Labels - Self-defined breakpoint
- Things to remember - Watch, scope, deactivate breakpoints

---

![](https://i.imgur.com/qPAOBsU.png)


---
