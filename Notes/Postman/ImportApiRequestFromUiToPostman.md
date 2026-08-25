- Open the application UI.
- Press **F12** to open **DevTools**.
- Go to **Network → Fetch/XHR**.
- Perform the action so the API request is triggered.
- Right-click the API request.
- Select **Copy → Copy as cURL (bash)**.
- Open **Postman**.
- Click **Import**.
- Paste the copied **cURL command**.
- Select or create a **collection**.
- Click **Import**.

**Result:**

The API request (URL, method, headers, payload) is recreated in Postman automatically.

<aside>
✅

**When to use this approach**

- When UI is working but you want to test the API faster in Postman
- When you want to debug headers/tokens/body without clicking UI repeatedly
</aside>
