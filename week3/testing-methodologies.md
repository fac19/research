# Testing methodologies
![image alt](https://media3.giphy.com/media/7MZ0v9KynmiSA/giphy.gif)

---

##  What is Test-Driven Development (TDD)? 
![image alt](https://miro.medium.com/max/1200/1*-Qk4PaEr5CR6EQ3vhvRWyg.png)

___

---

* check if a passing test is not a false positive
* Write the implementation code and watch the test pass.
* Refactor if needed.

---

## TDD can teach you How to Write Better Code
![image alt](https://media.giphy.com/media/ZVik7pBtu9dNS/giphy.gif)

---

* how long it takes to debug it if something goes wrong. 
* TDD is far more than a safety net
* breaking large problems down into lots of small fixable ones

---

```javascript=
const allInput = document.querySelectorAll('input')

for (let i = 0; i <allInput.length; i++){
    if (allInput[i].innerText !== '') {
    console.log("I am in")
      submitArray.push(allInput[i]);
}

```

---

![form where name attribute is filled with the name of Rambo](https://i.imgur.com/qAdfERL.png)

---

```javascript=
const allInput = document.querySelectorAll('input')

test("check if we are gettting correct info from name input", t => {
    t.equal(allInput[0].innerText, Rambo) // this would fail test
    t.equal(allInput[0].value, Rambo) // this would pass
})

```

---

### First, write the test. 
![image alt](https://media.giphy.com/media/xT5LMtserjL4RtFZQc/giphy.gif)

---

### watch it fail
![image alt](https://media.giphy.com/media/11XB0sYkytJPNK/giphy.gif)

---

### Refactor 
![image alt](https://media.giphy.com/media/1rf4hhXCoTQNa/giphy.gif)

---

## How TDD Saves Whole Teams Time?

* It eliminates fear of the merge button.
* let changes thrive

---

### What is Behavior-Driven Development (BDD)? 

- Approach to software development based on a user's behaviour
- Part of the Agile Methodology
- Encourages collaboration among developers, QA and non-technical or business participants
- Emarged from TDD
- At the first stage uses normal language to describe each step of the users' journey - easy to understand for non-technical stakeholders
- Focus on collaboration & communication

---

![image alt](https://agilecoach.typepad.com/.a/6a00e54ee21bf28834016302ae39ee970d-pi)

---

### BDD Process

- define a test set for the unit first;
- make the tests fail;
- then implement the unit;
- finally verify that the implementation of the unit makes the tests succeed.

---

### Different layers of tests within BDD methodology

- Unit Tests
- Functional Tests
- Inegration Tests

---

### Tools

- TestCafe
- Cucomber

---

## How do we translate _user requirements_ into _automated tests_?

---

```
Story: Subscribe to a newsletter

As a website user
In order subscribe to a newsletter
I want a form to take my name and email address

Given that type of input is correct
I want to be able to submit data
And be notified of successful subscription

```

---

1. Open the form
2. Fill in name and email
3. Click submit button
4. Wait for a confirmation dialog
5. Click and confirm subscription


---

#### Test Coverage


![](https://i.imgur.com/38cPqBE.png)

---

Step 1. The total lines of code in the piece of software quality you are testing 
Step 2. The number of lines of code all test cases currently execute
Now, you need to find (X divided by Y) multiplied by 100. The result of this calculation is your test coverage %.

---

For example:

If the number of lines of code in a system component is 500 and the number of lines executed across all existing test cases is 50, then your test coverage is:

```
(50 / 500) * 100 = 10%
```

---

#### you are doing enough testing if the following is true:
* You rarely get bugs that escape into production.
* You are rarely hesitant to change some code for fear it will cause production bugs.

---

### Should we aim for 100% test coverage?

![](https://media.giphy.com/media/9XRgItPZDUlTa/giphy.gif)

---

## References

## TDD

- https://medium.com/javascript-scene/tdd-changed-my-life-5af0ce099f80

### BDD

- https://medium.com/javascript-scene/behavior-driven-development-bdd-and-functional-testing-62084ad7f1f2
- https://agilecoach.typepad.com/agile-coaching/2012/03/bdd-in-a-nutshell.html
- https://en.wikipedia.org/wiki/Behavior-driven_development

### Test Coverage
- https://www.martinfowler.com/bliki/TestCoverage.html#footnote-devs
- https://www.guru99.com/test-coverage-in-software-testing.html#8
