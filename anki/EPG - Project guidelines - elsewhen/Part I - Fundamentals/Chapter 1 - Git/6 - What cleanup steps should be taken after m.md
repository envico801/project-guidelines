========== Question ==========  

### What Cleanup Steps Should Be Taken After Merging Feature Branches?  

========== Answer ==========  

After your feature branch has been merged (either through a Pull Request or direct merge), you should perform these cleanup steps:

1. Delete your local feature branch:

    ```sh
    git branch -d <branchname>
    ```

2. Delete the remote feature branch to avoid repository clutter:

    ```sh
    git push origin --delete <branchname>
    ```

3. Clean up any local branches that are no longer on the remote:

    ```sh
    git fetch -p && for branch in `git branch -vv --no-color | grep ': gone]' | awk '{print $1}'`; do git branch -D $branch; done
    ```

These steps ensure that:

-   Your repository stays clean and organized

-   You avoid accidentally reusing old feature branches

-   Each feature branch is only merged once

-   Your local repository accurately reflects the remote state

========== Id ==========  
6

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 1 - Git

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-1-Git::#6-What-cleanup-steps-should-be-taken-after-m

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
