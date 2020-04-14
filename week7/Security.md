# Security Spike

---

### Questions:

1. What is CSP?

2. How can we implement CSP?

3. How to prevent a brute-force attack against our log in endpoint?

---

#### What is Content Security Policy? (CSP)

![](https://media.giphy.com/media/l46CtrZxECRP4j4mk/giphy.gif =600x)

---

- CSP is WC3 web standard. Up to v3 now.
- In practice it's a set of "directives" in a header
- These say where code can come from from
- The aim is to thwart XSS attacks

Specified in a header...

```javascript
    let headers = {
        "Content-Security-Policy" : 
        "script-src 'self' https://apis.google.com"
    }
```

---

Can also be set in the `<head>` section of your client side html, although this doesn't permit as wide a range of directives...

```html
<meta
    http-equiv="Content-Security-Policy"
    content="default-src https://cdn.example.net;
    child-src 'none';
    object-src 'none'"
>
```

In both cases the argument is a string of directives separated by semicolons.

---

### The directives...

![](https://media.giphy.com/media/giEftvZuPAiZQBphEI/giphy.gif)

There are a LOT of directives (about 20). They can do things like specify what are valid endpoints for form submission, origins that are allowed to serve web fonts, permitted sources for images etc.

---

### Important to note

Several things are disabled
by default when you use CSP

![](https://media.giphy.com/media/utmZFnsMhUHqU/giphy.gif =500x)

---

### No inline code at all!
    - So no code within`<script>` tags.
    - Only external files allowed...
      `<script src='index.js'></script>`
    - That includes CSS!
    - So no `<style>` blocks OR
    - Styles as an attribute `<html style="Nope!">`

---

### No eval of any kind
    - Eval was always evil anyway
    - Use JSON.parse to decode json!
    - That includes `new Function('let no="way"')`
    - No string arguments to setTimeout and setInterval

---

### How can we implement CSP and other useful security filtering?

---

### Tool: "Helmet"

"Helmet" (bunch of middleware functions that set security related HTTP response headers) 

![](https://media.giphy.com/media/1pw5Hn77ylYxW/giphy.gif)

---

### Installing and Using Helmet
```
npm install --save helmet
```
```javascript=
const express = require('express')
const helmet = require('helmet');
server = express();
server.use(helmet());
```

---

* middleware functions (in helmet):
  
![](https://i.imgur.com/numLtSC.png)

---

hide PoweredBy:
```
app.disable('x-powered-by')
```

![](https://media.giphy.com/media/zac5EvG19YCVa/giphy.gif)

Yo' homies can't know your runnin' express. (unless they're expert homies)

---

### Set csp using helmet

* helmet does not set csp by default

```javascript
const helmet = require('helmet')

app.use(helmet.contentSecurityPolicy({
  directives: {
    defaultSrc: ["'self'"],
    styleSrc: ["'self'", 'maxcdn.bootstrapcdn.com']
  }
}))
```
* lots of different directives (see documentation)

---


### What do brute force attacks look like?
![](https://media.giphy.com/media/lX4YtjGGiuhUY/source.gif)

---

### How can we prevent them
* Block users who fail authentication too often
* Block IPs who fail authentication too often
![](https://media.giphy.com/media/njYrp176NQsHS/source.gif)

---

### Express middleware to the rescue!
Use [rate-limiter-flexible](https://github.com/animir/node-rate-limiter-flexible) package
```javascript=
const opts = {
  points: 6, // 6 points
  duration: 1, // Per second
};
const rateLimiter = new RateLimiterMemory(opts);
rateLimiter.consume(remoteAddress, 2) // consume 2 points
    .then((rateLimiterRes) => {// 2 points consumed})
    .catch((rateLimiterRes) => {// Not enough points to consume});
```

---

### Ensure your dependencies are secure
1. you can use `npm audit`
2. or if you want to stay more secure, consider Snyk.

    ```bash
    $ npm install -g snyk
    $ cd your-app
    $ snyk test
    $ snyk wizard
    ```

---


### Resources
[Node.js security checklist](https://blog.risingstack.com/node-js-security-checklist/)
[Production Best Practices: Security](https://expressjs.com/en/advanced/best-practice-security.html)
[Content Security Policy overview](https://developers.google.com/web/fundamentals/security/csp)
[CSP standard v3](https://www.w3.org/TR/CSP3/)
[node-rate-limiter minimal brute force example](https://github.com/animir/node-rate-limiter-flexible/wiki/Overall-example#minimal-protection-against-password-brute-force)

