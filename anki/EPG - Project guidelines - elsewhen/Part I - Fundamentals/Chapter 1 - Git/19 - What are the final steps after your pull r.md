========== Question ==========  

### What are the final steps after your Pull Request has been accepted, merged, and closed?  

========== Answer ==========  

The final steps are:

1. Remove your local feature branch if you're done:

```sh
git branch -d <branchname>
```

2. To remove all branches which are no longer on remote:

```sh
git fetch -p && for branch in `git branch -vv --no-color | grep ': gone]' | awk '{print $1}'`; do git branch -D $branch; done
```

========== Id ==========  
19

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 1 - Git

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-1-Git::#19-What-are-the-final-steps-after-your-pull-r

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
