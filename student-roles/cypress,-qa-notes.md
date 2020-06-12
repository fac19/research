---
title: "Cypress, QA Notes"
tags: ""
---

## Set Up

To Install Cypress:

```bash
npm install cypress --save-dev
```

To open Cypress:

```bash
node_modules/.bin/cypress open
```

Or

```bash
npx cypress open
```

* * *

## To run Cypress in CI:

Headless Mode (Without opening up the browser)=>

```bash
npx cypress run
```

Records result to cypress dashbard=>

```bash
npx cypress run --record
```

CI with Parallelistion (don't need)=>

```bash
npx cypress run --record --parallel
```

## File Structure

![](https://i.imgur.com/nhsjrAn.png)

-   **Fixtures** are external pieces of static data that can be used by your tests. We should not hard code data in the test case. It should drive from an external source like CSV, HTML, or JSON. They will be majorly used with the cy.fixture() command when you need to stub the network calls. 

-   The **integration** folder provides a place that writes out test cases. It also provides an “examples” directory, which contains the default test cases provided by Cypress and can be used to add new test cases also. We can also create our folder under the integration directory and add out test cases under that.

-   **Plugins** contain the plugins or listeners. By default, Cypress will automatically include the plugins file “cypress/plugins/index.js” before every test it runs. You can programmatically alter the resolved configuration and environment variables using plugins, Eg. If we have to inject customized options to browsers like accepting the certificate, or do any activity on test case pass or fail or to handle any other events like handling screenshots. They enable you to extend or modify the existing behavior of Cypress. 

-   **Support** writes customized commands or reusable methods that are available for usage in all of your spec/test files. This file runs before every single spec file. That’s why you don’t have to import this file in every single one of your spec files.  The “support” file is a great place to put reusable behavior such as Custom Commands or global overrides that you want to be applied and available to all of your spec files. 

-   **Cypress.json** is used to store different configurations. E.g., timeout, base URL, test files, or any other configuration that we want to override for tweaking the behavior of Cypress.

* * *

## Config package.json

```json
{
  "scripts": {
    "cy:open": "cypress open",
    "cy:run": "cypress run --spec 'cypress/integration/*.spec.js'",
    "cy:ci": "start-server-and-test start http://localhost:3000 cy:run"
  },
  "devDependencies": {
    "cypress": "^4.8.0",
    "eslint-plugin-cypress": "^2.11.1",
    "husky": "^4.2.5",
    "lint-staged": "^10.2.9",
    "start-server-and-test": "^1.11.0"
  },
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.js": [
      "cy:run"
    ]
  }
}
```

```bash
--spec 'cypress/integration/*.spec.js'
```

=> Used to specify which tests to run

```bash
"cy:ci": "start-server-and-test start http://localhost:3000 cy:run"
```

=> **start-server-and-test**, Starts server, waits for URL, then runs test command; when the tests end, shuts down server

**eslint-plugin-cypress** &lt;= NEED THIS!!

* * *

## Config cypress.json

```json
{
  "projectId": "zu91zp",
  "baseUrl": "http://localhost:3000",
  "viewportHeight": 568,
  "viewportWidth": 320,
  "video": false
}
```

-   with baseUrl => in test, set cy.visit("/");

-   without baseURL => in test, set cy.vist("<http://localhost:3000/">)

-   viewportHeight & viewportWidth => sets default viewport, override with cy.viewport('iphone-6');

-   video => stops saving video files of test locally 

* * *

## Config eslintrc

```json
{
  "extends": ["react-app", "plugin:jsx-a11y/recommended", "plugin:cypress/recommended"],
  "plugins": ["jsx-a11y", "cypress"],
}
```

* * *

## Config travis.yaml

```yaml
script:

  - num run cy:ci --record
```

* * *

## Config .gitignore

/cypress/integration/examples

=> comes with example when installed, doesn't need to be in deployment

/cypress/videos

=> If cypress.json doesn't have _video: false_, videos are then stored into this file, doesn't need to be in deployment

* * *

## Example test file

cypress/intergration/sample.spec.js

```js
describe('Sample.spec', () => {
  it('is working', () => {
    expect(true).to.equal(true);
  });
});
```

* * *

## Resources

[Cypress Offical Guide](https://docs.cypress.io/guides/overview/why-cypress.html#In-a-nutshell)

[Examples on gitHub](https://github.com/cypress-io/cypress-example-recipes)

[Cypress CSS Tricks Guide](https://css-tricks.com/using-cypress-to-write-tests-for-a-react-application/)

[Jest, React Testing Library, React](https://medium.com/javascript-in-plain-english/i-tested-a-react-app-with-jest-testing-library-and-cypress-here-are-the-differences-3192eae03850)

[Cypress 5min Youtube](https://www.youtube.com/watch?v=AddBNz1T08U)

[Testing for React Applications with Cypress 40min Youtube](https://www.youtube.com/watch?v=lgurVvQsOTY)

[ Testable UI Architecture | Lunchtime Sessions](https://www.youtube.com/watch?v=yIje50csKpk&feature=youtu.be)
