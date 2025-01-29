========== Question ==========  

### What is the purpose of interactive rebasing in Git?  

========== Answer ==========  

Interactive rebasing is a powerful feature in Git that allows you to edit, combine, or reorder commits in your branch history before applying them to another branch. It is commonly used to clean up commit history, fix mistakes, or squash multiple commits into a single one to make the history more concise and easier to understand.

Interactive rebasing is often used to update a feature branch with the latest changes from a target branch (e.g., `develop`). For example, you can use the following commands:

```
git checkout <branchname>
git rebase -i --autosquash develop
```

#### What does the `-i` flag do?

The `-i` flag stands for **interactive** mode. When used, it opens an editor where you can see a list of commits and choose actions to perform on each commit, such as:

-   **Reword**: Change the commit message.

-   **Pick**: Keep the commit as is.

-   **Squash**: Combine this commit with the previous one.

-   **Drop**: Remove the commit entirely.

-   **Edit**: Pause the rebase to make changes to the commit.

Without the `-i` flag, Git performs a **non-interactive rebase**, meaning it automatically replays all commits from your branch onto the target branch (`develop` in this case) without giving you the opportunity to modify, reorder, or squash commits. This can be faster if no changes to the commit history are needed, but it lacks the flexibility to clean up or reorganize commits.

#### What does the `--autosquash` option do?

The `--autosquash` option works in conjunction with interactive rebasing. It automatically groups and combines fixup commits (commits prefixed with `fixup!`) with their respective base commits during the rebase process. This ensures that the branch history is cleaner, with fewer intermediate commits, and helps maintain a more organized and professional commit log on the target branch.

#### Use Case:

By combining all related commits into a single, polished commit, interactive rebasing with `-i` and `--autosquash` keeps the `develop` branch cleaner and avoids clutter from multiple commits for a single feature.

**References:**

-   Interactive rebasing with `--autosquash`

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
