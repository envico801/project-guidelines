========== Cloze Question ==========

###  When validating the content-type in API requests, it's recommended to mostly use {{c1::application/*json}}. Accepting other mime types like {{c2::application/x-www-form-urlencoded}} could allow attackers to {{c3::create a form and trigger a simple POST request}}.  

========== Answer ==========  

(Cloze) The server should never assume the Content-Type. A lack of Content-Type header or an unexpected Content-Type header should result in the server rejecting the content with a 4XX response.

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
````
QUESTION STATUS: Safe to store
