========== Question ==========  

### What is a safer alternative to `git push -f` if others are working on the branch?  

========== Answer ==========  

Use `--force-with-lease` instead of `-f` when others may also be working on the branch. It prevents overwriting changes someone else may have pushed.

**References**:

-   [Explanation of `--force-with-lease`](https://developer.atlassian.com/blog/2015/04/force-with-lease/)

========== Id ==========  
18

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 1 - Git

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-1-Git::#18-What-is-a-safer-alternative-to-git-push--

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
