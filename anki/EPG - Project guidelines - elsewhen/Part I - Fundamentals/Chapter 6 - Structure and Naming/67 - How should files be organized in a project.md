========== Question ==========  

### How should files be organized in a project structure?  

========== Answer ==========  

Files should be organized around product features / pages / components, not roles. Test files should be placed next to their implementation.

**Bad**

```
.
├── controllers
|   ├── product.js
|   └── user.js
├── models
|   ├── product.js
|   └── user.js
```

**Good**

```
.
├── product

|   ├── index.js
|   ├── product.js
|   └── product.test.js
├── user

|   ├── index.js
|   ├── user.js
|   └── user.test.js
```

========== Id ==========  
67

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 6 - Structure and Naming

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-6-Structure-and-Naming::#67-How-should-files-be-organized-in-a-project

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
````
QUESTION STATUS: Safe to store
