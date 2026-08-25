### What Postman is used for

- Postman is a tool for working with APIs. It is commonly used to do **API testing** (mostly **black-box testing**), where you validate the API based on its **request** and **response** behavior.
- If you were testing the internal code logic directly (unit tests, code-level tests), that would be closer to **white-box testing**.

### What we focus on while testing

- Request: method, URL, headers, params, body
- Response: status code, headers, body, response time

### Writing tests in Postman (Tests tab)

- Tests are typically written under the **Tests** (post-response script) tab for a request.
- Common things to validate:
    - **Status code** (e.g., 200, 201, 400)
    - **Response time** (assert within a reasonable range since it varies)
    - **Response body fields** (e.g., message, token)
    - **JSON schema** validation (structure + required fields)

### Idempotency (important HTTP concept)

- **POST is typically non-idempotent**: calling it multiple times can create different results each time (e.g., generating a new token on each login).
- Many other methods are typically **idempotent** (e.g., GET, PUT), meaning repeating the same request should produce the same result (as far as the server state is concerned).
- HTTP is **stateless**: each request is evaluated independently; the server doesn’t automatically “remember” what happened previously unless state is stored (e.g., sessions, tokens, database).

### ChaiJS in Postman

- Postman includes **ChaiJS** assertions via `pm.expect(...)`.
- You’ll often use:
    - `to.eql(...)` for equality
    - `to.have.length(...)` for length checks
    - `to.be.a(...)` / `to.be.an(...)` for type checks
    - `to.be.not.NaN` for numeric sanity checks

### Callback / anonymous functions in tests

- A function without a name is an **anonymous function** (sometimes called an inline function).
- In Postman, we commonly pass an anonymous function as a parameter to `pm.test`:

```jsx
pm.test("Verify login test", function () {
  // assertions...
})
```

### Guidelines: keep tests small & independent

- Keep each test as small as possible.
- Prefer: **one test checks one thing**.
- Avoid complex logic inside tests:
    - avoid loops
    - avoid conditional statements
    - avoid local variables unless truly necessary
    - avoid exceptions/try-catch inside tests
- Tests should be **independent** of each other.
- **Assertions are mandatory** (a test without an assertion doesn’t validate anything).

### JWT token validation (quick check)

- To inspect a JWT token, you can paste it into a **JWT decoder** and view the 3 parts:
    - Header
    - Payload
    - Signature
- Quick structural validation: a JWT should have **3 dot-separated segments**.

```jsx
pm.test("Token should look like a JWT", function () {
  pm.expect(token.split(".")).to.have.length(3)
})
```

### What is NaN?

- **NaN** means **Not a Number** (JavaScript value for an invalid number conversion).

### Example: validate a 10-digit numeric mobile number

```jsx
pm.test("mobile_number should be a 10-digit numeric string.", function () {
  pm.expect(pm.response.json().data.mobile_number.length).to.eql(10)

  let mobileNum = Number(pm.response.json().data.mobile_number)

  pm.expect(isNaN(mobileNum)).to.eql(false)
  pm.expect(mobileNum).to.be.not.NaN
})
```

### Collaboration

- Postman supports collaboration across teams (developers, testers, and product). If someone updates a collection, others can see the changes and stay in sync.

### API documentation

- Collections can serve as **living API documentation** (requests, examples, descriptions, and expected responses).

### Monitors (health checks)

- **Monitors** can run requests on a schedule to check the health of critical APIs.
- Example: run every day at **9:00 AM** to verify the API is up and returning expected results (similar to a scheduled job).

### Newman (CLI runner)

- **Newman** is the command-line runner for Postman collections.
- Useful for automation and CI/CD (for example, running in Jenkins pipelines).

### Data-driven testing

- You can parameterize requests using external data files like:
    - CSV
    - JSON

### Limitations / drawbacks (common in Postman-only testing)

- **Database validation** is not built-in. You usually need separate scripts/tools or a custom framework to validate DB state.
- **Complex end-to-end flows** are often easier to manage in a custom automation framework (better control, reusable code, reporting, integrations).
- **Parallel execution** is limited in Postman/Newman by default. Collections usually run **sequentially** unless you add additional tooling/approaches to parallelize.
