========== Question ==========  

### What is the recommended case for query string parameters and resource fields?  

========== Answer ==========  

Use **camelCase** for parameters in query strings or resource fields.

**Examples**:

-   Query string parameters:

    ```
    https://api.example.com/users?firstName=John&lastName=Doe&sortBy=createdDate
    ```

-   JSON resource fields:

    ```json
    {
        "firstName": "John",
        "lastName": "Doe",
        "createdDate": "2023-11-21",
        "contactInfo": {
            "phoneNumber": "123-456-7890",
            "emailAddress": "john.doe@example.com"
        }
    }
    ```

========== Id ==========  
98

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 9 - API

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-9-API::#98-What-is-the-recommended-case-for-query-str

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
