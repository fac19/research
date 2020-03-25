
---

# Debugging HTML & CSS
How can we find out why our page doesn't look right?

![](https://media.giphy.com/media/10eJOwQ9BKrF72/giphy.gif)

---

## How can we see and edit what elements and styles are rendered to the page?

![](https://i.imgur.com/Gt1B1Ku.png)

---

![](https://i.imgur.com/XTRPf1Y.png)

---

![](https://i.imgur.com/fOw6Vdd.png)

---

![](https://i.imgur.com/2slnWXZ.png)

- Right-click the node you're working on and select Scroll into view. Your viewport scrolls back up and you will see the selected node on the screen.

___

![](https://i.imgur.com/H7PwCd6.png)    

- Edit the DOM on the fly and see how those changes affect the page. Double-click the content on the developer tool and work from there.

---

![](https://i.imgur.com/5cjg6nG.png)

---

![](https://i.imgur.com/6GAjl2U.png)

---

![](https://i.imgur.com/AQOQUlK.png)

### Copy JS path
1. Copy the JavaScript path to a node when you need to reference it in an automated test. 
2. Right-click the content in the DOM Tree and select Copy > Copy JS Path. A document.querySelector() expression that resolves to the node has been copied to your clipboard.

---

![](https://i.imgur.com/Tzwv6OX.png)

---

### Store as global variable

![](https://i.imgur.com/lZnCBqF.png)

If you need to refer back to a node many times, store it as a global variable.
1. Right-click the content in the DOM Tree and select Store as global variable. 
2. Type temp1 in the Console and then press Enter. The result of the expression shows that the variable evaluates to the node.

---

## How can we easily test how responsive our page is?

Chrome's dev-tools can simulate mobile screens with the "Device Toolbar"

![](https://i.imgur.com/e61HHS8.png)

---

The size of the simulated screens can be typed in manually or adjusted with the on screen handles.

![](https://i.imgur.com/CuAircG.png)

---

In this view's top right corner is an elipsis icon which gives you a menu with several options.

![](https://i.imgur.com/jqzoeJQ.png)

---

Selecting "Show Media Queries" gives you a graphical representation of where your breakpoints are and what their numeric values are. You can click to quickly swap between them.

![](https://i.imgur.com/dL8RGbv.png)

---

Chrome has a very large selection of devices that it knows the dimensions of. Spending a lot of time making device specific layout may be a design smell BUT, if you need to you can augment this list with your own entries...

![](https://i.imgur.com/BO8RNVQ.png)

---

### Viewing on your own mobile.
First make sure your phone is on the same wifi as your development machine. Then browse to it's local ip address + the port live server gives you...

Getting IP in Linux:
![](https://i.imgur.com/sQ2hdzX.png)
In Windows use IPCONFIG in the terminal. Sorry, probably no grep for you!

Getting port in VScode, bottom right hand corner:
![](https://i.imgur.com/GYx5i26.png)

Put this in your phone's browser...
![](https://i.imgur.com/erfAqIa.png)

---

### Viewing on thousands of real mobiles.

There are commercial services who allow you to test your designs on a very large number of real handsets. The free trials might be useful if you want to try your design on a popular phones you don't have.

https://www.browserstack.com/responsive

https://crossbrowsertesting.com

---
## How can we debug CSS grid and flexbox layouts?

---

