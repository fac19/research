# Browser cashing - Week 8 Spike :bear:

---

## [Money cache load, money cache load.](https://www.youtube.com/watch?v=31xa0CLbcls)  
![](https://media1.giphy.com/media/2Nbu3fA8swIcE/200.gif?cid=e1bb72ff0a6e0c7575a59633c8cdeb2492c8b029f9d29c6d&rid=200.gif)

---

## Topics 
How can we avoid unnecessary network requests?
- What is HTTP caching?
- How can our server tell browsers to cache our responses?

---

## What is HTTP caching? :bear: 
>A Web cache allows for the temporary storage of Web documents, such as Web pages and images to reduce server lag.

---

## How can we control it? 
The HTTP cache's behavior is controlled by a combination of request and response headers.

---

### Requests - Just Chill 
Stick with the defaults (handled by the browser)

![](https://media2.giphy.com/media/7NUdxH6uzeI1i/200.gif?cid=e1bb72ffa4c4c1de7b54b3a29ff246678ace75b0554ece3b&rid=200.gif)

---

### Responses - Put in work $$$ :bear: 	
The part of the HTTP caching setup that matters the most is the headers that your web server adds to each outgoing response, these are the important ones:
1. Cache-Control, 
2. ETag,  
3. Last-Modified 

---

P.S: Leaving out the Cache-Control response header does not disable HTTP caching! Instead, browsers effectively guess

---

There are two important scenarios that you should cover:

---

### 1. Long-lived caching for versioned URLs (Things don't change) :bird: :bear: 

- Sometimes you attach a unique id to the files you send out, e.g. style.4553.css
- Your html, not uniquely versioned, is requested every time, and contains an up to date css filename

---

### long-lived caching (continued)

- When you send out the css you can set max-age=31536000 (1 year, the longest allowed time) because the browser will always use the html to ask for the right one

`Cache-Control: max-age=31536000`

---

### 2. Server revalidation for unversioned URLs (Things change) :bird: :monkey: 

- First off, make sure you add `Cache-Control: no-cache` to your response messages. This explicitly tells the browser that it needs to go to the network to check if there's been an update is necessary.
- `Cache-Control: no-cache` doesn't mean "don't cache", it means it must check with the server before using the cached resource.

---

### Server revalidation (continued)

- When you send the resource, you should send it with an E-tag, a fingerprint of the file (an alternative approach is last-modified), and a max-age. 
- You should set the max-age low.

---

### Server revalidation (continued)


- When the client wants the resource again, it checks max-age. If the cache is old, it sends a request with the E-tag to the server. 
- The server looks at the E-tag and sees whether the client has an up to date resource. If they do, it returns 304 Not Modified. If they don't, it returns the resource. Either way, max-age is reset.

---

### ETag :monkey: 

![](https://webdev.imgix.net/http-cache/http-cache.png)

---

:monkey: 
`ETag: "<etag_value>"`

* They allow caches to be more efficient and are useful to help prevent simultaneous updates from overwriting each other ("mid-air collisions").


---

### `Etag` and `If-match` :monkey: 

* `POST` request contains `If-match` header containing Etag values
* No hash match = 412 error
* if resourse has been updated new Etag has to be generated

---

### `Last-Modified:` :monkey: 

* Less accurate than an ETag header, it is a fallback mechanism.
* Contains the date and time at which the origin server believes the resource was last modified. 
* It is used as a validator to determine if a resource received or stored is the same. 


`Last-Modified: <day-name>, <day> <month> <year> <hour>:<minute>:<second> GMT`


---

## HTTP Caching in Node with Express? :goat: 
![](https://media3.giphy.com/media/H6JdkRnhXQaImiCYp2/giphy.gif?cid=ecf05e4773ce9d59750e8cc002313cb01dbe43567fd8354a&rid=giphy.gif)

---

## Easiest approach ( to my understanding ...) is: :goat:
![](https://media.giphy.com/media/hvSOjOos8rZyb9ZUjO/giphy.gif)

---

As with many problems, someone likely has already solved it for you and made it into an NPM package. Here's a couple of popular ones:


- memory-cache
- redis

Node npm module that's used as middleware in your routes. 

---

```javascript=
    // configure cache middleware
    let memCache = new cache.Cache();
    let cacheMiddleware = (duration) => {
        return (req, res, next) => {
            let key =  '__express__' + req.originalUrl || req.url
            let cacheContent = memCache.get(key);
            if(cacheContent){
                res.send( cacheContent );
                return
            }else{
                res.sendResponse = res.send
                res.send = (body) => {
                    memCache.put(key,body,duration*1000);
                    res.sendResponse(body)
                }
                next()
            }
        }
    }
```

---

use it as a middlewere
```javascript=
    // index.js

    app.get('/products', cacheMiddleware(30), function(req, res){
         [...]    
    });
```

it's a module, so don't forget tio require it!
```javascript=
const cache = require('memory-cache');
```

---

### Conclusion :goat:

- Caching comes in handy a lot of times, but you need to know when to use it. it may be an overkill especially when the requests made to the application aren’t frequent.

- POST, PUT and DELETE methods should never be cached because you want unique resources to be affected each time a request is made.

---


## Resources
[HTTP Caching | Web Fundamentals](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching)
[The HTTP cache: your first line of defense](https://web.dev/http-cache/)
[Caching best practices - with some clear examples](https://jakearchibald.com/2016/caching-best-practices/)
