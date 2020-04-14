# CORS - Cross Origin Resource Sharing - Week-7-Spike

:bear: :whale: :bird: :cat: 

![](https://media.giphy.com/media/TIyJGNK325XGciFEnI/giphy.gif)

---

## We're going to talk about :bear: 
1. What is CORS?
2. Why would it be dangerous for browsers to allow arbitrary cross-origin requests?
3. How can we configure our server to allow requests from a specific different domain?

---

### What is an 'origin'? :whale:

![](https://i.imgur.com/cM1j7WY.png)

[More on ports](https://en.wikipedia.org/wiki/Port_(computer_networking))

---

 
### What is CORS?  :bird:

- CORS policies, or **Cross--Origin-Resource-Sharing** policies, are implemented as a security measure. 
- A CORS policy determines what origins other than your own can access the data at your origin.

---

### CORS vs. SOP :bird: 
- Same Origin Policy means you can only access resources from the same origin as you
- It is enabled by default
- Cross-origin-policies let you relax the same-origin-policy

---

### Donald Trump analogy :cat: 

![white house](https://cdn.arstechnica.net/wp-content/uploads/2019/10/GettyImages-1063284214.jpg)

---

![donald wants pizza](https://media.giphy.com/media/l3vRgKqw8Pzwmb62A/giphy.gif =600x)

---

![kitchens](https://media.giphy.com/media/demgpwJ6rs2DS/giphy.gif =600x)

---

![white house security](https://media.giphy.com/media/5eFRKTq4uUeHe1czA5/giphy.gif =600x)

---

![donald gets pizza](https://media.giphy.com/media/gOkl3JJ50kTDO/giphy.gif =600x)

---

### Why would it be dangerous to allow arbitrary cross-origin requests? :cat: 

- We don't want to let just anyone into the White House!
- Without same-origin-policy, one browser window could use the privileges the user had enabled in another and use presidential powers for nefarious purposes.
- Most servers will allow GET requests but may block requests to modify resources on the server. 

---

## When would I use CORS? :bear: 

1. You've built an API and hosted it at your-domain.com/api
2. An application on another-domain.com wants data from your API
3. The request will FAIL because domains are protected by Same Origin Policy which is very restrictive
4. To address this you use CORS

---

The standard adds some headers, including:
1. **Origin** for requests
2. **Access-Control-Allow-Origin (ACAO)** for responses

---

## Example :bear: 

The website http://www.hotapps.com is the app. When it makes a request to your API, the Origin header contains this website's fully qualified domain name (FQDN):

```javascript=
// Origin
GET /api/foo HTTP/1.1
Origin: http://www.hotapps.com
```

---

If you want this request to succeed, your API needs to send back an Access-Control-Allow-Origin header in its response:

```javascript=
ACAO
HTTP/1.1 200 OK
Access-Control-Allow-Origin: http://www.hotapps.com
```

- If the link in the response didn't match the origin in the request, the browser would receive this information, but not use it.
- a possible value for the response is *

---

## Request: :whale:
There are two types of CORS request
- Simple...
- Pre-flight...

[read more](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

---

### Simple Requests :whale:


![](https://media.giphy.com/media/l3q2TGhB8qZhs1tny/giphy.gif)

---

### Pre-flight requests :whale::cat: 

- Checks to see whether or not the original request is safe 

![](https://kevhuang.com/content/images/2015/04/cors-timeline.png)

---

Options request
```
OPTIONS /image/ HTTP/1.1  
Accept: text/html,application/xhtml+xml,application/xml;
Access-Control-Request-Method: DELETE
Access-Control-Request-Headers: accept, content-type  
Origin: https://funnyimages.com  
```

Options response
```
HTTP/1.1 200 OK  
Access-Control-Allow-Origin: *  
Access-Control-Allow-Methods: GET,PUT,POST,DELETE  
Access-Control-Allow-Headers: Content-Type, Accept  
```

---

### Allowing requests
- Can be done in vanilla Node
- express has a ```cors``` package


---

### Express example 1: allowing all requests :bird: 

```$ npm install cors```

```javascript=1
var express = require('express')
var cors = require('cors')
var app = express()

app.use(cors())

app.get('/products/:id', function (req, res, next) {
  res.json({msg: 'This is CORS-enabled for all origins!'})
})

app.listen(80, function () {
  console.log('CORS-enabled web server listening on port 80')
})

```

---

### Express example 2: allowing specific requests :bird: 

```javascript=1
var express = require('express')
var cors = require('cors')
var app = express()

app.get('/products/:id', cors(), function (req, res, next) {
  res.json({msg: 'This is CORS-enabled for a Single Route'})
})

app.listen(80, function () {
  console.log('CORS-enabled web server listening on port 80')
})

```

---

### So why is it needed? :whale: [Meow]
>The CORS standard is needed because it allows servers to specify not just who can access its assets, but also how the assets can be accessed.

---


## Resources

[Allowing requests from other domains](https://apigility.org/documentation/recipes/allowing-request-from-other-domains)
[What is CORS](https://www.codecademy.com/articles/what-is-cors)

There are useful cors examples in the express docs
https://expressjs.com/en/resources/middleware/cors.html

---

### Any Questions?

![](https://media.giphy.com/media/U44jsTIBBkmya4fFI2/giphy.gif)



