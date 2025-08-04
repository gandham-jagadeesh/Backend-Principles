# Introduction to Serialization and Deserialization

Serialization and deserialization are key concepts in backend engineering, especially when clients (e.g., browsers) communicate with servers over networks such as HTTP, gRPC, or WebSocket.

- The client is typically a JavaScript application built using frameworks like React or Angular.
- It sends an HTTP request that includes a URL, headers, and a request body with data.
- The server, possibly written in a different language like Rust, needs to understand and process this data despite language and type differences.

---

# Understanding the OSI Model

To understand how data moves across the internet, it's helpful to learn the OSI model:

- The OSI (Open Systems Interconnection) model has layers like Application, Transport, Network, and Physical.
- Each layer handles a specific part of the data transmission process.
- Both the client and server rely on these layers to send and receive data, but backend engineers mainly focus on the Application layer.

---

# Why Serialization and Deserialization?

Serialization and deserialization make communication between different systems and languages possible:

- **Serialization** converts data into a common, standard format for transmission (e.g., from JavaScript objects to JSON).
- **Deserialization** converts the data back into a usable format on the server (e.g., into Rust structs).
- This enables domain-agnostic and language-agnostic communication.

---

# Communication Standards

To communicate effectively across different systems, we need common standards:

- These standards define how data should be formatted, transmitted, and interpreted.
- Serialization acts as the bridge, making it possible to send meaningful data regardless of the programming language or platform used.

---

# HTTP and REST APIs in Backend Engineering

HTTP is the most common protocol used for communication between clients and servers:

- REST APIs built on HTTP are widely used in modern web applications.
- Understanding HTTP methods, request/response structure, and status codes is essential for backend engineers.
- Serialization is often used in this context to structure data using JSON.

---

# Databases in Backend Engineering

Databases store the data that backend applications work with:

- **Relational Databases:** PostgreSQL, MySQL, SQLite  
- **Non-relational Databases:** MongoDB, DynamoDB

PostgreSQL is a common choice in both startups and large-scale applications.

---

# Serialization Standards

There are several popular serialization formats:

## Text-Based Formats:
- JSON (JavaScript Object Notation)
- YAML (YAML Ain’t Markup Language)
- XML (Extensible Markup Language)

## Binary Formats:
- Protocol Buffers (Protobuf)

JSON is by far the most widely used format—responsible for about 80% of client-server data communication.

---

# JSON as a Serialization Standard

JSON is lightweight, human-readable, and widely supported:

- Originally from JavaScript, but used across all languages.
- Common in config files, APIs, and logging.

### JSON Structure:
- Objects start and end with `{}`.
- Keys must be in double quotes.
- Values can be:
  - Strings
  - Numbers
  - Booleans
  - Arrays
  - Nested objects

This flexible structure makes JSON ideal for transmitting complex data between systems.

---

# JSON in Request and Response Flows

In a typical client-server interaction:

1. The client sends a request (e.g., a POST) with JSON data in the body.
2. The server reads, deserializes, and processes the data.
3. The server responds with JSON.
4. The client parses and renders the result.

This flow ensures consistent and structured communication using a shared standard.

---

# Mental Model for Backend Engineers

Backend engineers should:

- Focus on the **Application Layer** of the OSI model.
- Assume the client and server follow the same data format standard (usually JSON).
- Understand that lower-level steps like IP packets and physical transmission are abstracted away.

---

# Summary: Purpose of Serialization and Deserialization

Serialization and deserialization:

- Allow consistent data formatting between systems.
- Enable interoperability between different domains and programming languages.
- Are essential for communication in distributed systems, especially over the web.

Mastering these concepts is foundational for becoming a competent backend engineer.
