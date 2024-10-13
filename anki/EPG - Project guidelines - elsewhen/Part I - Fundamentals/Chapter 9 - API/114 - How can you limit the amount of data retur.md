========== Question ==========  

### How can you limit the amount of data returned in an API response?  

========== Answer ==========  

Use a fields query parameter that takes a comma-separated list of fields to include. For example:

```
GET /students?fields=id,name,age,class
```

========== Id ==========  
114

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#114-How-can-you-limit-the-amount-of-data-retur

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
````
QUESTION STATUS: Safe to store
