# bdd-angular-using-cucumber
bdd-angular-using cucumber


Create angular project

$ npm install @cucumber/cucumber

Let's take this example of something to test:
class Greeter {
  sayHello() {
    return 'hello'
  }
}

First, write your feature in features/greeting.feature:
Feature: Greeting

  Scenario: Say hello
    When the greeter says hello
    Then I should have heard "hello"
Next, implement your steps in features/support/steps.js:
const assert = require('assert')
const { When, Then } = require('@cucumber/cucumber')
const { Greeter } = require('../../src')

When('the greeter says hello', function () {
  this.whatIHeard = new Greeter().sayHello()
});

Then('I should have heard {string}', function (expectedResponse) {
  assert.equal(this.whatIHeard, expectedResponse)
});
Finally, run Cucumber:
npm test
