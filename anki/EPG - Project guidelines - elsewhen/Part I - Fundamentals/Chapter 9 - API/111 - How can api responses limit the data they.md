========== Question ==========  

### How can API responses limit the data they return?  

========== Answer ==========  

Use a **fields query parameter** to specify a comma-separated list of fields to include in the response. For example:

```
GET /students?fields=id,name,age,class
```

This limits the data returned, improving performance and minimizing data transfer.

========== Id ==========  
111

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#111-How-can-api-responses-limit-the-data-they

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
