========== Question ==========  

### Why should basic authentication not be used unless over a secure connection (HTTPS)?  

========== Answer ==========  

Basic authentication should not be used without HTTPS because the token, user ID, and password are transmitted over the network as clear text (base64 encoded, which is reversible). This makes the basic authentication scheme insecure. [Read more...](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication)

========== Id ==========  
118

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#118-Why-should-basic-authentication-not-be-use

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
