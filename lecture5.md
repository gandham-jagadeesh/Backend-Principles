
# Backend Engineering: HTTP Protocol Overview

## Introduction

Backend engineering is a vast field, and this discussion focuses on topics used in most codebases, starting with the HTTP protocol.

HTTP is the medium through which browsers and servers communicate to send or receive data.

## HTTP Overview

HTTP is based on two main ideas:

- **Statelessness**: Each request carries all the necessary information, meaning the server doesn’t need to retain session information.
- **Client-Server Model**: The client (typically a browser or app) initiates communication, and the server processes the request and sends a response.

### Statelessness

The stateless model simplifies communication and enhances scalability since servers do not need to remember previous interactions.

### Client-Server Model

In this model, a client sends a request to a server. The server processes it and returns a response.

## Evolution of HTTP

Different versions of HTTP have evolved over time:

- **HTTP 1.0**: Basic functionality
- **HTTP 1.1**: Introduced persistent connections
- **HTTP 2.0**: Added multiplexing and improved performance
- **HTTP 3.0**: Built on QUIC for even better performance

## HTTP Messages

HTTP messages consist of **requests** and **responses**, with components like:

- Request methods (GET, POST, etc.)
- Resource URLs
- HTTP versions
- Headers
- Message bodies

### Structure of Messages

Request and response messages are structured with headers, blank lines, and optional bodies.

## HTTP Headers

Headers are key-value pairs that provide metadata about requests or responses. They’re essential because they deliver context and information without having to inspect the body.

Think of headers like parcel labels—they tell you what’s inside without opening the package.

### Types of HTTP Headers

- **Request Headers**: e.g., `User-Agent`, `Authorization`
- **General Headers**
- **Representation Headers**
- **Security Headers**: e.g., `Strict-Transport-Security`, `Content-Security-Policy`

## HTTP Methods

Common HTTP methods include:

- **GET**: Retrieve data
- **POST**: Create data
- **PUT**: Update or replace data
- **PATCH**: Modify part of the data
- **DELETE**: Remove data

Understanding method semantics is crucial for correct implementation.

## Idempotent vs Non-Idempotent Methods

- **Idempotent Methods**: Return the same result no matter how many times they’re called (GET, PUT, DELETE).
- **Non-Idempotent Methods**: Can produce different results on repeated calls (POST).

## OPTIONS Method and CORS Workflow

The `OPTIONS` method checks server capabilities for cross-origin requests (CORS).

CORS is a browser-enforced security policy that controls how web apps interact with resources on different domains.

### Simple Request Flow

- The browser sends an `Origin` header.
- The server includes an `Access-Control-Allow-Origin` header if the origin is allowed.

### Pre-flight Request Flow

Triggered when:

- The method is not GET, POST, or HEAD
- The request includes custom headers
- The content type is not simple

The browser sends an `OPTIONS` request before the actual request. The server responds with headers like:

- `Access-Control-Allow-Origin`
- `Access-Control-Allow-Methods`
- `Access-Control-Allow-Headers`

If the CORS policy allows it, the browser proceeds with the actual request.

## Response Codes

Response status codes help browsers and clients determine the result of a request.

### Categories of Response Codes

- **1xx (Informational)**
- **2xx (Success)**: e.g., 200 OK, 201 Created, 204 No Content
- **3xx (Redirection)**: e.g., 301 Moved Permanently, 302 Found, 304 Not Modified
- **4xx (Client Errors)**: e.g., 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 405 Method Not Allowed, 409 Conflict, 429 Too Many Requests
- **5xx (Server Errors)**: e.g., 500 Internal Server Error, 501 Not Implemented, 502 Bad Gateway, 503 Service Unavailable, 504 Gateway Timeout

These codes guide clients on how to handle responses appropriately.

## HTTP Caching

Caching reduces server load and improves performance by storing copies of responses.

Key caching headers:

- `Cache-Control`
- `ETag`
- `Last-Modified`

The server and client use these headers to determine if a cached version is valid or if a new request is needed.

## HTTP Content Negotiation

This allows clients and servers to agree on the best data format for communication.

Types of negotiation:

- **Media Type**: `Accept` header
- **Language**: `Accept-Language` header
- **Encoding**: `Accept-Encoding` header

The server responds in a format that matches the client's preferences.

## HTTP Compression

Compression reduces response size and bandwidth usage.

- Common formats: `gzip`, `deflate`
- The client indicates supported formats via `Accept-Encoding`
- The server compresses the response accordingly

## Persistent Connections and Keep-Alive

Introduced in HTTP/1.1, persistent connections allow reuse of a single TCP connection for multiple requests/responses.

- Managed using the `Connection` and `Keep-Alive` headers
- Reduces overhead from repeatedly opening/closing connections

## Multipart Data and Chunked Transfer

- **Multipart Requests**: Used for file uploads, breaking data into parts
- `boundary` parameter separates each part
- **Chunked Transfer**: Used to stream large responses in parts

## SSL, TLS, and HTTPS

- **SSL**: Outdated protocol for secure communication
- **TLS**: Modern replacement for SSL, provides encryption and authentication
- **HTTPS**: HTTP over TLS, secures communication between clients and servers
