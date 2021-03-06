# ES modules
![](https://media.giphy.com/media/3o85xDazgkTMedOX8A/giphy.gif)

---

### Questions to consider
- What are the different ways we can import/export code? 
- What does "dynamic import" do?
- Why might using hundreds of small modules in the browser cause performance problems?

---

### Why should we use modules? (c)
- Ensures DRY code
- Separates the modules to make debugging easier and avoid unexpected behaviour.

---

### Boris Analogy (c)

![Boris browser needs to solve problem](https://media.giphy.com/media/VEVzz4VZVsXNioYt5T/giphy.gif )

---

![How to get Brexit done](https://media.giphy.com/media/JQdMxVDuwqpLezoLlE/giphy.gif)

---

### Michael Gove module

![Michael Gove module](https://media.giphy.com/media/Y0DUJbOsJPWHg8GWUG/giphy.gif)

---

![Has the Brexit function to give Boris](https://media.giphy.com/media/YWUpVw86AtIbe/giphy.gif )

---

![Happy Boris](https://media.giphy.com/media/8HZmQNESCZKJG/giphy.gif)

---

### What are the different ways we can import/export code? (L)

- To import code, you have named imports and namespace imports
- For exports, there's named exports and default exports

---

### Namespace imports (L)
- This is a type of static module
- Another alternative to named imports
- Namespace importing turns the module into an object
-  Its respective properties are the named exports

```javascript=
import * as myModule from '/modules/my-module.js';

myModule.doAllTheAmazingThings();
```

---

### What are the downsides of static modules? (L)

- Slows the loading of your code
- Can increase your program's memory usage
- As a rule of thumb, it's good to use to static imports over dynamic imports as you can download initial dependencies


---

### What does "dynamic import" do? (G)

- The usual way to import a module is statically -> module called once the page has loaded
- There may be instances where you want to load a module conditionally
--> Dynamic imports!

---


-> `import` keyword called as a function
-> It returns a :heart: promise.

```javascript=1
    import('/modules/my-module.js')
      .then((module) => {
        // Do something with the module.
      });
```

---

Also supports `await`:

```javascript=1
    let module = await import('/modules/my-module.js');
```

---

### Default exports (G)

- Usually used when a module  contains a single function or a single [class](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes).

```javascript=100
export default strFunction
```

```javascript=1
// inline
export default str => str.toUpperCase()
```
- Avoid mixing named exports and default exports

---

#### Why might using hundreds of small modules in the browser cause performance problems?

![](https://2r4s9p1yi1fa2jd7j43zph8r-wpengine.netdna-ssl.com/files/2018/03/10_construction.png)

---

- Require Vs Import 
- We would have to go through the tree layer-by-layer finding and loading all of the dependencies.
- For larger projects we should dynamically import to help with browser performance!

---

## Resources
- [MDN JavaScript import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)
- [Dynamic imports](https://javascript.info/modules-dynamic-imports)
- [MDN JavaScript exports](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)
- [ES modules: A cartoon deep-dive](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/)

---

## Questions?

![](https://thumbs.gfycat.com/GroundedOblongDuiker-size_restricted.gif)
