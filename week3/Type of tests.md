# Type of Tests
![I Fd up](https://media0.giphy.com/media/y0vEHbjlGJofC/200.gif?cid=e1bb72ff83a9ddb5f6c03273be65b41ac65042e06f410745&rid=200.gif)

---

## We'd like to talk about
- What is Prettier? How might it help us write better code? 
- What is static analysis? 
- How can a linter help us avoid bugs? 
- What are the pros and cons of unit, integration and end-to-end tests?

---

## Types of test
- **End to End:** Code that behaves like a user, clicks around the app and verifies that it functions correctly. 

- **Integration:** Verify that several units of code are able to work together.
- **Unit:** Check that individual segments of code (e.g. functions) work.
- **Static:** Catch typos and type errors as you write the code.

---

``` let yourTests = aCathedral :)```

![Not another cathedral analogy](https://media3.giphy.com/media/EqiFV8QX3DEc4bfTc5/200.gif?cid=e1bb72fffd5fed3f51d212f50eba105d68e5fce48b9035ca&rid=200.gif)

---

![](https://i.imgur.com/pFTHfHL.png)


---

## Trade offs
### Cost
As we move up the floors of our testing cathedral, the complexity of the design increases.

```javascript=
let cost = moreComplexTesting => morePointsOfFailure => moreChanceTheTestWillBbreak
```

- Operation costs: money to run the tests in their environment (electricity & water) 
- Contruction & Maintenance of tests (Raw materials and construction workers and janitors' salaries)

---

### Speed

```javascript=
let speed = numberOffTests + amountOfCode
```

Unit tests typically test something small that has no dependencies **OR** will mock those dependencies (effectively swapping out what could be thousands of lines of code).

>So if unit tests are cheap and fast. Why would we use anything else?

---

### Confidence
>*"The more your tests resemble the way your software is used, the more confidence they can give you."*

**Ideal Scenario:** we'd mimic a user and manually test every edge case but that would be expensive and slow.

---

Conversely, the lower down the cathedral you are, the less code you are testing.

So how can we find the right balance? 

![Pros and cons](https://media1.giphy.com/media/6S3BEgH1UN61i/200.gif?cid=e1bb72ffe5061919f1b2c55f6ef828afce730d08b89f51f2&rid=200.gif)

---

## Pros and Cons of Unit testing

- Quick
- No dependent code
- Enables fast developer feedback during development.

```javascript
test("makeUrl should create the correct PokéAPI URL", t => {
  t.equal(makeUrl("pikachu"), "https://pokeapi.co/api/v2/pikachu");
  t.equal(makeUrl("bulbasaur"), "https://pokeapi.co/api/v2/bulbasaur");
});
```

---

## Pros and Cons of Integration testing 
- Tests the links between chunks of code
- Continuously checks new code 

```javascript=
test("calculates user's input correctly", t => {
  const a = document.querySelector('#a')
  a.value = 5;
  const b = document.querySelector('#b')
  b.value = 13;
  const sign = document.querySelector('#sign')
  sign.value = '+';
  const submitBtn = document.querySelector("button[type='submit']");
  submitBtn.click();
  const result = document.querySelector('#result')
  t.equal(result.textContent, '18')
  result.textContent = ''
});
```

---

### Basketball analogy

![The pope is a baller too](https://media2.giphy.com/media/zP09g2o0vLNw4/200.gif?cid=e1bb72ff3871636b94ed6b9a2c707130e7e59643e6e6d4ff&rid=200.gif)

---

## Pros and Cons of E2E testing
- Simulates a user's experience
- Accurate, detailed feedback about app from back-end to front-end
- Time-consuming
- Expensive

![](https://media1.giphy.com/media/ro2tOPw8ywqJi/200.gif?cid=e1bb72ff377e3cf04db9cf91d1e83ea120cdd85ed9b89806&rid=200.gif)

---

```javascript=
module.exports = {
  'Demo test Google' : function (browser) {
    browser
      .url('http://www.google.com')
      .waitForElementVisible('body', 1000)
      .setValue('input[type=text]', 'nightwatch')
      .waitForElementVisible('button[name=btnG]', 1000)
      .click('button[name=btnG]')
      .pause(1000)
      .assert.containsText('#main', 'Night Watch')
      .end();
  }
};

```

---

# Getting Started with ESLint

### https://eslint.org/

---

## What is ESLint?
It is a tool/extension to make sure your JS is free of any errors!!

![lint](https://media.giphy.com/media/7DynWwZL3misg/giphy.gif)

---

## How can a linter help us avoid bugs?

### Find Problems
- ESLint analyzes your code to quickly find problems. 
- ESLint is built into most text editors

---

### Fix Automatically
- Many problems ESLint finds can be automatically fixed. 
- ESLint fixes are syntax-aware so you won't experience errors introduced by traditional find-and-replace algorithms.

### Customize
- Write your own rules that work alongside ESLint's built-in rules. 
- You can customize ESLint to work for you and your project.

---

## How to Install ESLint?
#### What you need:
Node.js

npm
    - https://www.npmjs.com/ 
    - npm is the package manager for the Node JavaScript platform

---

1. You can install ESLint using npm or yarn:
`npm install eslint --save-dev`
or
`yarn add eslint --dev`
2. You should then set up a configuration file:
`$ npx eslint --init`
3. After that, you can run ESLint on any file or directory like this:
`$ npx eslint yourfile.js`

---

## Example

*show ESLint using https://eslint.org/demo*

---

## What is Prettier?

![image alt](https://media.giphy.com/media/k1SuVPEuA89S8/giphy.gif)
- Prettier is an extension used to format code and supports over 10 languages
- It takes your code input and prints it in a consistent format, removing any of the original code style
- To get started with Prettier, check out prettier.io

---

___

## Installing Prettier

- You can install Pretttier using yarn or npm from the command line

```javascript=
yarn add prettier --dev --exact
# or globally
yarn global add prettier
```

```javascript=
npm install --save-dev --save-exact prettier
# or globally
npm install --global prettier
```

- Then, search for the extension on VSCode Marketplace


---
___

___

## Prettier in action
```javascript=
foo(reallyLongArg(), omgSoManyParameters(), IShouldRefactorThis(), isThereSeriouslyAnotherOne());
```
Prettier will format this into into:
```javascript=
foo(
  reallyLongArg(),
  omgSoManyParameters(),
  IShouldRefactorThis(),
  isThereSeriouslyAnotherOne()
);
```



___

___

## Benefits of using Prettier

- Saves the developer time formatting code, since it's already done automatically
- Consistent formatting across the board. Say goodbye to those pesky brackets
- Enforces a consistent style for a team
- Beginner friendly for those who are new to the language
- You can run it from the command line

---


## Things to remember

- Prettier is not a substitute for a linter
- There are some things that a linter does, that Prettier does not do. Most importantly, linters will flag actual errors with in your code
-  For example, if there's an unused variable floating about somewhere


---

-  Prettier does not do this and concerns itself mainly with code formatting
-  It would be better to have both ESlint and Prettier installed
-  To avoid any conflicts between both tools, disable the formatting rules for ESLint



---

## Why install ESlint and Prettier

![image alt](https://media3.giphy.com/media/ul1omlrGG6kpO/giphy.gif?cid=790b7611fc20d284e97e53da6e1a0265232f65b83b5c4afa&rid=giphy.gif)

---


- Best of both worlds!
- Save time catching bugs and removing dodgy formatting
- Makes code reviews easier


---

## Any questions?

![image alt](https://media3.giphy.com/media/3ohzdRoOp1FUYbtGDu/giphy.gif)

