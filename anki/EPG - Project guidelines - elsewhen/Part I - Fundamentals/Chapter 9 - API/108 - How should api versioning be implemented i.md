========== Question ==========  

### How should API versioning be implemented in URLs?  

========== Answer ==========  

Use an **ordinal number with a "v" prefix** (e.g., `v1`, `v2`) for versioning and place it at the beginning of the URL to give it **higher scope**. For example:

```
http://api.domain.com/v1/schools/3/students
```


> Versioning is helpful for public APIs as it allows changes without breaking existing implementations that third-party services rely on.

**References**:

-   [RESTful API Design Tips: Versioning](https://apigee.com/about/blog/technology/restful-api-design-tips-versioning)

========== Id ==========  
108

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#108-How-should-api-versioning-be-implemented-i

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
