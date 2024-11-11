========== Question ==========  

### What is the purpose of interactive rebasing in the Git workflow?  

========== Answer ==========  

Interactive rebasing is used to update your feature branch with the latest changes from develop. You can use the following commands:

```sh
git checkout <branchname>
git rebase -i --autosquash develop
```

You can use --autosquash to squash all your commits to a single commit. Nobody wants many commits for a single feature in develop branch. [read more...](https://robots.thoughtbot.com/autosquashing-git-commits)

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
