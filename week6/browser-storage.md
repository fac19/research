# Week6 Spike- Browser storage

![](https://media.giphy.com/media/N35rW3vRNeaDC/giphy.gif)

---

## What's the difference:small_red_triangle: between local storage, session storage and cookies? 

![](https://media.giphy.com/media/a5viI92PAF89q/giphy.gif =300x)

---

![](https://i.imgur.com/8Eak2Kw.png)

---

#### Local storage

- Persists data even when the browser is closed and reopened.
- Stores data with no expiration date, and gets cleared only through JavaScript, or clearing the Browser Cache / Locally Stored Data. 
- Largest storage limit amonst the three.


---

#### Session storage

- Stores data only for a session, meaning that the data is stored until the browser (or tab) is closed.
- Data is never transferred to the server.
- Storage limit is larger than a cookie (at most 5MB).

---

#### Cookies :cookie: 

- Access to the **_sever_** and local machine / browser
- Can set expire date 
- Great for authentication 
- can be used to customise the user session.
- cookies can be set, edited and read on the browser and server side

---

## What types of things would you store in each?

---

### localStorage and sessionStorage
- key-value pairs stored as string
- Great for non-sensitive data needed on client side (ex: preferences, scores in games). 
- the data stored here can easily be read or changed on the client side - not to store sensitive or security-related


---

### Cookies :cookie: 
- session cookies - stored in the browser's memory but only lasts till you end the session
- persistent cookies - stored by the browser even after you close the session 
- first party cookies - created by the site you're currently visting in the browser
- third party cookies - used to track ad traffic

---

## Where can we see what a web page has stored in our browser?

![](https://media.giphy.com/media/3orieUe6ejxSFxYCXe/giphy.gif =300x)

---

### Local Storage
![](https://i.imgur.com/YjGOne2.png)

---

### Session Storage
![](https://i.imgur.com/VDOCqQu.png)

---

### Cookies :cookie: 
![](https://i.imgur.com/5qSgTF9.png)

---

![](https://media.giphy.com/media/1ngQorBCDcUFy/giphy.gif =300x)
- Open the cookies!!!!! :open_file_folder: :cookie: 
- Different fields: Name, Value, Path, Max-age, Size, HTTP, Secure, same site. 
- Filter, 
- Edit, 
- Delete, 
- Delete all 

---

### The Cookies table
- **Name** The cookie's name
- **Value** The cookie's value
- **Domain** The hosts that are allowed to receive the cookie
- **Path** The URL that must exist in the requested URL in order to send the Cookie header
- **Expires / Max-Age** The cookie's expiration date or maximum age

---

- **Size** The cookie's size, in bytes
- **HTTP** If true, this field indicates that the cookie should only be used over HTTP, and JavaScript modification is not allowed
- **Secure** If true, this field indicates that the cookie can only be sent to the server over a secure, HTTPS connection
- **SameSite** Contains strict or lax if the cookie is using the SameSite attribute

---

### Resources

![](https://media.giphy.com/media/xT5LMGUxeK4KTqZG8g/giphy.gif =300x)

[Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API)
[View, Edit, And Delete Cookies With Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/storage/cookies)
[CodePen Example](https://codepen.io/beaucarnes/pen/KmeRMx)
[YouTube, cookies vs localStorage vs sessionStorage](https://www.youtube.com/watch?v=AwicscsvGLg)
[Local Storage And How To Use It On Websites](https://www.smashingmagazine.com/2010/10/local-storage-and-how-to-use-it/)
[WHATWG documentation: Web storage](https://html.spec.whatwg.org/multipage/webstorage.html)

---

## Qustions:question: 

![](https://media.giphy.com/media/kDfGTmnbS9Ljm9hnwq/giphy.gif)