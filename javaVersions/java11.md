🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️
☑️ • ‣ → ⁕ ⏺️

# ⏺️ Java 11

## ➡️ Local-Variable Syntax for Lambda Parameters (var):

## ➡️ HTTP Client API (Standardized): 🟠🟠🟠

- Standard Java library (`java.net.http`) supports both `HTTP/1.1` and `HTTP/2` protocols.

#### 🟦 Key Features

##### 🔵 HTTP/1.1 and HTTP/2 Support:

- Automatically negotiates `HTTP/2` when supported by the server; falls back to `HTTP/1.1` otherwise.
- Supports `HTTP/2` features like multiplexing (multiple requests over a single connection) and server push.

##### 🔵 Synchronous and Asynchronous Requests:

- **Synchronous:** Blocks until the response is received (`client.send()`).
- **Asynchronous:** Non-blocking with `CompletableFuture` (`client.sendAsync()`).

##### 🔵 Request Customization:

- Supports all standard HTTP methods (`GET`, `POST`, `PUT`, `DELETE`, etc.).
- Allows custom `headers`, `query parameters`, and request bodies (**e.g.**, `JSON`, form data).
- Configurable timeouts and redirects.

##### 🔵 Response Handling:

- Provides flexible body handlers for processing responses as `strings`, `byte arrays`, `files`, or `streams`.
- Handles status codes, headers, and errors.

##### 🔵 Connection Management:

- Supports connection pooling for reusing TCP connections.
- Configurable `SSL/TLS` settings and proxy support.

##### 🔵 Authentication:

- Built-in support for Basic Authentication and extensible for custom schemes (**e.g.**, `OAuth`).

##### 🔵 WebSocket Support:

- Includes a `WebSocket` client for real-time, bidirectional communication.

#### 🟦 Core Components

##### 🔵 1. HttpClient

- The HttpClient is the central class for sending requests and managing configurations like timeouts, proxies, and SSL settings.
- Created using HttpClient.newBuilder() or HttpClient.newHttpClient()

##### 🔵 2. HttpRequest

- Represents an immutable HTTP request, built using HttpRequest.newBuilder().
- Configures the HTTP method, URL, headers, and optional body.
- Supports query parameters via URI construction.

##### 🔵 3. HttpResponse

- Represents the server’s response, including status code, headers, and body.
- Body is processed using a BodyHandler (e.g., ofString(), ofByteArray(), ofFile()).

##### 🔵 4. BodyHandlers and BodyPublishers

- **BodyHandlers:** Define how to process the response body (**e.g.**, `ofString()`, `ofInputStream()`, `ofFile()`).
- **BodyPublishers:** Define how to send the request body (**e.g.**, `ofString()`, `ofByteArray()`, `ofFile()`).

## ➡️ String API Enhancements: 🟠

## ➡️ Removal of Java EE and CORBA Modules:

## ➡️ Z Garbage Collector (Experimental):

## ➡️ Flight Recorder:

## ➡️ Nest-Based Access Control:

## ➡️ Unicode 10 Support:

###
