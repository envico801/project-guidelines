========== Question ==========  

### Why do you need to use the -f flag when pushing after a rebase?  

========== Answer ==========  

When you do a rebase, you are changing the history on your feature branch. As a result, Git will reject normal `git push`. Instead, you'll need to use the -f or --force flag. The command to use is:

```sh
git push -f
```

[read more...](https://developer.atlassian.com/blog/2015/04/force-with-lease/)

========== Id ==========  
17

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 1 - Git

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-1-Git::#17-Why-do-you-need-to-use-the--f-flag-when-pu

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
