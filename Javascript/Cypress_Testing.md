# Cypress Testing

---

## Writing the First Test using Cypress.io

[Cypress Document](https://docs.cypress.io/guides/getting-started/writing-your-first-test.html) - Check out full documentation from Cyperss.io

Example test script `sample_spec.js`

```javascript
describe('My First Test', function() {
    it('Does not do much!', function() {
        // this block is where test script is written
        expect(true).to.equal(true)
    })
})
```

Seperated documentation is required.
`describe` and `it` comes from [Mocha](https://mochajs.org)
`expect` comes from [Chai](https://www.chaijs.com)

---

## Test Methodology

Testing consists of 3 phases(AAA);
    1. Arrange - set up, mock, stub, visit, query
    2. Act - click, fill in, ...
    3. Assert - check output

### 1. Arrange - `visit` `query`

Using kitchen sink application[^1] as the example.

#### Visit 

```javascript
describe('My First Test', function() {
    it('Visits the Kitchen Sink', function() {
        cy.visit('https://example.cypress.io') // navigate to the page
    })
})
```

#### Query

```javascript
describe('My First Test', function() {
    it('finds the content "type"', function() {
        cy.visit('https://example.cypress.io')

        cy.contains('type') // focus on the element containing text 'type'
    })
})
```

Selecting elements can be done using

- `cy.contains` - finding element using text
- `cy.get` - find element using selector (similart to jQuery $('.title'))
  - `.find` - find element with in DOM from `.get`
  - `.then` - wait for the element to be ready then do function, can also set timeout here
  - `.its` - find its property

### 2. Act - `click`

```javascript
describe('My First Test', function() {
    it('finds the content "type"', function() {
        cy.visit('https://example.cypress.io')

        cy.contains('type').click() // click on the focused element
    })
})
```

Actions

- `type` - type into selected the element
- `click` - click on the selected element
- `focus`
- `clear`
- `check` ...

### 3. Assert - `should`

``` javascript
describe('My First Test', function() {
  it('clicking "type" navigates to a new url', function() {
    cy.visit('https://example.cypress.io')

    cy.contains('type').click()

    // Should be on a new URL which includes '/commands/actions'
    cy.url().should('include', '/commands/actions')  // assert on url (cy.url())

    // Get an input, type into it and verify that the value has been updated
    cy.get('.action-email')
      .type('fake@email.com')
      .should('have.value', 'fake@email.com')  // assert on the element class action email
  })
})
```

[*Assertion Guide*](https://docs.cypress.io/guides/core-concepts/introduction-to-cypress.html#Assertions) - documentation on how to assert

- Asserting class 
  - `cy.get('button').click().should('have.class', 'active')`
- Asserting response body 
  - `cy.request('/users/1').its('body').should('deep.eq', { name: 'Jane' })`

[Common assertion](https://docs.cypress.io/guides/references/assertions.html#Common-Assertions) - examples of assertion

---

## Testing strategies (Common issues)

### Setup & Teardown

- [`cy.exec`](https://docs.cypress.io/api/commands/exec.html) - execute bash command
- [`cy.task`](https://docs.cypress.io/api/commands/task.html) - run defined node.js script in pluginsFile
- [`cy.request`](https://docs.cypress.io/api/commands/request.html) - make HTTP request

Setup can be done using `beforeEach` within each test case and `afterEach` for tear down.

```javascript
describe('The Home Page', function () {
  beforeEach(function () {
    // reset and seed the database prior to every test
    cy.exec('npm run db:reset && npm run db:seed')  // 
  })

  it('successfully loads', function() {
    cy.visit('/')
  })
})
```

---

##  Best Practices

### Selecting 


[^1]: Kitchen sink or [Everything but the kinchen sink](https://dictionary.cambridge.org/dictionary/english/everything-but-except-the-kitchen-sink) - a much larger number of things than is necessary