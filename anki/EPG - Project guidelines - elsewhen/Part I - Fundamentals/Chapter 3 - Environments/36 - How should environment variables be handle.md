========== Question ==========  

### How should environment variables be handled in a project?  

========== Answer ==========  

Store environment variables in `.env` files and exclude them from version control using `.gitignore`. Commit a `.env.example` file as a guide for developers, and set environment variables through standard means for production.

**References**:

-   [Guide to managing environment variables in Node.js](https://medium.com/@rafaelvidaurre/managing-environment-variables-in-node-js-2cb45a55195f)

========== Id ==========  
36

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 3 - Environments

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-3-Environments::#36-How-should-environment-variables-be-handle

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
