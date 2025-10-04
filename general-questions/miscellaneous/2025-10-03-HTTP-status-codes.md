# HTTP Status Codes — 2025-10-03

**Difficulty:** beginner-intermediate

**Summary:** Choosing the correct HTTP status code is fundamental to designing clear, reliable, and predictable APIs that clients can interact with intelligently.

## Initial Thoughts

HTTP status codes are a standardized language that a server uses to communicate the outcome of a client's request. They are the essential feedback mechanism of the web. For a system designer, they are not just error numbers; they are a contract that defines how different parts of a distributed system should behave in response to an action.

They are grouped into five classes:
* **2xx (Success):** The request succeeded.
* **3xx (Redirection):** The client needs to go somewhere else.
* **4xx (Client Error):** The client made a mistake.
* **5xx (Server Error):** The server made a mistake.

Understanding the key codes in each class is crucial for designing everything from simple web apps to complex microservice architectures.

---

## 2xx Success Codes 

These codes indicate that the client's request was successfully processed.

#### `200 OK`
* **Meaning:** The standard, generic success response.
* **Real-World Scenario:** A browser requests a user's profile page (`GET /api/users/me`). The server finds the user and sends back their information in a JSON object with a `200` status.

#### `201 Created`
* **Meaning:** The request was successful, and a new resource was created.
* **Real-World Scenario:** A user signs up for a new account by submitting a form (`POST /api/users`). The server creates the user in the database and responds with `201`. The response should also include a `Location` header (e.g., `Location: /api/users/12345`) pointing to the URL of the newly created user.

#### `204 No Content`
* **Meaning:** The server successfully processed the request but has no data to return.
* **Real-World Scenario:** A user clicks "delete" on one of their photos (`DELETE /api/photos/abcde`). The server successfully deletes the photo from storage and the database. Since there's no data to return, it sends back an empty `204` response. This tells the frontend client the operation worked and it can now remove the photo from the UI.

#### `202 Accepted`
* **Meaning:** The server has received the request for processing, but the processing has not been completed. The request is valid, but the work will be done later.
* **Real-World Scenario:** A user requests to export their entire transaction history as a CSV file (`POST /api/exports`). This might take several minutes. The server immediately responds with `202` to let the client know the job has been queued. The client can then poll a status endpoint or wait for a notification (like a webhook or WebSocket message) to know when the file is ready for download.

---

## 3xx Redirection Codes ↪

These codes instruct the client to go to a different location.

#### `301 Moved Permanently`
* **Meaning:** The requested resource has been permanently moved to a new URL.
* **Real-World Scenario:** A company rebrands and changes its domain from `old-company.com` to `new-company.com`. To preserve SEO rankings and avoid breaking user bookmarks, they configure their servers to respond to all requests for the old domain with a `301` redirect to the corresponding page on the new domain.

#### `307 Temporary Redirect`
* **Meaning:** The resource is temporarily located at a different URL. The client should continue to use the original URL for future requests.
* **Real-World Scenario:** A user clicks on a `tiny.url/g8` link. Our URL shortener service looks up `g8`, finds the long URL, and responds with a `307` and a `Location` header. This forces the browser to check with our service every time, allowing us to track the click before sending the user to the final destination.

#### `304 Not Modified`
* **Meaning:** The client already has the latest version of the resource in its cache.
* **Real-World Scenario:** A user revisits a blog post. Their browser sends a request with an `If-None-Match` header containing an "ETag" (a version identifier for the content it has cached). The server checks if the post has been updated. If not, it responds with an empty `304` status, telling the browser to use its local copy. This saves significant bandwidth and makes the page load instantly.

---

## 4xx Client Error Codes 

These codes indicate that the client has made an error.

#### `400 Bad Request`
* **Meaning:** A generic error for when the server cannot process the request due to a client-side issue (e.g., malformed syntax).
* **Real-World Scenario:** A developer using your API tries to create a new product but sends a malformed JSON payload (e.g., a comma is missing). The server fails to parse the JSON and responds with `400`, often with a message explaining the syntax error.

#### `401 Unauthorized`
* **Meaning:** The request requires authentication, but the client has not provided any credentials, or the credentials are invalid.
* **Real-World Scenario:** A user tries to access their account dashboard (`GET /dashboard`) but their session has expired. The server responds with `401`. A well-designed frontend will intercept this response and automatically redirect the user to the login page.

#### `403 Forbidden`
* **Meaning:** The server understands the request, but refuses to authorize it. The client's identity is known, but they don't have the necessary permissions.
* **Real-World Scenario:** A standard user (authenticated, so no `401`) tries to access an admin-only page (`GET /admin`). The server checks their role, sees they are not an administrator, and responds with `403`.

#### `404 Not Found`
* **Meaning:** The server cannot find the requested resource.
* **Real-World Scenario:** A user clicks on a link to a product that was recently deleted, or mistypes a URL. The server looks for the resource in the database, doesn't find it, and returns a `404` page.

#### `429 Too Many Requests`
* **Meaning:** The user has sent too many requests in a given amount of time.
* **Real-World Scenario:** To protect a login endpoint from brute-force attacks, you implement **rate limiting**. If an IP address makes more than 10 failed login attempts in one minute, the server will start responding to further requests from that IP with `429`, potentially including a `Retry-After` header to tell the client when it can try again.

---

## 5xx Server Error Codes 

These codes indicate that the server is aware it has erred or is incapable of performing the request.

#### `500 Internal Server Error`
* **Meaning:** A generic, unexpected error occurred on the server that it doesn't know how to handle.
* **Real-World Scenario:** A user is finalizing a purchase. The code that calls the payment processor has a bug and throws an unhandled exception (e.g., a `NullReferenceException`). The application's global error handler catches this, logs the detailed error for developers to fix, and sends a generic, user-friendly `500` response.

#### `503 Service Unavailable`
* **Meaning:** The server is not ready to handle the request. This is usually a temporary state.
* **Real-World Scenario:** You are performing a major database migration and need to take your application offline for 10 minutes. You configure your load balancer to temporarily stop sending traffic to your application servers and instead serve a static page with a `503` status, informing users that the site is under maintenance and to try again shortly.

#### `504 Gateway Timeout`
* **Meaning:** The server, while acting as a gateway or proxy, did not receive a timely response from an upstream server it needed to access to complete the request.
* **Real-World Scenario:** In a microservices architecture, the `Order Service` needs to call the `Inventory Service` to confirm an item is in stock. The `Inventory Service` is overloaded and takes too long to respond. The `Order Service` has a 10-second timeout, gives up, and returns a `504` to the user, indicating that it couldn't get the information it needed in time.

## Trade-offs / Considerations

* **Clarity and Predictability:** Using the correct, specific status code makes your API predictable and easier to debug for client developers. A `403` is much more informative than a generic `400`.
* **Client Behavior:** The code you choose directly influences how a well-behaved client will act. `301` causes caching, `429` should trigger backoff logic, and `503` implies a retry is worthwhile.
* **Monitoring & Alerting:** Your monitoring system should treat these codes differently. A sudden spike in `5xx` errors is a critical alert indicating your service is broken. A spike in `403` errors might indicate a widespread permissions issue or a potential security probe.

## Related

* **API Design & REST:** The principles for building web APIs, where proper use of HTTP status codes is a cornerstone.
* **Idempotency:** A concept where operations can be safely retried without changing the outcome. Essential for designing clients that can recover from `5xx` errors.
* **Circuit Breaker Pattern:** A design pattern where a client will stop trying to contact a service that is consistently returning `5xx` errors, preventing cascading failures.
* **Rate Limiting:** The technique of controlling the rate of traffic, implemented by returning `429` status codes.

## Futhur Readings
[link][https://developers.google.com/search/docs/crawling-indexing/http-network-errors]
