========== Question ==========  

### What is the best way to structure URLs for nested resources?  

========== Answer ==========  

For nested resources, use URLs that represent the relationship between them. Examples:

-   `GET /schools/2/students` retrieves all students from school with ID 2.

-   `GET /schools/2/students/31` retrieves details of student 31 from school 2.

-   `DELETE /schools/2/students/31` removes student 31 from school 2.

-   `PUT /schools/2/students/31` updates information for student 31. Only use `PUT` on resource URLs, not on collections.

-   `POST /schools` creates a new school and returns details of the newly created school. Use `POST` on collection URLs.

========== Id ==========  
102

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#102-What-is-the-best-way-to-structure-urls-for

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
