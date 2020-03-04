# CSS Layout

---

## The Box Model
* Every element in HTML essentially is a box.
* Each box consists of 4 layers:
  1. Margin 
  2. Border
  3. Padding
  4. Content

---

### Content Box
* The default setting for box-sizing in CSS.
* The sizing of an element is set independent of the margin, border and padding. The margin, border and padding are additional.
* For example, if the width property of an element is set to 100px, the content will be 100px, and the margin, border and padding will add to the overall width.

```
.example {
  box-sizing: content-box;
}
```

---

### Border Box
* The sizing of an element is set inclusive of the margin, border and padding.
* For example, if the width property of an element is set to 100px, the overall width of the element will be 100px including the border and padding, **but not the margin**.

```
.example {
  box-sizing: border-box;
}
```

---

### Example

You can find an example that illustrates both these box model methods [here](https://codepen.io/rogerheathcote/pen/XWbazBg).

---

&nbsp;

## The Display Property

---

### None
* The page is rendered as if the element does not exist, but the element is still technically loaded (this will affect load time).
* This is different to `visibility: hidden;` where a blank space would be left where the element would otherwise be.

```
.example {
  display: none;
}
```

---

### Block

Fills all available space in one direction, usually horizontally in languages read left to right.

```
.example {
  display: block;
}
```

---

### Inline

* If you think typographically: blocks elements are the paragraphs, inline elements are the words.
* Elements with the display property of inline, can go inside elements with the display property of block.
* If there are two inline elements they flow adjacently.

```
.example {
  display: inline;
}
```

---

### Inline-block

* A hybrid of the block and inline properties.
* It allows you to edit the height and width properties (unlike inline), but it doesn't insert a new line (like block does).

```
.example {
  display: inline-block;
}
```

---

### Flex
* A one-dimensional container that positions its children horizontally or vertically.
* It has sub-properites to control the positioning and size of the element's children.

```
.example {
  display: flex;
}
```

---

### Grid
* A two-dimensional container that can position its children horizontally and vertically.
* Gives you the ability to name grid areas.

```
.example {
  display: grid;
}
```

---

&nbsp;

## The Position Property

* Used as a tool to disrupt the normal flow of the page.
* Top, bottom, left and right properties (offset properties) are dependent on the position property.

---

### Static

* The default CSS position.
* Follows the flow of the rules dictated by the display property.
* Ignores the offset properties.

```
.example {
  position: static;
}
```

---

### Fixed 
* Relative to the viewport.
* Stays in the same place in the viewport when user scrolls.
* Positioned by offset properties.

```
.example {
  position: fixed;
}
```

---

### Sticky
* Based on the users scroll position.
* Toggles between relative and fixed.
* Positioned relative until it hits the given offset position within the viewport, then it turns to fixed and remains in the position that the offset was met.

```
.example {
  position: sticky;
}
```

---

### Relative
* Behaves like static unless offset properties are added.
* Positioned relative to current position in flow.
* Does not change surrounding layout, other content will not be adjusted to compensate for the gap left.

```
.example {
  position: relative;
}
```

---

### Absolute
* Positioned relative to the nearest positioned ancestor, ie parent element, which is set to anything except static.
* Changes the surrounding layout, the space left by the element will be filled.

```
.example {
  position: absolute;
}
```
