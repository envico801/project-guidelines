========== Question ==========  

### When are verbs appropriate in API URLs?  

========== Answer ==========  

Use verbs in **non-resource URLs** when the endpoint doesn’t return a resource but performs an action, delivering the result. These are not CRUD operations. Example:

```
/translate?text=Hallo
```


> For CRUD operations, use HTTP methods on resource or collection URLs. Verbs in this context generally refer to **Controllers**, and typically only a few are needed.

**References**:

-   [API Guidelines: Controller Usage](https://github.com/byrondover/api-guidelines/blob/master/Guidelines.md#controller)

========== Id ==========  
103

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#103-When-are-verbs-appropriate-in-api-urls

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
