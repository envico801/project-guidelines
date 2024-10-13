========== Question ==========  

### Why might you need a separate `test` mode environment?  

========== Answer ==========  

A separate `test` mode environment can be useful because:

1. You may not want to enable analytical information in 'production' mode and pollute someone's dashboard with test data.

2. Your API may have rate limits in `production` that could block your test calls after a certain amount of requests.

========== Id ==========  
56

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 5 - Testing

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-5-Testing::#56-Why-might-you-need-a-separate-test-mode

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
````
QUESTION STATUS: Safe to store
