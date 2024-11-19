========== Question ==========  

### Why is the `-f` flag needed when pushing after a rebase?  

========== Answer ==========  

After a rebase, Git rejects a normal `git push` due to changed history. Use the `-f` or `--force` flag to push:

```sh
git push -f
```

========== Id ==========  
17

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 1 - Git

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-1-Git::#17-Why-is-the--f-flag-needed-when-pushing-a

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
