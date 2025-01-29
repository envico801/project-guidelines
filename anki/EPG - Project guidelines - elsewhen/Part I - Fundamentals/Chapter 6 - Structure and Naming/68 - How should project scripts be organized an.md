========== Question ==========  

### How Should Project Scripts Be Organized and Why?  

========== Answer ==========  

<hr>

Place all project scripts (bash, node, etc.) in a dedicated `./scripts` folder for better organization. This practice offers several benefits:

```
project/
├── scripts/
│   ├── build/
│   │   ├── production.js
│   │   └── development.js
│   ├── db/
│   │   ├── migrate.sh
│   │   ├── seed.js
│   │   └── sync.sh
│   ├── deploy/
│   │   ├── staging.sh
│   │   └── production.sh
│   └── tests/
│       ├── e2e.js
│       └── setup-test-db.sh
├── src/
└── package.json
```

<hr>

Common script categories include:

-   Build scripts (production, development, staging)

-   Database management (migrations, seeding, backups)

-   Deployment automation

-   Test setup and execution

-   Development environment setup

-   Code generation tools

-   CI/CD helpers

<hr>

This organization:

-   Makes scripts easily discoverable

-   Prevents cluttering the root directory

-   Allows for logical grouping of related scripts

-   Simplifies script management in `package.json`:

```json
{
    "scripts": {
        "build:prod": "node scripts/build/production.js",
        "build:dev": "node scripts/build/development.js",
        "db:migrate": "bash scripts/db/migrate.sh",
        "db:seed": "node scripts/db/seed.js",
        "deploy:staging": "bash scripts/deploy/staging.sh"
    }
}
```

========== Id ==========  
68

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen::Part I - Fundamentals::Chapter 6 - Structure and Naming

FILE TAGS: #Javascript::#Coding-best-practices::#EPG-Project-guidelines-elsewhen::#Part-I-Fundamentals::#Chapter-6-Structure-and-Naming::#68-How-should-project-scripts-be-organized-an

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
```

QUESTION STATUS: Safe to store
