========== Question ==========  

### What is the purpose of interactive rebasing in Git?  

========== Answer ==========  

Interactive rebasing updates your feature branch with the latest changes from `develop`. Use:

```sh
git checkout <branchname>
git rebase -i --autosquash develop
```

The `--autosquash` option combines all commits into a single one. This keeps the `develop` branch cleaner and avoids multiple commits for one feature.

**References**:

-   [Interactive rebasing with autosquash](https://robots.thoughtbot.com/autosquashing-git-commits)

========== Id ==========  
15

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 1 - Git

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-1-Git::#15-What-is-the-purpose-of-interactive-rebasin

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
