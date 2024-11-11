========== Question ==========  

### What are some important HTTP status codes to use in API responses, and what do they indicate?  

========== Answer ==========  

Some important HTTP status codes include:

> `200 OK` response represents success for `GET`, `PUT` or `POST` requests. `201 Created` for when a new instance is created. Creating a new instance, using `POST` method returns `201` status code. `204 No Content` response represents success but there is no content to be sent in the response. Use it when `DELETE` operation succeeds. `304 Not Modified` response is to minimize information transfer when the recipient already has cached representations. `400 Bad Request` for when the request was not processed, as the server could not understand what the client is asking for. `401 Unauthorized` for when the request lacks valid credentials and it should re-request with the required credentials. `403 Forbidden` means the server understood the request but refuses to authorize it. `404 Not Found` indicates that the requested resource was not found. `500 Internal Server Error` indicates that the request is valid, but the server could not fulfill it due to some unexpected condition.

========== Id ==========  
113

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#113-What-are-some-important-http-status-codes

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
