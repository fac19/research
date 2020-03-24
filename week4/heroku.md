# Heroku Tech Spike
![image alt](https://media.giphy.com/media/KcttJjGMgk3hBGPrDk/giphy.gif)

---

## Platform as a service? 
(PaaS) is a category of cloud computing services that provides a platform allowing customers to 
- develop
- run
- manage 

applications without having to build and maintain the infrastructure

Examples: Windows azure,
Amazon Web Services (AWS) is not (we think maybe...)!

---

## What is heroku?
Heroku is a platform as a service (PaaS) that enables developers to build, run, and operate applications entirely in the cloud.

![image alt](https://media.giphy.com/media/HknSLLEbzZCoM/giphy.gif)

---

* Heroku lets you deploy, run and manage applications written in Ruby, Node.js, Java, Python, Clojure, Scala, Go and PHP.
* Every app built on Heroku is deployed to Amazon Web Services(AWS).

---

Heroku is known for running apps in dynos – which are really just virtual computers that can be powered up or down based on how big your application is. This is one of its main benefits - unlike if you buy your own server, you can just rent more dyno space. 

![](https://media0.giphy.com/media/FQxxGAgpD9bIA/giphy.gif?cid=790b76119ab415571627b5734558da1692ccb4767bab0368&rid=giphy.gif)

---

## Heroku and Dependencies
Dependency mechanisms vary across languages: 
- in Ruby you use a Gemfile, 
- in Python a requirements.txt, 
- in Node.js a package.json, 
- in Java a pom.xml 

and so on.

---

## What is an application?
An application is a **collection** of 

**source code** written in one of these languages, 

perhaps a **framework**, 

and some **dependency description** that instructs a build system as to which additional dependencies are needed in order to build and run the application.

---

## How to run the application?
One requirement is informing the platform as to which parts of your application are runnable. In Node.js it’s the main field in package.json

---

When you create an application on Heroku, it associates a new Git remote, typically named heroku, with the local Git repository for your application.

---

As a result, deploying code is just the familiar git push, but to the heroku remote instead:

```bash

$ git add .
$ git commit -m "Added a Procfile."
$ heroku login
Enter your Heroku credentials.
...

$ heroku create
Creating arcane-lowlands-8408... done, stack is cedar
http://arcane-lowlands-8408.herokuapp.com/ | git@heroku.com:arcane-lowlands-8408.git
Git remote heroku added

$ git push heroku master
...
-----> Node.js app detected
...
-----> Launching... done
       http://arcane-lowlands-8408.herokuapp.com deployed to Heroku

```

---

## What is an Environmental Variable (EV) :electric_plug: 




An EV is a variable whose value is set outside the program through: 
- functionality built into the operating system or
- a microservice

---

An EV is made up of a name/value pair, and any number may be created and available for reference at a point in time.

Using EVs in backend applications relies on operating system commands to define the EV and its value.

EVs typically aren’t globally accessible across the OS, they usually session-specific. 

---

## Where to find your EV

Windows OP: control panel>system>advanced system settings>environment variables

Linux & Mac OS: run **_env_** in the terminal


---

## Why use an EV?

One use for them is securing information from an application that others can see. For instance, you could save Oauth tokens for an API in an environment variable, and then share the project but not the location of the environment variables so that people could not access your API token. 

![](https://media3.giphy.com/media/Zczaq4MUUZ3B9Y0L89/200.gif?cid=e1bb72ff309db7dc8f7cad6dbf39f7ab4f7660a066bfbbd8&rid=200.gif)

## EVs for Node outside Heroku

If you're not using Heroku, you can write them in a file called .env, and then use the third party module [dotenv](https://www.npmjs.com/package/dotenv) to make them available in your source code.

At runtime, NodeJS automatically loads EVs into process.env to make them available to the application.

In the .env file:

    MY_OAUTH_TOKEN=d41045d93d4884c613da4ac0e5a79a


In your JavaScript:

```javascript=0
require('dotenv').configure()
process.env.MY_OAUTH_TOKEN // d41045d93d4884c613da4ac0e5a79a
```



## EVs for Node applications running in Heroku

In Heroku, you set them by the Heroku CLI, via an API, or with the Heroku dashboard. In the CLI you use 

    heroku config::set MY_TOP_SECRET_PASSWORD=password

to set environment variables and you can use

    heroku config
    
to see them.

---

You can also use the Heroku dashboard:

![](https://i.imgur.com/eaCvzPv.png)

---

Outside Heroku, a common way to access the .env file is with the third-party module dotenv:

---

## Git and Heroku

## How to deploy a NodeJS app to Heroku from Github?

---

### STEP 1
in direcotry run `npm init` that will create json file. similar to this 
```jsonld=
{
  "name": "coolnodeapp",
  "version": "1.0.0",
  "description": "node app ",
  "main": "app.js",
  "scripts": {
  "start": "node app.js"
},
  "repository": {
  "type": "git",
  "url": ""
},
  "author": "",
  "license": "ISC",
  "bugs": {
  "url": ""
},
  "homepage": ""
}
```

---

Ipmportant change to nitice is `"start": "node app.js"`
After the deployment, Heroku will run this command to start your application

---

be carefull with hard coding port varaible for the app
`const port = process.env.PORT || 3000`
The application server is started on a random port on the cloud.

---

### STEP 2: Push to GitHub
 push this to your git repository

---

### STEP 3: Deploy to Heroku
- Open free account with Heroku
- Click “Create new app”
- The app name will be included in the public URL for your application

---

- Open Deploy tab, scroll to the “Deployment method” and select GitHub as the method.
- It will show Connect to GitHub, screen-shot below

![image alt](https://cdn-media-1.freecodecamp.org/images/ylaZsAuah1udMDvouTIQLmzLDKJX9FrC23yB)

---

- the Deployment section will show up where you can select if you want Automatic Deployment (as soon as the changes are pushed to GitHub, Heroku will pick them up and deploy) or Manual Deployment
![](https://cdn-media-1.freecodecamp.org/images/PPD75YeIqpQs-R2pFcjyRmfvZwNQWvrAH6CM)

---

- to tell heroku that we are using nodeJs app we need to click on **add buildpack**
![image alt](https://cdn-media-1.freecodecamp.org/images/C-eFABZoiiKs2MJMPfWNSFaALNH2mLeIlmlN)

---

- At Deploy tab, and click Deploy Branch
- Heroku will take the code and host it!

---

## Resources
##### Seting up Heroku: https://devcenter.heroku.com/articles/getting-started-with-nodejs#set-up
##### GitHub Integration(Heroku GitHub Deploys):https://devcenter.heroku.com/articles/github-integration
##### automatically deploy merges to our Master branch:https://www.freecodecamp.org/news/how-to-deploy-a-nodejs-app-to-heroku-from-github-without-installing-heroku-on-your-machine-433bec770efe/

---

Questions

![](https://media0.giphy.com/media/3ofT5zixhJOx82Zkly/giphy.gif?cid=790b76113592d0e65fed8b9917fd18c49435abae3ec17e1e&rid=giphy.gif)

