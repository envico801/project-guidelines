========== Question ==========  

### How should security exception messages be handled in API responses?  

========== Answer ==========  

Keep security exception messages as generic as possible. For instance, instead of saying 'incorrect password', reply with 'invalid username or password'. This prevents unknowingly informing the user that the username was correct and only the password was incorrect.

========== Id ==========  
117

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#117-How-should-security-exception-messages-be

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
