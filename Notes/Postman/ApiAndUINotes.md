# API and UI Notes

## UI, API, and Database

- **UI (Frontend)** is the interface users interact with.
- **API (Backend)** handles requests and business logic.
- **Database** stores data permanently.
- **UI does not directly access the database**.
- **Flow:** UI → API → DB → API → UI

**Example:**

User logs in → UI sends request → API validates using DB → API responds to UI.

<aside>
🧠

**Analogy (Restaurant):**

- UI = Waiter (takes your order)
- API = Kitchen staff (prepares the food using rules)
- DB = Pantry/Fridge (stored ingredients / saved data)

You don’t go inside the kitchen and pantry directly — you place an order via the waiter.

</aside>

---

## When APIs Are Triggered

- Button click (Login, Submit)
- Typing input (Search, autocomplete)
- Page load or refresh

---

## API Request Components

- **Base URL**: Backend server address (domain or IP).
- **Endpoint**: API path.
- **HTTP Verb**: Operation type.
- **Headers**: Additional request information.
- **Body / Payload**: Data sent to server.

---

## HTTP Verbs and Operations

- **POST** → Create
- **GET** → Read
- **PUT / PATCH** → Update
- **DELETE** → Delete

<aside>
🧠

**Analogy (Library):**

GET = read a book

POST = add a new book record

PUT/PATCH = edit book details

DELETE = remove the book record

</aside>

---

## Data Transfer Format

- UI and API communicate using **JSON**.
- **Content-Type** header specifies the data format.

---

## Authentication and Authorization

- **Authentication**: Verifies user identity.
- **Authorization**: Verifies access permissions.
- Authentication happens before authorization.

**Example:**

Login checks credentials, role decides access.

<aside>
🧠

**Analogy (Office building):**

Authentication = showing who you are at reception (ID check)

Authorization = whether your badge opens the 5th-floor door (permission)

</aside>

---

## Token-Based Access

- Login API returns a **token**.
- Token is sent in **Authorization header** for protected APIs.
- Backend validates token before processing request.

**Example:**

`Authorization: Bearer <token>`

<aside>
🧠

**Analogy:** Token is like a **temporary entry pass** you carry after logging in. You show it on every request so the server doesn’t have to re-check your password each time.

</aside>

---

## Viewing APIs from UI

- Open **DevTools (F12)**.
- Go to **Network → Fetch/XHR**.
- View:
    - URL and endpoint
    - Headers
    - Payload
    - Status code
    - Response

---

## Postman Collections

- **Collection** is a group of APIs for one flow.
- Different flows use different collections.

**Example:**

Login flow, InWarranty flow.

---

## Volatile and Persistent Memory

- **Volatile Memory**: Data lost on power off (RAM, cache).
- **Persistent Memory**: Data retained (Disk, Database).

---

## API Responses

- **Status Code** shows request result.
- **Response Time** indicates performance.
- **Response Body** contains returned data.
- **Response Headers** provide metadata.

---

## Common Status Codes

- **200** → OK
- **201** → Created
- **400** → Bad Request
- **401** → Unauthorized
- **403** → Forbidden
- **404** → Not Found
- **500** → Server Error

---

## Quick Revision

- UI → API → DB → API → UI
- JSON + Content-Type
- POST, GET, PUT, DELETE
- Authentication ≠ Authorization
- Token in Authorization header
- Network → Fetch/XHR for debugging

---
