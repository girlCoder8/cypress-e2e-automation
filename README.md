# ** E2E test suite with Cypress **
> **application under test:** http://angularjs.realworld.io/


## :goal_net: Goals
- keep it simple - no 'custom' abstractions/functions/utils/helpers (use what Cypress provides)
- tests are easily readable
- project is easily understandable even to people without previous JS or Cypress knowledge
- [use shortcuts](https://docs.cypress.io/api/cypress-api/custom-commands#4-Skip-your-UI-as-much-as-possible) to avoid repeating/testing the same UI actions over and over again

![image](https://user-images.githubusercontent.com/48861601/110022516-af6f2400-7d34-11eb-8b13-f21789331cb3.png)


## :gear: Setup

1. `git clone https://github.com/girlCoder8/cypress-e2e-automation.git`
2. cd to `cypress-e2e-automation` folder and run `npm install`


## :heavy_check_mark: Run tests

- If you installed Cypress via npm:
    - cypress test runner (cypress __open__):
        - **`npm run cy:open:web`** OR `cypress open --env device=web` (change web to mob to switch to mobile view)

    - cypress __headless mode__ (cypress run):
        - `npm run cy:run:web` OR `cypress run --env device=web`
- If you installed Cypress zip:
    - import **`cypress-e2e-automation.zip`** folder and you are good to go

#### :hammer_and_wrench: Configuration
Config files:
1. `cypress.config.js` - Main config file where default behavior of Cypress can be modified. [More info](https://docs.cypress.io/guides/references/configuration)
2. `plugins/index.js` - Plugins file is where we can programmatically alter the resolved configuration [More info](https://docs.cypress.io/guides/tooling/plugins-guide#Use-Cases)

This test suite is supporting multiple viewports (mobile and desktop). See `plugins/index.js` file

One solution is to use [cy.viewport()](https://docs.cypress.io/api/commands/viewport) command inside the test, to change the viewports, but very often websites also check user agent to get the device information(and show the mobile view). Since user agent is something [we can't change in the middle of the test](https://github.com/cypress-io/cypress/issues/2100), we need to pass config value when launching tests. In `cypress.config.js` we have a `device` parameter and in plugins file `index.js`, we decide viewports and user agent parameter values based on that device value.
