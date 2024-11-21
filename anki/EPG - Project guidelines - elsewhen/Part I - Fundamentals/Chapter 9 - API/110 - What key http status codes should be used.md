========== Question ==========  

### What key HTTP status codes should be used in API responses, and what do they indicate?  

========== Answer ==========  

Key HTTP status codes include:

-   **200 OK**: Successful `GET`, `PUT`, or `POST` requests.

-   **201 Created**: New resource successfully created (used with `POST`).

-   **204 No Content**: Success with no content to return (common for `DELETE` success).

-   **304 Not Modified**: Indicates a cached version can be used, reducing data transfer.

-   **400 Bad Request**: The request could not be understood or was incorrect.

-   **401 Unauthorized**: Request is missing valid credentials; re-authentication needed.

-   **403 Forbidden**: Server understood the request but refuses authorization.

-   **404 Not Found**: The requested resource does not exist.

-   **500 Internal Server Error**: A valid request could not be processed due to server error.

========== Id ==========  
110

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#110-What-key-http-status-codes-should-be-used

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
