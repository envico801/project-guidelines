========== Question ==========  

### How should environment variables be managed in a project?  

========== Answer ==========  

Use `.env` files to store your variables and add them to `.gitignore` to be excluded. Instead, commit a `.env.example` which serves as a guide for developers. For production, you should still set your environment variables in the standard way. [read more](https://medium.com/@rafaelvidaurre/managing-environment-variables-in-node-js-2cb45a55195f)

========== Id ==========  
36

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 3 - Environments

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-3-Environments::#36-How-should-environment-variables-be-manage

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
