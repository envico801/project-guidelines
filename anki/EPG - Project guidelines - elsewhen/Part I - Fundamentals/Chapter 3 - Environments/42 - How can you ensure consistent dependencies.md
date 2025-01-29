========== Question ==========  

### How can you ensure consistent dependencies when using older versions of npm?  

========== Answer ==========  

For older versions of npm, use `--save --save-exact` when installing a new dependency and create an `npm-shrinkwrap.json` file before publishing. This will lock dependencies to specific versions, similar to `package-lock.json` in newer npm versions.

**References**:

-   [npm documentation on package locks](https://docs.npmjs.com/files/package-locks)

========== Id ==========  
42

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 3 - Environments

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-3-Environments::#42-How-can-you-ensure-consistent-dependencies

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
