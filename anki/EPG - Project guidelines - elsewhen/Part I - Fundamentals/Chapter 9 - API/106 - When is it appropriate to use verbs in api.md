========== Question ==========  

### When is it appropriate to use verbs in API URLs?  

========== Answer ==========  

Use verbs for non-resources, when your API doesn't return any resources but instead executes an operation and returns the result. These are not CRUD operations. For example:

```
/translate?text=Hallo
```

_Why:_

> Because for CRUD we use HTTP methods on `resource` or `collection` URLs. The verbs we were talking about are actually `Controllers`. You usually don't develop many of these. [read more...](https://github.com/byrondover/api-guidelines/blob/master/Guidelines.md#controller)

========== Id ==========  
106

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#106-When-is-it-appropriate-to-use-verbs-in-api

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
