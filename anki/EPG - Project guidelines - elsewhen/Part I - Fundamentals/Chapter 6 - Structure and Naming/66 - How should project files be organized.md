========== Question ==========  

### How should project files be organized?  

========== Answer ==========  

Organize files around product `features`, `pages`, or `components`, rather than by role. Place test files next to the code they test.

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
66

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 6 - Structure and Naming

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-6-Structure-and-Naming::#66-How-should-project-files-be-organized

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
