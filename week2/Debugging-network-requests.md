# Debugging network requests
![debugging](https://media.giphy.com/media/5H3myfJ4jRVOU/giphy.gif)

---

## Why do we want to do this?

We want to see what is going on in our request.

![unsure](https://media.giphy.com/media/ANbD1CCdA3iI8/giphy.gif)

---

## Usually, we have a problem

* For example you fetch `url` similar to this `"/njagnja"` and things seems to work but they actaully don't - you might want to access the status code

---

* Debugging gives you clarity over what's going on 'under the hood'

![under-the-hood](https://media.giphy.com/media/xTiTnm8AGoS75Cvyko/giphy.gif)

---

## We have a problem

![example problem](https://developers.google.com/web/tools/chrome-devtools/network/imgs/slow-content-download.png)

---

* The connection between the client and server is slow (e.g. on mobile).
* A lot of content is being downloaded.

---

## Fortunately we have some tools
![how](https://media.giphy.com/media/fpXxIjftmkk9y/giphy.gif)

---

**In-browser**
* Chrome Dev tools
* Postman

**External**
* cURL

---

## Chrome Dev Tools
![](https://media.giphy.com/media/89bq55CYqPQDS/giphy.gif)

It's simple and does most things.

---

## Using Chrome Dev Tools to Inspect Network Activity
1. Open Chrome Dev Tools
2. Click the 'Network' tab
3. If the 'Network' panel is empty, refresh the page
4. All activity should be logged in the 'Network Log'
5. Each row represents a resource
6. Each column represents information about a resource, e.g. 'Status', 'Type', 'Initiator', etc.

---

## i.e.

![example problem](https://developers.google.com/web/tools/chrome-devtools/network/imgs/slow-content-download.png)

---

## Postman
![postface](https://media.giphy.com/media/cViyi7tY8I62c/giphy.gif)

For when simple just isn't good enough.

---

## What is Postman?

A native app used to make API requests and examine the responses without using a terminal or writing any code.

When you send a request, the API response appears inside the Postman UI.

---

## How to send a request on Postman?

1. Open the Postman App and sign in
2. Make sure build is selected
3. Click + to open a new request tab
4. Enter the API URL into the URL field
5. Click send

*Demonstrate sending the request*
The JSON data response from the server will appear in the lower panel

---

## Uses of Postman
![postman](https://media1.tenor.com/images/40884b219e55db5f4b34a563b52de19b/tenor.gif)

---

### On-the-fly testing
Postman lets you write a test without needing to save it, you just make a request to a URL and see the result parsed into JSON within the app interface.


---

### Test suites
Create collections of integration tests to ensure your API is working as expected. Tests are run in a specific order with each test being executed after the last is finished. 


---

### Request history
Postman gives you a data-stamped history of all the requests you build for easy reference as you work with an API.

---

## cURL
![cmd line](https://media.giphy.com/media/W3k4blp4iS15m/giphy.gif)

Create network requests from the command line

---

## How to use cURL

The basic syntax of using cURL is simply:

```
$ curl <url>
```

This fetches the content available at the given URL, and prints it onto the terminal. 

For example, if you run: 
```
$ curl example.com
```
You should be able to see the HTML page printed *show in demo*

---

## Uses of cURL

### Testing for protocol support
To check if a site supports a certain version of SSL. An SSL certificate is "a type of digital certificate that provides authentication for a website and enables an encrypted connection"

---

Example: If you want to check if a site supports TLS v1.2, you can use:
    `curl -v --tlsv1.2 https://www.booleanworld.com/`
    
    
This command will throw a 'handshake_failed' because the server doesn't support this version of SSL

---

## Question time
![question](https://media.giphy.com/media/FJ0lXKOdOwjvO/giphy.gif)

---

## Extra Reading

Find some super fun cURL tutorials [here](https://www.booleanworld.com/curl-command-tutorial-examples/)

Find more info on what cool things you can do with cURL [here](https://https://flaviocopes.com/http-curl/)

