# Browser Rendering

![loading](https://media.giphy.com/media/5UH4hjSciuic5W9ZFo/giphy.gif)

---

>The Critical Rendering Path is the sequence of steps the browser goes through to convert the HTML, CSS, and JavaScript into pixels on the screen.
>~ MDN

---

![sequence](https://bitsofco.de/content/images/2017/01/CRP-Sequence-Copy.png)

---

![devtools](https://i.imgur.com/TrR4nd2.png =500x)

---

## 1. GET index.html

```html
<head>
  <link rel="stylesheet" type="text/css" href="style.css">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Example</title>
</head>
<body>
  <h1>Hello World</h1>
<script src="main.js"></script>
</body>
```

---

## 2. Read HTML and GET style.css and main.js

```css
body {
  font-size: 1rem;
}
h1 {
  color: pink;
}
```

```javascript
alert("JavaScript is running on this page!");
```

---

### DOM Tree

![](https://i.imgur.com/rBDHD0C.png)


An Object representation of the fully parsed HTML page, with element and text nodes.

---

## 3. Read CSS Object Model created from style.css

---

### CSSOM (CSS Object Model) Tree

![](https://i.imgur.com/gl4M4wF.png)

An Object representation of the nodes and their associated styles.

---

## 4. Run JS scripts

---

### The Render Tree

![tree](https://i.imgur.com/5rAO0FQ.png)

An Object representation of what is rendered on the page. 

Hidden elements, i.e. elements styled with `display: none` are not included.

---

## 5. Generate layout using meta viewport tag
```htmlembedded
<meta name="viewport" content="width=device-width,initial-scale=1">
```

---

## 6. Paint pixels on document

![painting](https://media.giphy.com/media/rYEAkYihZsyWs/giphy.gif)

---

![devtools](https://i.imgur.com/TrR4nd2.png =500x)

---

## But wait!
![twist](https://media.giphy.com/media/9AIdwh5YqwUF6uvIgJ/giphy.gif)

---

## Render blocking

![](https://media.giphy.com/media/vzE7csLWN3uRW/giphy.gif)

---

### What are "render blocking" resources

- Those that must finish downloading or running before another resource can run.
- CSS blocks Javascript and construction of the render tree.
- JS blocks the HTML parser, stopping rendering until it has been downloaded and run.

---

### General techniques

- Download speed - Less is more
- Compression & minification,
- CDN

---

### Avoiding CSS blocking
- Use fewer CSS files by combining
- Write tight CSS
- Inline CSS when possible
- Never import CSS with @import, always use link
- Label things like print CSS
- `<link href="print.css" rel="stylesheet" media="print">`
- Lazy load less important CSS

---

### Avoiding JS blocking
- Traditionally `<script>` tags are included at the end of the HTML so as not to block the HTML parser.
- Downside is .js files only start downloading after parsing.
- JS loaded with `async` only blocks the HTML parser if the script comes back before it is done rendering.
- JS loaded with `defer` won't block the HTML parser.

---

## Asynchronous and Deferred Javascript
What do the async and defer keywords do?
- Boolean attributes with similar usage
- Async > defer on modern browsers
- Not all older browsers support async
``` HTML
<script async src="script.js"></script>
<script defer src="script.js"></script>
```
- Used when defining script in the head, rather than the body

---

### Current execution (at end of body)
![No defer or async](https://i.imgur.com/EuXtTAJ.png)

---

### Async
![Async loading](https://i.imgur.com/zLFDIfn.png)

---

### Defer
![Defer loading](https://i.imgur.com/CkrMj9L.png)

---

### Page Loading
domLoading: timestamp start of HTML loading.
domInteractive = HTML loaded + parsed, DOM built.
domContentLoaded = DOM ready, construct render tree
domComplete = all processing complete, everything loaded + parsed
onLoad = event to trigger additional application logic. 
> If you want to ensure there is no render blocking, you should make sure scripts are run after the onLoad event. 

---
    
### So which is best? 
```async``` scripts are executed in a casual order, useful for analytics
```defer``` scripts are executed in the order in which they are defined, useful when certain scripts depend on others.

--- 

## Reference

[The critical rendering path](https://bitsofco.de/understanding-the-critical-rendering-path/)

[Async & defer](https://flaviocopes.com/javascript-async-defer/)

[MDN](https://developer.mozilla.org/en-US/docs/Web/Performance/Critical_rendering_path)
