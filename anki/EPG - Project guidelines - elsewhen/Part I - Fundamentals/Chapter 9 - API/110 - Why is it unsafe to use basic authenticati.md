========== Question ==========  

### Why is it unsafe to use basic authentication without HTTPS?  

========== Answer ==========  

Avoid basic authentication over unsecured connections, as it transmits the user ID and password in plain text (encoded in base64, which is easily reversible). Without HTTPS, this information can be intercepted, posing a significant security risk.

**References**:

-   [Importance of HTTPS for Basic Authentication](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication)

========== Id ==========  
110

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#110-Why-is-it-unsafe-to-use-basic-authenticati

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
