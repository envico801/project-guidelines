========== Question ==========  

### How should authentication tokens be transmitted in API requests?  

========== Answer ==========  

Authentication tokens must be transmitted using the Authorization header on every request. For example: `Authorization: Bearer xxxxxx, Extra yyyyy`. They should not be transmitted in the URL.

========== Id ==========  
119

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#119-How-should-authentication-tokens-be-transm

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
