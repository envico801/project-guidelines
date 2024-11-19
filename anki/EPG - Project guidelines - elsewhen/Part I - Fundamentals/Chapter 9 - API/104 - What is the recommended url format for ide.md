========== Question ==========  

### What is the recommended URL format for identifying specific resources?  

========== Answer ==========  

Use a **singular resource** that begins with a **collection** and ends with an **identifier**, for example:

```
/students/245743
/airports/kjfk
```

Avoid formats like:

```
GET /blogs/:blogId/posts/:postId/summary
```


> This structure targets a property rather than a resource. Instead, include the property as a parameter to simplify responses.

========== Id ==========  
104

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#104-What-is-the-recommended-url-format-for-ide

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
