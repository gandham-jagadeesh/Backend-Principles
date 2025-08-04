# Introduction to Routing

Routing in the backend expresses the **"where"** of a request. It indicates where to send the intention or which resource to perform the action on. Routing is the combination of the **HTTP method** and the **route** (URL path), which maps to a handler or set of instructions on the server.

- **HTTP methods** (GET, POST, PATCH, etc.) describe the action to perform on a resource.
- **Routes** specify the location of the resource.
- Together, they form a **unique path** that maps to server-side logic, which performs business operations, accesses databases, and returns data.

Routing is a key concept in backend development because it determines how to handle incoming requests and return the appropriate responses.

---

# How Routing Works

- In web apps (e.g., React apps), routes like `/API/SL/books` are used to communicate with the backend.
- The server reads both the **HTTP method** and **route**, and uses them together to map to a specific handler.
- Different HTTP methods (e.g., GET and POST) can use the **same URL path** but perform different actions.
- Routing is essentially the server's logic for mapping requests to functions or handlers.

---

# Types of Routing

## Static Routes

- Static routes do **not** have variable parameters.
- Example: `/API/SL/books`  
  This route always returns the same type of data.
- These routes are consistent and predictable.

## Dynamic Routes

- Dynamic routes **include variable parameters**, such as `/API/SL/users/:ID`.
- The `:ID` acts as a **route parameter** that changes depending on the resource requested.
- The server extracts these parameters and uses them (e.g., to fetch a user by ID from the database).

---

# Dynamic Routes and Route Parameters

- Servers **match** the HTTP method and the route path to identify the correct handler.
- A colon (`:`) in the route (e.g., `:id`) signifies a **dynamic parameter**.
- Example: `GET /API/SL/users/123` retrieves the user with ID 123.
- These parameters make routes more **semantic** and **human-readable**.

Terminology:
- **Static routes** – fixed paths like `/API/books`.
- **Dynamic routes** – variable paths like `/API/users/:id`.
- **Route/path parameters** – values in the URL path used to identify specific resources.

---

# Path Parameters and Query Parameters

## Path Parameters

- Appear in the **URL path** (e.g., `/API/users/123`).
- Used to **identify specific resources** (like a user by ID).
- They are **semantic expressions** of what data is being requested.

## Query Parameters

- Used to send **additional data** in **GET** requests (which don’t have bodies).
- Appended after a `?` in the URL as **key-value pairs** (e.g., `/API/books?page=2`).
- Used for metadata like:
  - Pagination
  - Search queries
  - Sorting options

- Query parameters allow clients to customize the data they receive without modifying the path.

---

# Using Query Parameters

- Enable **pagination**: Clients can specify page size, current page, etc.
- Servers often have default settings (e.g., returning 20 results per request).
- Query params like `page=2` or `limit=10` control which part of the dataset is returned.
- Common for:
  - Fetching next/previous pages
  - Filtering/sorting data
  - Sending lightweight metadata in GET requests

---

# Nested Routes

- Nested routes add **semantic meaning** by nesting resources in the URL.
- Example:  
  - `/API/users` – Get all users  
  - `/API/users/123` – Get user 123  
  - `/API/users/123/posts` – Get posts from user 123  
  - `/API/users/123/posts/456` – Get post 456 from user 123

- Each level can have its own handler and logic.
- Useful for **medium-complexity APIs** where related data is grouped logically.

---

# Route Versioning and Deprecation

- **Versioning** adds a version to the API route (e.g., `/API/V1/users`) to support evolution without breaking existing clients.
- Allows:
  - Supporting multiple clients with different data needs.
  - Making **breaking changes** safely (e.g., in `/V2`).
  - Providing a **migration window** for older clients.
- Eventually, deprecated versions (like V1) can be **phased out**.

---

# Catch-all Routes

- Catch-all routes handle **undefined routes**.
- Instead of sending a null or broken response, they return a **user-friendly message**.
- Example:
  - If a user accesses `/API/non-existent`, the catch-all route will send a 404 response like `"Route not found"`.

- Ensures:
  - Clear communication to clients.
  - Cleaner fallback experience.
  - Better debugging and user experience.

---

# Conclusion

Understanding routing is essential in backend development:

- It defines how the server processes incoming requests.
- Involves:
  - Static & dynamic routes
  - Path & query parameters
  - Nested routes
  - Versioning & deprecation
  - Catch-all routes

Mastering these concepts enables backend engineers to build flexible, maintainable APIs and efficiently manage communication between clients and servers.
