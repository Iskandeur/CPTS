[[HTTP]] status codes are issued by a [[Web Server]] in response to a client's request made to the server. They indicate whether a specific HTTP request has been successfully completed. Responses are grouped into five classes: informational responses (1xx), successful responses (2xx), redirects (3xx), client errors (4xx), and server errors (5xx).

Understanding these codes is crucial for [[Web Enumeration]], diagnosing web application issues, and interpreting tool output.

Source: https://en.wikipedia.org/wiki/List_of_HTTP_status_codes

## Status Code Classes

|Status Code|Name|Description|Common Use Cases|
|---|---|---|---|
|**1xx Informational**||Responses indicating the request was received and understood, and the process is continuing.||
|100|Continue|The server has received the request headers, and the client should proceed to send the request body.|Used in large POST/PUT requests to confirm headers are valid before sending the payload.|
|101|Switching Protocols|The server agrees to switch protocols as requested by the client (e.g., upgrading to WebSocket).|WebSocket handshakes or other protocol upgrades.|
|102|Processing|The server is processing the request but has not yet completed it (non-standard, defined in WebDAV).|Long-running WebDAV operations.|
|103|Early Hints|The server sends preliminary response headers to allow the client to start preloading resources.|Preloading resources like CSS or JavaScript before the final response.|
|**2xx Success**||Responses indicating the request was successfully received, understood, and accepted.||
|200|OK|The request was successful, and the server is returning the requested resource.|Standard response for successful GET or POST requests.|
|201|Created|The request was successful, and a new resource was created as a result.|Successful POST or PUT requests creating a new resource (e.g., creating a new user).|
|202|Accepted|The request has been accepted for processing, but processing is not complete.|Asynchronous processing, such as batch jobs or queued tasks.|
|203|Non-Authoritative Information|The response is a transformed or cached version of the original resource, not directly from the origin server.|Proxy or CDN responses with modified content.|
|204|No Content|The request was successful, but there is no content to return.|Successful DELETE requests or updates with no response body.|
|205|Reset Content|The request was successful, and the client should reset the document view (e.g., clear a form).|Rarely used; form submissions that require resetting the client UI.|
|206|Partial Content|The server is delivering only part of the resource due to a range header sent by the client.|Resuming downloads or streaming media with range requests.|
|207|Multi-Status|Provides status for multiple independent operations (used in WebDAV).|WebDAV operations like batch resource updates.|
|208|Already Reported|Used in WebDAV to avoid enumerating the same resource multiple times in a response.|WebDAV PROPFIND requests with nested resources.|
|226|IM Used|The server fulfilled a request for the resource, and the response is a representation of the result of one or more instance-manipulations (used in Delta encoding).|Rarely used; Delta encoding in HTTP.|
|**3xx Redirection**||Responses indicating further action is needed to complete the request, often involving redirection.||
|300|Multiple Choices|The requested resource has multiple representations, and the client must choose one.|Rarely used; offering multiple formats (e.g., HTML vs. PDF).|
|301|Moved Permanently|The requested resource has been permanently moved to a new URL.|Permanent URL changes, SEO-friendly redirects.|
|302|Found|The requested resource is temporarily located at a different URL.|Temporary redirects, often misused for permanent redirects.|
|303|See Other|The response to the request can be found at a different URL, and the client should use a GET request to retrieve it.|Redirecting after a POST to prevent resubmission (Post/Redirect/Get pattern).|
|304|Not Modified|The resource has not been modified since the last request (based on headers like If-Modified-Since).|Caching; used to save bandwidth when content hasn't changed.|
|305|Use Proxy|The requested resource must be accessed through a proxy (deprecated).|Deprecated; historically used for proxy redirection.|
|306|(Unused)|Reserved and unused in modern HTTP standards.|Not used.|
|307|Temporary Redirect|The requested resource is temporarily located at a different URL, and the original method should be used.|Temporary redirects preserving the HTTP method (e.g., POST).|
|308|Permanent Redirect|The requested resource has been permanently moved to a new URL, and the original method should be used.|Permanent redirects preserving the HTTP method.|
|**4xx Client Error**||Responses indicating an error in the client's request.||
|400|Bad Request|The server cannot process the request due to malformed syntax or invalid parameters.|Invalid JSON, missing required fields, or malformed URLs.|
|401|Unauthorized|The request requires authentication, and the client has not provided valid credentials.|Missing or invalid authentication tokens.|
|402|Payment Required|Reserved for future use; sometimes used experimentally for paid APIs.|Rarely used; potential use in paywalled content or APIs.|
|403|Forbidden|The client is authenticated but lacks permission to access the resource.|Access control restrictions, such as role-based access denial.|
|404|Not Found|The requested resource could not be found on the server.|Broken links or nonexistent resources.|
|405|Method Not Allowed|The HTTP method used is not supported for the requested resource.|Attempting a POST on a GET-only endpoint.|
|406|Not Acceptable|The server cannot produce a response matching the client's Accept headers.|Client requests unsupported content types (e.g., JSON instead of XML).|
|407|Proxy Authentication Required|The client must authenticate with a proxy to proceed.|Proxy servers requiring authentication.|
|408|Request Timeout|The server timed out waiting for the client's request.|Slow or stalled client requests.|
|409|Conflict|The request could not be completed due to a conflict with the current state of the resource.|Concurrent edits in APIs (e.g., version conflicts in PUT requests).|
|410|Gone|The requested resource is permanently unavailable and will not be available again.|Removed resources with no forwarding address.|
|411|Length Required|The server requires a Content-Length header, which was not provided.|Rare; malformed POST/PUT requests missing Content-Length.|
|412|Precondition Failed|One or more preconditions in the request headers (e.g., If-Match) were not met.|Conditional requests failing, such as ETag mismatches.|
|413|Payload Too Large|The request payload exceeds the server's size limits.|Uploading files larger than the server's maximum allowed size.|
|414|URI Too Long|The request URI exceeds the server's length limits.|Extremely long query strings or URLs.|
|415|Unsupported Media Type|The request's Content-Type is not supported by the server.|Sending XML to an API that only accepts JSON.|
|416|Range Not Satisfiable|The requested range of the resource cannot be provided (e.g., out-of-bounds range).|Invalid range requests in partial content scenarios.|
|417|Expectation Failed|The server cannot meet the requirements of the Expect header.|Rare; issues with the Expect: 100-continue header.|
|418|I'm a Teapot|A humorous code indicating the server refuses to brew coffee because it is a teapot (from an April Fools' RFC).|Rarely used; mostly for fun or Easter eggs.|
|421|Misdirected Request|The request was directed to a server that is not able to produce a response.|Misconfigured servers or incorrect routing.|
|422|Unprocessable Content|The request was well-formed but semantically invalid (used in WebDAV).|Invalid data in APIs (e.g., missing required fields in JSON).|
|423|Locked|The resource is locked and cannot be accessed (used in WebDAV).|WebDAV resources locked by another user or process.|
|424|Failed Dependency|The request failed because a dependent operation failed (used in WebDAV).|WebDAV batch operations where one failure halts others.|
|425|Too Early|The server is unwilling to process a request that might be replayed (used in early data scenarios).|TLS 1.3 early data rejection.|
|426|Upgrade Required|The client must upgrade to a different protocol to proceed.|Forcing clients to use HTTPS instead of HTTP.|
|428|Precondition Required|The server requires the request to include preconditions (e.g., If-Match).|Preventing accidental overwrites in APIs.|
|429|Too Many Requests|The client has sent too many requests in a given time frame (rate limiting).|API rate limiting or DDoS protection.|
|431|Request Header Fields Too Large|The request headers exceed the server's size limits.|Overly large headers, such as massive cookies.|
|451|Unavailable For Legal Reasons|The resource is unavailable due to legal restrictions.|Content blocked due to government censorship or DMCA takedowns.|
|**5xx Server Error**||Responses indicating an error on the server's side.||
|500|Internal Server Error|A generic error indicating the server encountered an unexpected condition.|Unhandled exceptions or server misconfigurations.|
|501|Not Implemented|The server does not support the requested functionality.|Unsupported HTTP methods or unimplemented features.|
|502|Bad Gateway|The server, acting as a gateway or proxy, received an invalid response from an upstream server.|Proxy or load balancer issues with backend servers.|
|503|Service Unavailable|The server is temporarily unavailable, often due to maintenance or overloading.|Server maintenance or traffic overload.|
|504|Gateway Timeout|The server, acting as a gateway or proxy, did not receive a timely response from an upstream server.|Slow or unresponsive backend servers.|
|505|HTTP Version Not Supported|The server does not support the HTTP protocol version used in the request.|Rare; using an unsupported HTTP version (e.g., HTTP/0.9).|
|506|Variant Also Negotiates|A server configuration error where a variant resource negotiates incorrectly (used in transparent content negotiation).|Rare; misconfigured content negotiation.|
|507|Insufficient Storage|The server cannot store the representation needed to complete the request (used in WebDAV).|WebDAV storage limits exceeded.|
|508|Loop Detected|The server detected an infinite loop while processing the request (used in WebDAV).|WebDAV operations causing recursive dependencies.|
|510|Not Extended|The server requires further extensions to fulfill the request.|Rare; used in scenarios requiring custom HTTP extensions.|
|511|Network Authentication Required|The client must authenticate to access the network (e.g., captive portals).|Captive portals in public Wi-Fi networks.|

## Notes

- **Source**: This table is based on RFC 9110 (HTTP Semantics), RFC 7231, and related IETF standards, with additional context from common usage.
- **Non-Standard Codes**: Some codes (e.g., 418, 429, 451) are widely used but originated from extensions or non-standard RFCs.
- **WebDAV**: Codes like 207, 422, 423, 424, 507, and 508 are primarily used in WebDAV (RFC 4918).
- **Deprecated Codes**: Codes like 305 are deprecated and should not be used in modern applications.