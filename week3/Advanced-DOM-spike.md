## Advanced DOM
### Using advanced DOM features to make rendering complex UIs easier

![Cinderella](https://media.giphy.com/media/Y47IU6pqyrn1tsPivl/giphy.gif)

---

### What is a `NodeList`? 

![nodes](https://media.giphy.com/media/fw8uZriJW4TlhmZnUj/giphy.gif =300x)

An object consisting of a list of all nodes in a page.

---

### DOM Tree Diagram `NodeList` 🌳

This is how a `NodeList` looks as DOM tree (a visual representation of the DOM):

![NodeList](https://www.w3schools.com/xml/nodelist.gif)

---

### `NodeList` in the Console 

![NodeList](https://i.stack.imgur.com/DPklJ.png)


---

### Live vs. Static `NodeList`s
We're able to use these both types of `NodeList` to manipulate the DOM, so be mindful of when you create the collection / object.

---

### Live `NodeList` ⚡️
- Changes in the DOM automatically update the collection when elements in the collection are updated.
- `Nodes.childNodes` is a live `NodeList`.
- Cathedral Marauder's Map ⛪️

---

### Static `NodeList` 🎈
- A "snapshot" of the DOM when you run the DOM access method, changes in the DOM do not affect the content of the collection.
- `querySelectorAll()` returns a static `NodeList`.
- Cathedral blueprint ⛪️

---

### `NodeList` isn't an array...yet! 🤯


NodeList is an object that you can interact with iteratively using `for()` methods e.g. `forEach()`. 

```javascript
const list = document.querySelectorAll('input[type=checkbox]');
for (let checkbox of list) {
  checkbox.checked = true;
}
```

It could be more helpful as an array; we can do this with `Array.from(NodeList)`.

---

### How is it different from an `HTMLCollection`?

Both `HTMLCollections` and `NodeLists` are collections.

![collection](https://media.giphy.com/media/pMiiPGLp5dzkk/giphy.gif)

---

### `HTMLCollection` 
- Node elements
- Always a live representation of the elements' presence in the DOM

---

### `NodeList` 
- All node types (including elements, but also attributes, text, comments, and so on...)
- A list of nodes that may or may not be in the DOM.

---

## Fragments and templates

![tesselate](https://media.giphy.com/media/4NveYsodRtoPuUe6o2/giphy.gif =300x)

---

### What is the `<template>` element?

The template element isn't rendered until activated in the script.


```HTML
<template id="myTemplate">
  <img src="" alt="great image">
  <p class="comment"></p>
</template>
```

---


### The basics 
Wrapping content in a `<template>` gives us few important properties.

- Its content is effectively inert until activated. Essentially, your markup is hidden DOM and does not render.

---

- Any content within a template won't have side effects. Script doesn't run, images don't load, audio doesn't play ...until the template is used.

- Content is considered not to be in the document. Using `document.getElementById()` or `querySelector()` in the main page won't return child nodes of a template.

---

- Templates can be placed anywhere inside of `<head>`, `<body>`, or `<frameset>` and can contain any type of content which is allowed in those elements. Note that "anywhere" means that `<template>` can safely be used in places that the HTML parser disallows...all but content model children. It can also be placed as a child of `<table>` or `<select>`.

---

### Activating a template 🏁

![activate](https://media.giphy.com/media/xT5LMADLN3zGz4Y2VG/giphy.gif)

To use a template, you need to activate it. Otherwise its content will never render. 

We create a copy of the templates content. 

---

```JavaScript
var tmpl = document.getElementById('comment-template');
document.body.appendChild(tmpl.content.cloneNode(true));
```

Using the cloneNode method we then append it to the doccument.body in order for it to go live.
`cloneNode(true)` <- clones nodes, attributes and descendants
`cloneNode(false)` <- clones only node and attributes

---

### Document Fragment 

- Document fragments are faster than a single DOM node injection.

- We could use use this to add multiple list items 

---

```HTML
<ul id="list"></ul>
```

```JavaScript
var frag = document.createDocumentFragment();
    for(let i.....) {
        let li = document.createElement("li");
        li.textContent = "List item " + x;
        frag.appendChild(li);
      //listNode.appendChild(li);
    }
    listNode.appendChild(frag);
```

---

### To Do List Example ☑️

How can we use these to render dynamic UI?

- Create a template of a to do entry which includes:
  - a checkbox
  - Image
  - text input


---

You could include a button which copies the content of the template.

Appends these copies to a document fragment which is then added to the UI. 
