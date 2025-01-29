========== Question ==========  

### How should functions be organized within a file?  

========== Answer ==========  

Organize functions in a file according to the **step-down rule**, **placing higher-level functions at the top and lower-level functions below** for readability and logical flow.

```javascript
// Higher-level function at the top
function processUserData(userData) {
    const validatedData = validateUserInput(userData);
    const normalizedData = normalizeUserData(validatedData);
    return saveToDatabase(normalizedData);
}

// Mid-level supporting functions
function validateUserInput(userData) {
    validateEmail(userData.email);
    validateAge(userData.age);
    return userData;
}

function normalizeUserData(userData) {
    return {
        email: userData.email.toLowerCase(),
        age: Number(userData.age),
        lastUpdated: new Date(),
    };
}

// Lower-level utility functions at the bottom
function validateEmail(email) {
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(email)) {
        throw new Error('Invalid email format');
    }
}

function validateAge(age) {
    if (age < 0 || age > 120) {
        throw new Error('Invalid age');
    }
}

function saveToDatabase(data) {
    // Database saving logic here
    return data;
}
```

<hr>

This example shows how to organize functions with:

1. The main high-level function `processUserData` at the top, which describes the overall business logic

2. Supporting functions `validateUserInput` and `normalizeUserData` in the middle

3. Utility functions like `validateEmail`, `validateAge`, and `saveToDatabase` at the bottom

========== Id ==========  
82

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 7 - Code Style

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-7-Code-Style::#82-How-should-functions-be-organized-within-a

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
