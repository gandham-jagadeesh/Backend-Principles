# Authentication and Authorization: A Detailed Overview

## Introduction

* Authentication is the process of verifying a user's identity ("who are you?") in a specific context.
* Authorization determines what a user can do ("what can you do?") within that context, including their permissions and capabilities.

## History of Authentication

* **Pre-Industrial Societies:** Authentication was implicit, based on recognition within the community.
* **Medieval Period:** Seals were used as authentication tokens, relying on possession for verification.
* **Industrial Revolution:** The telegraph introduced shared secrets (passphrases) for secure message validation.
* **Early Computing (1960s):** Passwords were introduced for multi-user systems, initially stored in plain text.
* **Modern Era:** Hashing algorithms, asymmetric cryptography (PKI), and multi-factor authentication (MFA) emerged.
* **21st Century:** Cloud computing and mobile devices led to OAuth 2.0 and JWT.
* **Future:** Post-quantum cryptography may be necessary to counter quantum computing threats.

## Key Components of Authentication

### Sessions

* HTTP is stateless, treating each request as new.
* Sessions provide a server-side context for each user, allowing the server to "remember" them.
* A unique session ID is created and stored with user data.
* The session ID is sent to the client as a cookie.
* Session storage evolved from file-based to database-backed to distributed architectures (Redis, Memcached).

### JSON Web Tokens (JWT)

* JWTs offer advantages over traditional sessions, including offloading state from the server.
* JWTs are stateless mechanisms for transferring claims between parties.
* A JWT consists of three parts: header, payload, and signature.
* JWTs enable stateless authentication, eliminating the need for server-side session storage.
* JWTs include fields like "sub" (user ID) and "iat" (issued at).
* JWTs are scalable and portable, suitable for microservices.
* **Disadvantages:** Token impersonation and lack of immediate revocation.
* **Hybrid Approach:** Combines statelessness with a blacklist for token revocation.

### Cookies

* Cookies store information in a user's browser, sent back to the server with each request.
* During authentication, a cookie with an authorization token (JWT or session ID) is set.

## Types of Authentication

### Stateful Authentication

* The client sends credentials, and the server generates a session ID.
* Session data is stored in a system like Redis.
* The session ID is sent back to the client in an HTTP-only cookie.
* **Pros:** Centralized control, real-time information, easy revocation.
* **Cons:** Scalability issues, higher operational complexity in distributed systems.

### Stateless Authentication

* The server generates a signed JWT token after verifying credentials.
* The client sends the JWT token in the Authorization header.
* The server verifies the token using a secret key.
* **Pros:** Scalability, no session store dependency.
* **Cons:** Complex token revocation.

### API Key-Based Authentication

* Used to give access to servers catering to a specific UI.
* A cryptographically safe random string is generated.
* Commonly used in applications where a UI interacts with multiple servers (e.g., chatbots).
* API keys provide access to the server, not the UI.
* Ideal for machine-to-machine communication, where servers interact programmatically.

### OAuth and OpenID Connect

* Developed to address issues with password-based authentication.
* **Delegation:** One platform needs access to resources from another.
* OAuth (Open Authorization) was born in 2007 to share access without sharing passwords.
* Tokens with specific permissions are shared.
* **Components:** Resource owner, client, resource server, authorization server.
* **OAuth 1.0:** Clients request access to resources on behalf of a user.

  * **Limitations:** Complex implementation, error-prone cryptographic signatures.
* **OAuth 2.0:** Introduced bearer tokens and different flows based on app type.

  * **Flows:** Authorization code flow, implicit flow, client credentials flow, device code flow.
  * OAuth 2.0 is primarily for authorization, not authentication.
* **OpenID Connect (OIDC):** Introduced in 2014 to address authentication, building on OAuth 2.0.

  * Extended OAuth 2.0 with an ID token (JWT).
  * The ID token contains user information (ID, login time, profile).
  * Enables "Sign in with..." features.
  * Allows platforms to outsource authentication.
  * OAuth 2.0 and OpenID Connect ensure users only access resources they have permission for.

## Choosing an Authentication Technique

* **Stateful:** Web app-based authentication.
* **Stateless:** APIs, scalable systems with distributed servers.
* **OAuth:** Third-party integrations, login via external providers.
* **API Key:** Server-to-server or machine-to-machine communication.

## Authorization

* Authorization determines what actions a user can perform after authentication.
* It grants special permissions to certain users (administrators).
* Providing specific permissions to specific users is authorization.
* Not all users have the same level of access.

### Role-Based Access Control (RBAC)

* Admins assign different permissions to members (read/write).
* Different roles have different sets of permissions.
* The server checks the user's role and grants/denies access.
* A "forbidden" error (403) indicates insufficient permissions.

## Security Considerations

* Avoid specific error messages during authentication to prevent attackers from gaining information.
* Use generic error messages like "authentication failed."
* Be aware of timing attacks, where attackers exploit response time differences.
* Use constant time operations and simulate response delays to defend against timing attacks.



# Web Security & Authentication Resources

## 🛡️ PortSwigger Web Security Academy
- [Web Security Academy - Main Page](https://portswigger.net/web-security)
- [Web Security Academy - Learning Paths](https://portswigger.net/web-security/learning-paths)

## 📚 OWASP Cheat Sheet Series
- [Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
- [Session Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html)
- [Cryptographic Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html)
- [Main Index (Highly Recommended)](https://cheatsheetseries.owasp.org/index.html)

## 🔐 Token & Identity Resources
- [JWT.io - JSON Web Tokens Explained & Debugger](https://jwt.io/)
- [FusionAuth Blog - Authentication & Authorization Topics](https://fusionauth.io/blog/category/essentials/)
- [Ping Identity - Security Resources & Articles](https://www.pingidentity.com/en/resources.html)

## 🔢 Cryptography
- [Wikipedia - Hash Function](https://en.wikipedia.org/wiki/Hash_function)
