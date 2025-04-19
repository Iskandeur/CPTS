# HTTP Headers

[[HTTP Headers]] are key-value pairs included in [[HTTP]] requests and responses. They provide essential metadata about the request, the response, or the resource being transferred.

## Header Types

*   **Request Headers:** Contain information about the client and the resource being requested (e.g., `User-Agent`, `Accept`, `Host`, `Authorization`).
*   **Response Headers:** Contain information about the server and the response being sent (e.g., `Server`, `Content-Type`, `Set-Cookie`, `Location`).
*   **Representation Headers (formerly Entity Headers):** Describe the payload body (e.g., `Content-Length`, `Content-Encoding`).

## Importance in Pentesting

Analyzing headers is crucial for:

*   [[Banner Grabbing]] (identifying server software via `Server` header)
*   Understanding authentication mechanisms (`Authorization`, `WWW-Authenticate`, `Set-Cookie`)
*   Detecting security misconfigurations (missing security headers like `Content-Security-Policy`, `Strict-Transport-Security`)
*   Identifying caching behavior (`Cache-Control`, `ETag`)
*   Exploiting vulnerabilities related to header processing. 