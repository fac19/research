### What is the difference between accessible and inclusive?

---

+ Inclusive design is about providing the best possible experience to the broadest range of users. Semantic HTML helps technologies and therefore users understand content on the web.


---

+ Accessibility concerns the structures and containers that hold your information and the way that your information is formatted and presented. Inclusivity lives or dies based on the information itself, and on your understanding and empathy with your audience. 

---

### Who does semantic HTML benefit?

When learning about accessibility, it helps to have an understanding of the diverse range of users in the world and the kinds of accessibility topics that affect them.

There are four broad categories of impairements: 
+ Visual, motor, hearing, and cognitive


---

### Visual impairments 

Using schemantic html allows screen readers and other assistive technologies to communicate elements properly to the user.

Using Semantic form elements can convey if a check box has been checked.


---

### Effective high-contrast options

![](https://i.imgur.com/dyxXrJC.png)

---

#### Visual bad example
![](https://i.imgur.com/OP9u69S.png)

---

#### Visual better example
![](https://i.imgur.com/QVx9rIk.png)

---

#### Using different textures
Using different textures can help distinguish for people with visual impairments (e.g. colour blindness)
![](https://i.imgur.com/DEOqvoJ.png)

![](https://i.imgur.com/5xW1X3P.png)

---

### Motor Impairments

+ Keyboard-only navigation is also aided by semantic HTML.

+ For instance, option menus and navigation can be very fiddly if you need to use a mouse to hover a menu open and move to select the desired item at the same time. 

+ Instead of using a drop down menu a multiple choice button would be better for someone using keyboard navigation.

---

### Poor use of spacing + small buttons:
![](https://i.imgur.com/3Mx87pL.png)

---

### Better spacing + larger buttons:
![](https://i.imgur.com/QVx9rIk.png)

---

### Hearing impairments

+ Avoid requiring audio to interact with the web application.
+ Add captions to all video content.
+ Create text transcripts for audio content.
+ Make sure your content is keyboard accessible: deaf-blind users can use screen readers that covert text to Braille on refreshable Braille devices.

---

Adding keypress methods in JavaScript (keyboard accessability)

![](https://i.imgur.com/de909xW.png)

---

### Cognitive impairments

+ Allow fonts to be enlarged.
+ Use real text or vector-based text, rather than text within raster-based images, to allow for higher quality enlargement, without pixilation.
+ Provide all content in a text format so that it can be read aloud by text-to-speech synthesizers.

---

#### Using rem units instead of px
![](https://i.imgur.com/1esg1FQ.png)

---

### How does ARIA relate to HTML?

ARIA is a set of attributes you can add to HTML elements that define ways to make web content and applications accessible to users with disabilities who use assistive technologies (AT). 

ARIA tags are helpful when JavaScript is used. An example could be an interactive toggle button. 

```
<button aria-expanded="false">Toggle content</button>
<div hidden>Some content</div>
```

---

+ A visually-impaired user with a screen reader, however, usually relies on spoken cues as they navigate through an interface. But when a screen reader focuses on the button, there’s nothing to tell it if the content is currently in view and needs to be read.

+ When accessibility issues cannot be managed with native HTML, ARIA can help bridge those gaps.

---
