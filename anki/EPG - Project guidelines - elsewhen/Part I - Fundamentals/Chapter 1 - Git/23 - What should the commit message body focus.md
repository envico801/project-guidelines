========== Question ==========  

### What Should the Commit Message Body Focus on Explaining?  

========== Answer ==========  

The body of a commit message should explain **what** and **why** changes are made, rather than focusing on **how** they were implemented.

<hr>

Example of a poor commit message (focuses on how):

```
feat: Add user authentication

Created a new AuthService class
Added login() method with bcrypt
Modified UserController to use AuthService
Added password hashing function
```

<hr>

Example of a good commit message (focuses on what and why):

```
feat: Add user authentication

Implement secure user authentication to protect sensitive user data
and meet compliance requirements for our banking features.

This change:
- Prevents unauthorized access to user accounts
- Adds industry-standard password security
- Addresses security audit finding #45
- Sets foundation for upcoming 2FA feature
```

<hr>

Another good example:

```
fix: Update database connection timeout

Increase connection timeout from 5s to 30s to handle peak traffic
periods. Our monitoring shows connection failures during high load
times (>1000 concurrent users), causing customer complaints.

Related to incident #123
```

<hr>

The body should provide context that future maintainers would need to understand why this change was necessary, not just what files were modified or how the code works.

========== Id ==========  
23

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 1 - Git

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-1-Git::#23-What-should-the-commit-message-body-focus

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
