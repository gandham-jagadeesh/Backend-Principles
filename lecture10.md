# Handlers, Services, Repositories, Middlewares, Controllers, Request Context

## Request - Response Life Cycle

Http → serialized → internet →

1. **Handler** (deserializes into native data types, also called binding)

   * If deserialization fails → 400 Bad Request (something wrong with the payload)
2. **Validation and transformation** on the request we got
3. **Calls the service layer** with transformed and validated payload
4. **Service** → calls → **Repository layer** or external API (e.g., sending email)
5. **Repository layer** → performs DB operations like fetch, insert, etc.
6. Data returns to **Service** → **Controller** → Controller sends data with appropriate response code like 200, 201, etc.

---

## Service Layer

* Does not deal with HTTP-specific logic
* Purely responsible for handling **business logic**

---

## Repository Layer

* Performs **DB operations**
* No method should do two things at once
* Example: a function with optional parameters

  * If parameters exist → return specific book
  * Else → return all books

---

## Middleware Layer

Flow:
Request → OS → Port forward → f1, f2... (middleware functions) → Routing → f1, f2... → Controllers → Service → Repository

* Middleware functions: `(req, res, next)`
* Forwards request from one middleware to the next using `next()`
* Can **send a response immediately** if validation or other logic fails

### Why Use Middleware?

* Middleware functions are reusable and can be used in different parts of the application

### Use Cases:

* **Security**: (CORS, rate limits, authorization)
* **Logging and monitoring**
* **Global error handling**:

  * Catches all unstructured errors
  * Sends proper error messages with status codes
  * Should be the **last** middleware
* **Compression**
* **Data parsing**

### Ordering:

* First middleware can be at most CORS
* Last should be global error handling
* Ordering is important and should be based on specific requirements

---

## Request Context (Shared State Scoped to One Request)

* Thousands of requests can come to the server
* Each request has its own **request scope + storage/state**, called **request context**
* One middleware can add data to the request, which the next middleware can access

### Example:

* `authMiddleware` → gets token ID, fetches user data, attaches it to `req.user`

---

## Good Patterns

* Make your API query params **optional** or assign **default values**
* Example:

  * `/books?sort=name`
  * `/books?sort=date`
  * `/books` → should still work by taking default sort values
