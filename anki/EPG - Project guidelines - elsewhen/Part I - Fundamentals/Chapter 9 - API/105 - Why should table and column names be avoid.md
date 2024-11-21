========== Question ==========  

### Why should table and column names be avoided as resource names and properties in APIs?  

========== Answer ==========  

Avoid using `table_name` for resource names and `column_name` for resource properties because an API **should expose resources rather than the underlying database schema**. This abstraction helps keep the API design separate from database structure.

========== Id ==========  
105

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#105-Why-should-table-and-column-names-be-avoid

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
