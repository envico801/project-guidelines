========== Question ==========  

### How should nested resources be represented in API URLs?  

========== Answer ==========  

For nested resources, use the relation between them in the URL. For example:

> `GET /schools/2/students ` , should get the list of all students from school 2. `GET /schools/2/students/31` , should get the details of student 31, which belongs to school 2. `DELETE /schools/2/students/31` , should delete student 31, which belongs to school 2. `PUT /schools/2/students/31` , should update info of student 31, Use PUT on resource-URL only, not collection. `POST /schools` , should create a new school and return the details of the new school created. Use POST on collection-URLs.

========== Id ==========  
110

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#110-How-should-nested-resources-be-represented

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
````
QUESTION STATUS: Safe to store
