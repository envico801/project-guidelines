========== Cloze Question ==========

###  Deployment-specific configurations should be loaded from {{c1::environment variables}} and never added to the codebase as {{c2::constants}}.  

========== Answer ==========  

(Cloze) This is because you have tokens, passwords, and other valuable information in there. Your config should be correctly separated from the app internals as if the codebase could be made public at any moment.

========== Id ==========  
35

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 3 - Environments

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-3-Environments::#35-Cloze-deployment-specific-configurations

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
````
QUESTION STATUS: Safe to store
