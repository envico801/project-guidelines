========== Question ==========  

### What steps should you take after your Pull Request has been accepted and merged?  

========== Answer ==========  

Final steps include:

1. Deleting your local feature branch:

```sh
git branch -d <branchname>
```

2. Cleaning up branches no longer on the remote:

```sh
git fetch -p && for branch in `git branch -vv --no-color | grep ': gone]' | awk '{print $1}'`; do git branch -D $branch; done
```

========== Id ==========  
19

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 1 - Git

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-1-Git::#19-What-steps-should-you-take-after-your-pull

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
