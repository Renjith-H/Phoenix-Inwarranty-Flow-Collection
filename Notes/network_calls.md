### Where to check network calls

- Open **DevTools** in the browser.
- Go to the **Network** tab.
- Use the **Fetch/XHR** filter to see only API calls.

### What you will observe (example: signing into the app)

- When you sign in to the Phoeix app, you will see multiple API calls.
- If you notice the **same endpoint called twice** (for example, two *user details* API calls), that is usually not ideal.
    - It can increase page load time.
    - It can indicate duplicate frontend triggers or inefficient state management.

### What to inspect in each call

- **Headers**
    - Authorization, content-type, cookies, etc.
- **Payload (Request body)**
    - The data being sent to the server.
- **Response**
    - Status code, response body, errors.

### Security check (important)

- If you can see a **password** or sensitive value in the payload in plain text, it is a security concern.
- In a secure setup:
    - Passwords should be sent only over **HTTPS**.
    - Sensitive values should not be logged or exposed.
    - If encryption is expected at the app level, verify that the value is not being sent in plain text.

### Track actions and the related APIs

- When you click **Create Job**, observe which new API calls appear.
- Do the same for other flows, for example:
    - Viewing **All jobs I created**
    - Opening a specific job
    - Editing or updating a job
    - Deleting a job

### Quick checklist (for revision)

- Check for duplicate API calls.
- Validate request payload and required headers.
- Confirm expected status codes (200, 201, 400, 401, 403, 500).
- Ensure no sensitive data is exposed in payloads/responses.
- Note any slow calls (high response time) or failures.
