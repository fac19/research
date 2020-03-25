# Client Vs Server 

![image alt](https://media.giphy.com/media/l4hLSSJA4KYpQhY1W/giphy.gif)

## What are the distinctions between a web client and a web server?

---


## Questions to consider

- What is a client and what is a server?
- Can something be both a client and a server?

- What kind of code should be run on a server instead of a browser?

![image alt](https://media1.tenor.com/images/408ce6d687a86456186aebc30f6a5486/tenor.gif?itemid=9438567)


---

## What is a client and what is a server?

---

Client:

![](https://media.giphy.com/media/786qVQHXMJhnO/giphy.gif)

- Client is a piece of hardware or software that accesses information stored on a server

---

Server:
    - hardware = stores web server software and files (HTML, JS...)
    - software = at minimum an HTTP server - a software that understands URL's and HTTP (a stateless protocol that defines how information is transmitted and formatted on the web)

---

![](https://i.imgur.com/XMpv4PF.png)

---


To publish a website you need either a static or dynmaic web server
    - static = sends files to browsers 'as-is'
    - dynamic = static + extra software like an application server and database. Application server updates files before sending them to the browser - processes content on the fly. Examples include google search or Amazon search.
 

---


![](https://mdn.mozillademos.org/files/13829/Web%20Application%20with%20HTML%20and%20Steps.png)

Source: [MDN: Client-server overview](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Client-Server_overview)

---

![](https://i.imgur.com/GYJF5j9.png)


---

## What kind of code should be run on a server instead of a browser?

- There are different programming languages used in server side scripts such as PHP, Java, C# but we're using JavaScript - (Node.js)
- Client side code does offer some user interaction with file systems and http requests but this is usually limited due to security concerns

---

- The advantage of using server-side code is that the client doesnt have to store vast amounts of data. If this was the case it would be really slow for the client to download all the data
- Server side code example.

```JavaScript
const data = new URLSearchParams(body);
       const name = data.get("name");           
```
^searches our form data from the client post request and stores name

---

## Example

### Google Earth
![](https://media.giphy.com/media/3oKIPhWFPjnUmf9fqg/giphy.gif =300x250)

- client side it displays a map which the user interacts with. Theres also a form where the user can send a HTTP POST request to the server.


---

- on the server side this is responsible for permanent storage of map data, taking user queries and resolving them into map data to be returned to the client. 

---

## Summary
### Can something be both a client and a server?

![image alt](https://media.giphy.com/media/l36kU80xPf0ojG0Erg/giphy.gif)

---

- To some degree, something can be both a client and a server
- You could for example, locally host your server on your computer (like we did in yesterday's Node JS workshop)
- The submit handler can fetch resources from a database in order to properly process the submitted info.

---

- As a result, the server could act as the client through receiving requests.
- The client, generally cannot be the server since clients are often web browsers
![image alt](https://media1.tenor.com/images/1e4dd6e15b29f265df3f7d5f2823202e/tenor.gif?itemid=9510094)

---

### However

- Clients and servers have different roles 
- The purpose of the server is to respond to client requests and in the case of a website, display information based on the user's input
- The server will contain files that you do not want your user to see, and vice versa.
- Whilst, the client interacts with the server through requesting data based on the user's input (in some cases).
- For larger projects, you would host the server separately from the client