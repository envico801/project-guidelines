========== Question ==========  

### How should security exceptions be represented in API response messages?  

========== Answer ==========  

**Use generic messages** for security exceptions to avoid disclosing sensitive information. For instance, instead of saying "incorrect password," use a message like "invalid username or password" to prevent revealing that the username is correct.

========== Id ==========  
114

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#114-How-should-security-exceptions-be-represen

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
