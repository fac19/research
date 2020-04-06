# Continuous integration

![](https://i.imgur.com/AiulNyn.gif?noredirect =400x)

---

<!-- Chloe -->
### What is continuous integration (CI)? 

- Agile / Extreme programming practice.
- A system for __automating__ the __development pipeline__ e.g. when you push, tests are run automatically, and if the tests pass, the program builds automatically. 
- Frequent merging/integrating everyone's code

---

> <!-- Kat -->
![](https://i.imgur.com/8IEZF2D.png)

---

### Why run tests whenever we push?
<!-- Chloe -->
![](https://media.giphy.com/media/cFkiFMDg3iFoI/giphy.gif)

- Reduce risk of merge conflicts
- Codebase is always deployable
- Integration and design bugs found early
- Encourages small commits and simpler code

---

### Workflow
<!-- Ivo -->
- Commit to main line several times a day
- Automated building and (quick) testing
- Minimal branching
- Every bug-fix should come with a test case

---

### Continuous deployment (CD)
<!-- Ivo -->
![](https://media.giphy.com/media/spZkHIUibt4ic/giphy.gif)

- Often mentioned in the same breath - CI/CD
- Closely allied concept, natural extension of the pipeline
- Deploying your project (relatively) rapidly
- How fast depends on context (website:fast, OS: slow)

---

### Continuous integration in practice: Github Actions

<!-- Roger -->
![dog](https://media.giphy.com/media/gzKRbHzioNmzS/giphy.gif)

---

- Sets up an automated testing system on Github projects
- Installs dependencies
- provides test results in a pull request so you can see whether there are errors on your branch

---

<!-- Roger -->
### Setting up automated github actions

- Make sure you have a node project with tests, and your package.json is configured so that `npm run test` runs your tests.
- Make a folder `.github/workflows`
- Create a file `javascript.yml` in it
- Copy the config from somebody's tutorial and adapt it!
- Commit and push that file up to your repo
- Check that it works by looking at the actions tab in github

---

<!-- Chloe -->
![github actions](https://i.imgur.com/499KeMo.png)

---

<!-- Chloe -->
![set up tests](https://i.imgur.com/I0JAe4h.png)

---

## YAML
<!-- Kat -->
- Simular to JSON, I think
- YAML readable data serialization standard 
- Can be used with all programming languages 
- Ofen used to write configuration files.

---

## Conclusion:
<!-- Kat -->
#### CI is a workflow strategy that ensures everyones changes will integrate with the current version of the project 

---

## Questions?

![](https://media.giphy.com/media/zgf1opQOtG05a/giphy.gif =750x)





