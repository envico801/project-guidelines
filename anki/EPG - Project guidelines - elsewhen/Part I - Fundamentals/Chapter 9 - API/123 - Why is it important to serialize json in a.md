========== Question ==========  

### Why is it important to serialize JSON in API responses?  

========== Answer ==========  

Serializing JSON is crucial because a key concern with JSON encoders is preventing arbitrary JavaScript remote code execution within the browser or on the server (if using node.js). Using a proper JSON serializer to encode user-supplied data properly prevents the execution of user-supplied input on the browser.

========== Id ==========  
123

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#123-Why-is-it-important-to-serialize-json-in-a

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
