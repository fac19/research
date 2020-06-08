￼￼
# Going Serverless

![](https://i.imgur.com/cu2Ldpw.png)



---

### What is Serverless?

"The term *“Serverless”* is confusing since there are still both server hardware and server processes running somewhere. The difference is that the organization building and supporting the *‘Serverless’* application is not looking after it. They are **outsourcing** this responsibility to someone else."


---

### What can you do with Serverless?

- **Backend as a Service** - apps which significantly rely on third-party cloud-based services to manage logic and state e.g. Firebase, Auth()
    - Popular for mobile apps and single-page web apps

---

- **Functions as a Service** - apps where server-side logic is still written but is run in stateless containers that are event-triggered and managed by a third-party. 
    - AWS Lambda functions are one of the most popular examples of FaaS


---

### Lambda functions

- Designed to activate quickly, do their job and then shut down - AWS have a timeout limit of 5mins
- Event-triggered - usually invoked by events from external services e.g. HTTP requests, new database entries or incoming message notifications
- Scalable - automatic and managed by the provider. No need to reconfigure in case of high traffic


---


### API Gateway

- API Gateway provides the REST endpoints which trigger the Lambda functions. Imagine you have the average Express app. You would usually create an app.get() method for a particular route, like this:

```javascript=
app.get('/', function(req, res, next) { /* execute some code */ });
```

- When a user hits the '/' route an event will trigger the callback function. API Gateway is the *route*, Lambda is the *callback function.*


---


![](https://i.imgur.com/O9lfLjV.png)


---

## CONFUSED YET?

![confused girl](https://media.giphy.com/media/APqEbxBsVlkWSuFpth/giphy.gif)
---

### Luckily there are tools to help

- **Serverless framework** - a popular open-source web framework written using Node.js
    - It bundles all the tools and third-party services you need into a manageable package
- **Netlify functions** - Lambda functions made easy

---

### Serverless Frameworks

1. ```npm install -g serverless```
2. Create an AWS account (limited free access for a year)
3. Set up an admin account
4. Copy credentials into .aws file
5. Create project => ```serverless create --template *aws-nodejs* --path *movie-rating*```


---

### Serverless request flow

![](https://i.imgur.com/IPohA9G.png)



---

### Netlify functions

- Netlify deploys the functions you write as full API endpoints and will even run them automatically in response to events

![](https://i.imgur.com/Qo43CRn.png)


---

### How?

1. ```npm i netlify-lambda```
2. Create a folder where your Lambda functions will live
3. Edit scripts in package.json

```json=
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start-lambda": "netlify-lambda serve src/lambda",
    "build-lambda": "netlify-lambda build src/lambda"
  },
  
```

---

#### Write your function in separate js files

- The ```event``` object - contains information from the client e.g. request headers and body 
- The ```context``` object - contains information from Netlify e.g. user information
- Netlify uses ```null``` to determine if an error occured

In hello.js
```javascript
exports.handler = (event, context, callback) => {
  callback(null, {
    statusCode: 200,
    body: 'Hello, world!',
  });
};

```

---

- Create a ```netlify.toml``` file - used to tell Netlify where to build or find our lambda functions.
- Unclear what to do with .env variables - either in Netlify UI or in .toml file

```
[build]
  Functions = "lambda"
  
 [context.production.environment]
  NAME= "World"

[context.deploy-preview.environment]
  NAME= "Developer"

```

---


### Run your functions!

``` 
    npm run start-lambda
```

- builds lambda functions in localhost directory and re-builds when a change is made
- Go to http://localhost:3000/hello and see **“Hello, world!”** displayed.
- Path name is derived from lambda function file name



------

## That's it!

![](https://media.giphy.com/media/3ofT5yFjWxh15lsl0s/giphy.gif)

---

### Resources 

[What is Serverless Architecture?](https://martinfowler.com/articles/serverless.html)

[Crash course on serverless](https://hackernoon.com/a-crash-course-on-serverless-with-node-js-632b37d58b44)

[Set up your first Serverless project](https://www.netlify.com/blog/2016/09/15/serverless-jam-a-serverless-framework-tutorial/)

[Netlify Lambda functions from scratch](https://travishorn.com/netlify-lambda-functions-from-scratch-1186f61c659e)

[Github Netlify Lambda docs](https://github.com/netlify/netlify-lambda)

[Netlify Serverless Image uploads](https://www.netlify.com/blog/2016/11/17/serverless-file-uploads/)
