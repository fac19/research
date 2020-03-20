---



---

## Basic selectors

![](https://media.giphy.com/media/2WNQ0N41BK5Us/giphy.gif)
  - Universal selector for all elements: ``` * { background: red; }```
  - A nodename: ```p { background: red; }```
  - Class selector: ```.box { background: red; }```
  - id selector: ```#carousel { background: red; }```
  - attribute selector: 
  
  ```css
  [type="text"] { background: red; }
  /* or */ 
  [submit] { background: red; } 
  ```

---

## Groups

You can _group_ selectors with a comma i.e. apply the same css rules to several selectors.

For example, with the following rule all ```<a>``` AND all ```<p>``` elements would get a red background, unless a more specific rule overrides this one.

```css
p, a { background: red; }   
```

---

## Combinator selectors

#### You can use combinators to chain selectors, making your CSS rules more specific (i.e. giving them higher precedence).

![](https://media.giphy.com/media/5FyJHOI62Bwu4/giphy.gif)

There are five combinators:

| combinator | syntax |
| ----- | ------ |
|descendant  | a b {}  |
| child | a > b {}|
|general sibling  | a ~ b  {} |
|adjacent sibling |  a + b {} |
|column |  a \|\| b {}|

They all use information from the left hand side to make the right hand side more specific - they do not select the left hand side.

The column combinator is for using the HTML table element and probably isn't worth focussing on.

The others work for any kind of element. They take advantage of HTML's tree-like structure to increase specificity. Let's see an example. 

---

### Example: the descendant selector

The most common combinator is probably the descendant combinator, which uses a space. 

```
a b {}
```

The right-hand side should be a descendant of the left hand side.

![](https://media.giphy.com/media/eK1wEASXgQTYs/giphy.gif)

---

HTML
```htmlembedded
  <div class="outer">
    <div class="inner">
      <h1>A title</h1>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit sapiente dicta suscipit voluptates incidunt iste alias quidem facilis aliquid perferendis, delectus magnam nemo nulla qui aperiam eligendi veritatis. Perferendis, ipsa!</p>
    </div>
  </div>
```

CSS
```css
* {
  background-color: grey;
}

.outer p {
  background-color: pink;
  color: green;
}

p {
  background-color: black;
  color: black;
}
```



![](https://i.imgur.com/RHVc7z5.png)

The p content is readable because the rule with the descendant combinator is more specific than the one that only has an element selector.

---

### You can also require _two_ selectors - kind of like && in JavaScript

```css
.dog.cat {
  background: red;
}
```

This rule applies to all elements that have **both** a dog and a cat class.

![](https://media.giphy.com/media/3ohzdMDbNXvnWdeOZi/giphy.gif =300x)

---

### The owl selector



You can use the adjacent child combinator (+) with the universal selector to make the owl:

```css
* + * { background: red;}
```

![](https://media.giphy.com/media/EdRgVzb2X3iJW/giphy.gif)

The adjacent child combinator selects the right-hand-side only if it is next to the element in HTML that is on the left in CSS. 

```css
img + p {
    /* every p element directly after an img element (which is a sibling) */
}
```


Therefore, the owl selector selects every html element with a sibling that comes before it. Everything which is __not__ a first child.

```css
* + * {
  margin-top: 1rem;
}
```

This adds a small margin on top of every element other than those elements which are the first children of their parent. 

If you want to be more specific, you could add another combinator, for instance the child combinator:

![](https://i.imgur.com/kC4A8zw.png)
```htmlembedded=
<h1>A title</h1>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit sapiente dicta suscipit voluptates incidunt iste alias quidem facilis aliquid perferendis, delectus magnam nemo nulla qui aperiam eligendi veritatis. Perferendis, ipsa!</p>
 <div class="owl-parent">
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptates, aut dolores alias provident qui illo officia iure dolor vitae autem repellendus dignissimos quidem obcaecati ipsum maxime ad fuga optio ipsam?</p>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptates, aut dolores alias provident qui illo officia iure dolor vitae autem repellendus dignissimos quidem obcaecati ipsum maxime ad fuga optio ipsam?</p>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptates, aut dolores alias provident qui illo officia iure dolor vitae autem repellendus dignissimos quidem obcaecati ipsum maxime ad fuga optio ipsam?</p>
  </div>
```



```css
.owl-parent > * + * {
  margin: 0;
  margin-top: 40px;

}

.owl-parent {
  background-color: pink;
}
```



![](https://media.giphy.com/media/JEIRAmTTfUgYE/giphy.gif)
---

## Pseudo elements - what are they?

Pseudo elements are virtual elements that let you style something before, or within, a selected element e.g. the first line of a paragraph.

```css
    /* Makes the first line of all <p> elements red */
    p::first-line {
    color: red;
}
```

![](https://i.imgur.com/BgJSrYF.png =600x100)


They can affect the flow of the document, but are created from CSS. They are not part of the DOM as such.

![](https://media.giphy.com/media/xUNda50uvXldMGE2Aw/giphy.gif)

---

In CSS3 pseudo elements are usually denoted by two colons — for example, ::first-line — to differentiate them from pseudo-classes which only use one colon e.g. a:visited.

```css
    /* CSS 2 syntax */
    selector:pseudo-element {
        property: value;
    }
```

```css
    /* CSS 3 syntax */
    selector::pseudo-element {
        property: value;
    }
```

---


### Other pseudo elements

| Element | What is does |
| ------- | ------------ |
|::cue | Style cue points in Web Video Text Tracks |
|::first-letter | Stlyes the first letter of the selected text element.|
|::first-line | Styles the first line of the selected text element.
|::placeholder | Style placeholder text in an input element|
|::selection | Style text that is selected in the browser|
::slotted()| Style things that have been slotted into an HTML template|

There are quite a few more but they are experimental or browser specific.


---

### ::before & ::after (was :before & :after)
These pseudo elements create a virtual element before the first child, or last child (respectively) of the selected element. You can add content to these elements and style them...
![](https://i.imgur.com/9yiMk8N.png)
![](https://i.imgur.com/dvmaAdV.png)
![](https://i.imgur.com/0V2rZGd.png)

---

Before and after pseudo elements initially take their position and dimensions from their parent. Their positions can then be adjusted by setting their position to absolute and using offset.

![](https://i.imgur.com/uPdn2MM.png =400x400)

---

```javascript=
 p::before {
      content: 'Before!';
      position: relative;
      display: block;
      height: 20px;
      width: 100%;
      background-color: blue;
  }
```

![](https://i.imgur.com/SZ6Mr6i.png)

![](https://i.imgur.com/gmzdOqc.png)



---

```javascript=
  input[type=checkbox]:checked + label::after {
    top: .4em;
    left: .7em;
    width: .4em;
    height: .8em;
    border-right: .25em solid #00f;
    border-bottom: .25em solid #00f;
    transform: rotate(45deg);
  }

  input[type=checkbox] + label::before {
    content: '';
    background: #fff;
    border: .1em solid rgba(0, 0, 0, .75);
    background-color: rgba(255, 255, 255, .8);
    display: block;
    box-sizing: border-box;
    float: left;
    width: 1em;
    height: 1em;
    margin-left: -1.5em;
    margin-top: .15em;
    vertical-align: top;
    cursor: pointer;
    text-align: center;
    transition: all .1s ease-out;
  } 
```

![](https://i.imgur.com/5mgU9Ho.png)


---

![](https://i.imgur.com/NGZKmlS.jpg =400x300)
![](https://i.imgur.com/Ip2WXLn.png =500x300)


---

## :focus (e.g. when tabbed on)

```javascript=
 input[type=checkbox]:focus + label {
    color: #00f;
    outline: 1px dotted #00f;
  }
```

![](https://i.imgur.com/v8dHftm.png)



---

## :disabled

```javascript=
input[type=checkbox]:disabled + label {
    color: #ccc;
  }

  input[type=checkbox]:disabled + label::before {
    border: .1em solid rgba(0, 0, 0, .1);
    background-color: rgba(0, 0, 0, .1);
  }
```

![](https://i.imgur.com/oKIoJPP.png)


---


# The Stack 

- Problem: In most styling we style only the elements we want to, and it doesn't effect the other elements on the page (e.g. background color). However some properties like "margin" is a property of the relationship between two nearby elements, therfore more unpredictable. 

e.g. 

![](https://every-layout.dev/images/illustrations/stack_padding_issue.svg)

(Padding of parent element is combined with margin)


