========== Cloze Question ==========

###  When validating the content-type in API requests, prioritize accepting {{c1::application/\*json}}. Allowing other MIME types like {{c2::application/x-www-form-urlencoded}} can enable attackers to {{c3::create a form and trigger a POST request}}.  

========== Answer ==========  

(Cloze) The server should **never assume the Content-Type**. If the Content-Type header is missing or incorrect, respond with a **4XX error** to reject unsupported content.

========== Id ==========  
124

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#124-Cloze-when-validating-the-content-type-i

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
