========== Question ==========  

### How do you create and manage a new feature or bug-fix branch in Git?  

========== Answer ==========  

1. Create a new branch:

    ```sh
    git checkout -b <branch-name>
    ```

2. Branch Naming Conventions:

    - Features: `feature/add-login`

    - Bugs: `bugfix/auth-error`

3. Push to remote:

    ```sh
    git push -u origin <branch-name>
    ```

<hr>

Best Practices:

-   Create from updated `main`/`develop`

-   Keep branches focused

-   Use pull requests for review

-   Delete after merging

========== Id ==========  
11

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 1 - Git

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-1-Git::#11-How-do-you-create-and-manage-a-new-feature

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
