========== Question ==========  

### What is the recommended format for URLs pointing to a specific resource?  

========== Answer ==========  

Always use a singular concept that starts with a collection and ends with an identifier, for example:

```
/students/245743
/airports/kjfk
```

Avoid URLs like this:

```
GET /blogs/:blogId/posts/:postId/summary
```

_Why:_

> This is not pointing to a resource but to a property instead. You can pass the property as a parameter to trim your response.

========== Id ==========  
104

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#104-What-is-the-recommended-format-for-urls-po

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
