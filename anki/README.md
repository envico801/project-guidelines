# EPG - Project guidelines - elsewhen

## Questions

### Part I - Fundamentals

#### Chapter 1 - Git

![Git](/images/branching.png)
<a name="some-git-rules"></a>

### 1.1 Some Git rules

Q:: What type of branch should you perform work in?
A:: You should perform work in a feature branch. This way all work is done in isolation on a dedicated branch rather than the main branch. It allows you to submit multiple pull requests without confusion. You can iterate without polluting the master branch with potentially unstable, unfinished code. [read more...](https://www.atlassian.com/git/tutorials/comparing-workflows#feature-branch-workflow)

Q:: Which branch should you branch out from when creating a feature branch?
A:: You should branch out from `develop`. This way, you can make sure that code in master will almost always build without problems, and can be mostly used directly for releases (this might be overkill for some projects).

Q:: (Cloze) When working with Git, you should never push into {{c1::develop}} or {{c2::master}} branch. Instead, you should make a {{c3::Pull Request}}.
A:: (Cloze) It notifies team members that they have completed a feature. It also enables easy peer-review of the code and dedicates forum for discussing the proposed feature.

Q:: What steps should you take before pushing your feature and making a Pull Request?
A:: You should update your local `develop` branch and do an interactive rebase. Rebasing will merge in the requested branch (`master` or `develop`) and apply the commits that you have made locally to the top of the history without creating a merge commit (assuming there were no conflicts). This results in a nice and clean history. [read more ...](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)

Q:: When should you resolve potential conflicts in your Git workflow?
A:: You should resolve potential conflicts while rebasing and before making a Pull Request.

Q:: What should you do with local and remote feature branches after merging?
A:: You should delete local and remote feature branches after merging. This will prevent cluttering up your list of branches with dead branches. It ensures you only ever merge the branch back into (`master` or `develop`) once. Feature branches should only exist while the work is still in progress.

Q:: (Cloze) Before making a Pull Request, ensure your feature branch {{c1::builds successfully}} and {{c2::passes all tests}}, including {{c3::code style checks}}.
A:: (Cloze) You are about to add your code to a stable branch. If your feature-branch tests fail, there is a high chance that your destination branch build will fail too. Additionally, you need to apply code style check before making a Pull Request. It aids readability and reduces the chance of formatting fixes being mingled in with actual changes.

Q:: Why should you use a specific `.gitignore` file?
A:: You should use [this](https://github.com/elsewhencode/project-guidelines/blob/master/.gitignore) `.gitignore` file because it already has a list of system files that should not be sent with your code into a remote repository. In addition, it excludes setting folders and files for most used editors, as well as most common dependency folders.

Q:: How can you protect your `develop` and `master` branches?
A:: You should enable branch protection for your `develop` and `master` branches. It protects your production-ready branches from receiving unexpected and irreversible changes. Read more about branch protection on [GitHub](https://help.github.com/articles/about-protected-branches/), [Bitbucket](https://confluence.atlassian.com/bitbucketserver/using-branch-permissions-776639807.html), and [GitLab](https://docs.gitlab.com/ee/user/project/protected_branches.html).

### 1.2 Git workflow

Q:: What is the first step in initializing a new project with Git?
A:: For a new project, initialize a git repository in the project directory using the commands:
```sh
cd <project directory>
git init
```
Note: This step should be ignored for subsequent features/changes.

Q:: How do you create a new feature or bug-fix branch in Git?
A:: You can create a new feature or bug-fix branch using the command:
```sh
git checkout -b <branchname>
```

Q:: (Cloze) When making changes in Git, you should use {{c1::git add <file1> <file2> ...}} to add files, followed by {{c2::git commit}} to commit the changes.
A:: (Cloze) `git add <file1> <file2> ... ` - you should add only files that make up a small and coherent change. `git commit` will start an editor which lets you separate the subject from the body. Read more about it in *section 1.3*.

Q:: What Git command can you use to review introduced changes one by one before committing?
A:: You can use `git add -p`, which will give you a chance to review all of the introduced changes one by one, and decide whether to include them in the commit or not.

Q:: How do you sync with the remote repository to get changes you've missed?
A:: You can sync with the remote repository using these commands:
```sh
git checkout develop
git pull
```
This will give you a chance to deal with conflicts on your machine while rebasing (later) rather than creating a Pull Request that contains conflicts.

Q:: What is the purpose of interactive rebasing in the Git workflow?
A:: Interactive rebasing is used to update your feature branch with the latest changes from develop. You can use the following commands:
```sh
git checkout <branchname>
git rebase -i --autosquash develop
```
You can use --autosquash to squash all your commits to a single commit. Nobody wants many commits for a single feature in develop branch. [read more...](https://robots.thoughtbot.com/autosquashing-git-commits)

Q:: (Cloze) If you have conflicts during rebasing, you should {{c1::resolve them}} and then continue the rebase using {{c2::git rebase --continue}}.
A:: (Cloze) To resolve conflicts, use:
```sh
git add <file1> <file2> ...
git rebase --continue
```

Q:: Why do you need to use the -f flag when pushing after a rebase?
A:: When you do a rebase, you are changing the history on your feature branch. As a result, Git will reject normal `git push`. Instead, you'll need to use the -f or --force flag. The command to use is:
```sh
git push -f
```
[read more...](https://developer.atlassian.com/blog/2015/04/force-with-lease/)

Q:: What is the less destructive alternative to `git push -f` if someone else is working on your branch?
A:: If someone else is working on your branch, you can use the less destructive `--force-with-lease` option instead of `-f`.

Q:: What are the final steps after your Pull Request has been accepted, merged, and closed?
A:: The final steps are:
1. Remove your local feature branch if you're done:
```sh
git branch -d <branchname>
```
2. To remove all branches which are no longer on remote:
```sh
git fetch -p && for branch in `git branch -vv --no-color | grep ': gone]' | awk '{print $1}'`; do git branch -D $branch; done
```

### 1.3 Writing good commit messages

Q:: How should you structure your commit message?
A:: You should separate the subject from the body with a newline between the two. Git is smart enough to distinguish the first line of your commit message as your summary. In fact, if you try git shortlog, instead of git log, you will see a long list of commit messages, consisting of the id of the commit, and the summary only.

Q:: (Cloze) When writing a commit message, limit the subject line to {{c1::50 characters}} and wrap the body at {{c2::72 characters}}.
A:: (Cloze) Commits should be as fine-grained and focused as possible, it is not the place to be verbose. [read more...](https://medium.com/@preslavrachev/what-s-with-the-50-72-rule-8a906f61f09c)

Q:: What are the rules for formatting the subject line of a commit message?
A:: The rules for formatting the subject line of a commit message are:
1. Capitalize the subject line.
2. Do not end the subject line with a period.
3. Use imperative mood in the subject line.

Q:: Why should you use imperative mood in the subject line of a commit message?
A:: Rather than writing messages that say what a committer has done, it's better to consider these messages as the instructions for what is going to be done after the commit is applied on the repository. [read more...](https://news.ycombinator.com/item?id=2079612)

Q:: What should be the focus of the body of a commit message?
A:: Use the body to explain **what** and **why** as opposed to **how**.

#### Chapter 2 - Documentation

![Documentation](/images/documentation.png)

Q:: What template should be used for creating a README.md file?
A:: Use this [template](./README.sample.md) for `README.md`. Feel free to add uncovered sections as needed.

Q:: How should documentation be handled for projects with multiple repositories?
A:: For projects with more than one repository, provide links to them in their respective `README.md` files.

Q:: (Cloze) The {{c1::README.md}} file should be {{c2::kept updated}} as the project {{c3::evolves}}.
A:: (Cloze) This ensures that the documentation remains relevant and useful throughout the project's lifecycle.

Q:: What is the primary purpose of commenting your code?
A:: Comment your code to make it as clear as possible what you are intending with each major section.

Q:: When should you include links to external discussions in your code comments?
A:: If there is an open discussion on GitHub or stackoverflow about the code or approach you're using, include the link in your comment.

Q:: (Cloze) Comments should not be used as an {{c1::excuse for bad code}}. Instead, you should {{c2::keep your code clean}}.
A:: (Cloze) This emphasizes the importance of writing clear, readable code rather than relying on comments to explain poorly written code.

Q:: What is the relationship between clean code and comments?
A:: Don't use clean code as an excuse to not comment at all. While code should be clean and readable, comments are still necessary to provide context and explain complex logic.

Q:: How should comments be maintained over time?
A:: Keep comments relevant as your code evolves. This means updating or removing comments that no longer accurately describe the code they're associated with.

#### Chapter 3 - Environments

![Environments](/images/laptop.png)

Q:: What are the three main environments typically defined in a project?
A:: The three main environments typically defined are `development`, `test`, and `production`.

Q:: Why is it important to define separate environments?
A:: Different environments may need different data, tokens, APIs, ports, etc. For example, you may want an isolated `development` mode that calls a fake API returning predictable data for easier testing, or enable Google Analytics only in `production`. [read more...](https://stackoverflow.com/questions/8332333/node-js-setting-up-environment-specific-configs-to-be-used-with-everyauth)

Q:: (Cloze) Deployment-specific configurations should be loaded from {{c1::environment variables}} and never added to the codebase as {{c2::constants}}.
A:: (Cloze) This is because you have tokens, passwords, and other valuable information in there. Your config should be correctly separated from the app internals as if the codebase could be made public at any moment.

Q:: How should environment variables be managed in a project?
A:: Use `.env` files to store your variables and add them to `.gitignore` to be excluded. Instead, commit a `.env.example` which serves as a guide for developers. For production, you should still set your environment variables in the standard way. [read more](https://medium.com/@rafaelvidaurre/managing-environment-variables-in-node-js-2cb45a55195f)

Q:: Why is it recommended to validate environment variables before the app starts?
A:: It may save others from hours of troubleshooting. You can use tools like `joi` to validate provided values. [Look at this sample](./configWithTest.sample.js)

Q:: (Cloze) To specify the node version for a project, set it in the {{c1::engines}} field of {{c2::package.json}}.
A:: (Cloze) This lets others know the version of node the project works on. [read more...](https://docs.npmjs.com/files/package.json#engines)

Q:: What is the purpose of using `nvm` and creating a `.nvmrc` file?
A:: Using `nvm` and creating a `.nvmrc` file allows anyone who uses `nvm` to simply use `nvm use` to switch to the suitable node version. [read more...](https://github.com/creationix/nvm)

Q:: Why might you set up a `preinstall` script in your project?
A:: It's a good idea to set up a `preinstall` script that checks node and npm versions because some dependencies may fail when installed by newer versions of npm.

Q:: What are the advantages of using Docker in a project?
A:: Using Docker can give you a consistent environment across the entire workflow, without much need to fiddle with dependencies or configs. [read more...](https://hackernoon.com/how-to-dockerize-a-node-js-application-4fbab45a0c19)

Q:: Why is it recommended to use local modules instead of globally installed modules?
A:: Using local modules lets you share your tooling with your colleagues instead of expecting them to have it globally on their systems.

Q:: (Cloze) To ensure consistent dependencies across a team, use {{c1::package-lock.json}} on {{c2::npm@5}} or higher, or alternatively use {{c3::Yarn}}.
A:: (Cloze) This ensures that team members get the exact same dependencies, making the code behave as expected and identical in any development machine. [read more...](https://kostasbariotis.com/consistent-dependencies-across-teams/)

Q:: For older versions of npm, how can you ensure consistent dependencies?
A:: For older versions of npm, use `—save --save-exact` when installing a new dependency and create `npm-shrinkwrap.json` before publishing. [read more...](https://docs.npmjs.com/files/package-locks)

#### Chapter 4 - Dependencies

![Github](/images/modules.png)

Q:: How can you keep track of your currently available packages in npm?
A:: You can use the command `npm ls --depth=0` to list your currently available packages. [read more...](https://docs.npmjs.com/cli/ls)

Q:: What tool can be used to check for unused or irrelevant packages in your project?
A:: You can use the `depcheck` tool to see if any of your packages have become unused or irrelevant. [read more...](https://www.npmjs.com/package/depcheck)

Q:: Why is it important to find and remove unused dependencies?
A:: You may include an unused library in your code and increase the production bundle size. Finding unused dependencies and getting rid of them helps optimize your project.

Q:: What should you check before using an npm dependency?  
A:: Before using a dependency, check its version release frequency, number of maintainers, and download statistics to see if it is heavily used by the community. You can use commands like `npm view async` or tools like `npm-stat` to get this information. More usage often means more contributors, better maintenance, and faster bug fixes. 

- [npm view async](https://docs.npmjs.com/cli/view) 
- [npm-stat](https://npm-stat.com/)

Q:: Why is it important to consider the maintainer activity of a dependency?
A:: Having loads of contributors won't be as effective if maintainers don't merge fixes and patches quickly enough.

Q:: What should you do if you need to use a less known dependency?
A:: If a less known dependency is needed, discuss it with the team before using it.

Q:: (Cloze) To ensure your app works with the latest version of its dependencies without breaking, use the command {{c1::npm outdated}}.
A:: (Cloze) This helps you stay up-to-date with dependency updates, which sometimes contain breaking changes. [read more...](https://docs.npmjs.com/cli/outdated)

Q:: Why should you update dependencies one by one?
A:: Updating dependencies one by one makes troubleshooting easier if anything goes wrong.

Q:: What tool can be used to facilitate updating npm packages?
A:: You can use a tool such as [npm-check-updates](https://github.com/tjunnone/npm-check-updates) to facilitate updating npm packages.

Q:: How can you check if a package has known security vulnerabilities?
A:: You can check for known security vulnerabilities in packages using tools like [Snyk](https://snyk.io/test?utm_source=risingstack_blog).

Q:: (Cloze) When updating dependencies, it's important to always check their {{c1::release notes}} when updates show up to be aware of potential {{c2::breaking changes}}.
A:: (Cloze) This practice helps you anticipate and address any issues that might arise from updating dependencies.

#### Chapter 5 - Testing

![Testing](/images/testing.png)

Q:: Why might you need a separate `test` mode environment?
A:: A separate `test` mode environment can be useful because:
1. You may not want to enable analytical information in 'production' mode and pollute someone's dashboard with test data.
2. Your API may have rate limits in `production` that could block your test calls after a certain amount of requests.

Q:: (Cloze) Test files should be placed {{c1::next to the tested modules}} using the naming convention {{c2::*.test.js}} or {{c3::*.spec.js}}.
A:: (Cloze) This placement ensures you don't have to dig through a folder structure to find a unit test. [read more...](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc)

Q:: Where should additional test files that don't relate to specific implementation files be placed?
A:: Additional test files that don't particularly relate to any specific implementation file should be put in a separate test folder, typically named `__test__`, to avoid confusion.

Q:: Why is the `__test__` folder name considered standard?
A:: The name `__test__` is considered standard and gets picked up by most JavaScript testing frameworks.

Q:: What are the characteristics of testable code?
A:: Testable code should:
1. Avoid side effects
2. Extract side effects
3. Use pure functions

Q:: (Cloze) A {{c1::pure function}} is a function that always returns the {{c2::same output}} for the {{c3::same input}}.
A:: (Cloze) Conversely, an impure function is one that may have side effects or depends on conditions from the outside to produce a value, making it less predictable. [read more...](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc)

Q:: Why is it important to write testable code with pure functions?
A:: Writing testable code with pure functions allows you to:
1. Test business logic as separate units
2. Minimize the impact of randomness and nondeterministic processes on the reliability of your code
[read more...](https://medium.com/javascript-scene/tdd-the-rite-way-53c9b46f45e3)

Q:: What is the benefit of using a static type checker?
A:: A static type checker brings a certain level of reliability to your code. [read more...](https://medium.freecodecamp.org/why-use-static-types-in-javascript-part-1-8382da1e0adb)

Q:: When should you run tests in relation to making pull requests?
A:: You should run tests locally before making any pull requests to `develop`.

Q:: Why is it important to run tests before pushing to a remote repository?
A:: Running tests after your `rebase` and before pushing your feature-branch to a remote repository ensures that you don't cause the production-ready branch build to fail.

Q:: Why is it important to document your tests?
A:: Documenting your tests provides valuable information for other developers, DevOps experts, QA, or anyone who may work on your code in the future, making it easier for them to understand and run the tests.

#### Chapter 6 - Structure and Naming

![Structure and Naming](/images/folder-tree.png)

Q:: How should files be organized in a project structure?
A:: Files should be organized around product features / pages / components, not roles. Test files should be placed next to their implementation.

**Bad**

```
.
├── controllers
|   ├── product.js
|   └── user.js
├── models
|   ├── product.js
|   └── user.js
```

**Good**

```
.
├── product
|   ├── index.js
|   ├── product.js
|   └── product.test.js
├── user
|   ├── index.js
|   ├── user.js
|   └── user.test.js
```

Q:: (Cloze) In a well-organized project structure, you should create {{c1::small modules}} that {{c2::encapsulate one responsibility}} including its {{c3::test}}.
A:: (Cloze) This organization makes it much easier to navigate through the project and find things at a glance, instead of dealing with a long list of files.

Q:: Where should additional test files be placed?
A:: Additional test files should be put in a separate test folder to avoid confusion.

Q:: Why is it beneficial to have a separate test folder for additional test files?
A:: It is a time saver for other developers or DevOps experts in your team.

Q:: (Cloze) Config files should be placed in a {{c1::./config}} folder, and you should {{c2::not make different config files}} for {{c3::different environments}}.
A:: (Cloze) This approach makes sense when breaking down config files for different purposes (database, API, etc.). It's important to remember that creating different config files for different environments doesn't scale cleanly as more deploys of the app are created.

Q:: How should values for config files be provided?
A:: Values to be used in config files should be provided by environment variables. [read more...](https://medium.com/@fedorHK/no-config-b3f1171eecd5)

Q:: Where should scripts be placed in the project structure?
A:: Scripts, including bash and node scripts, should be put in a `./scripts` folder.

Q:: Why is it recommended to have a separate folder for scripts?
A:: It's very likely you may end up with more than one script, such as production build, development build, database feeders, database synchronization, and so on.

Q:: (Cloze) Build output should be placed in a {{c1::./build}} folder, and {{c2::build/}} should be added to {{c3::.gitignore}}.
A:: (Cloze) The build folder (which can also be named 'dist') contains generated (bundled, compiled, transpiled) or moved files. These files don't need to be committed to the remote repository as they can be generated by team members.

Q:: Why shouldn't build output be committed to the remote repository?
A:: What you can generate, your teammates should be able to generate too, so there is no point committing them into your remote repository. Unless you specifically want to.

#### Chapter 7 - Code style

![Code style](/images/code-style.png)

### 7.1 Some code style guidelines

Q:: What JavaScript syntax is recommended for new projects?
A:: Use stage-2 and higher JavaScript (modern) syntax for new projects. For old projects, stay consistent with existing syntax unless you intend to modernize the project.

Q:: Why is it recommended to use stage-2 and higher JavaScript syntax?
A:: Stage-2 syntax is more likely to eventually become part of the spec with only minor revisions. Transpilers can be used to take advantage of new syntax features.

Q:: (Cloze) Code style checks should be included in your {{c1::build process}}.
A:: (Cloze) Breaking your build is one way of enforcing code style. It prevents you from taking it less seriously. Do it for both client and server-side code. [read more...](https://www.robinwieruch.de/react-eslint-webpack-babel/)

Q:: What tool is recommended to enforce code style in JavaScript?
A:: [ESLint - Pluggable JavaScript linter](http://eslint.org/) is recommended to enforce code style.

Q:: Why is ESLint preferred for enforcing code style?
A:: ESLint has more rules supported, the ability to configure the rules, and the ability to add custom rules.

Q:: Which JavaScript Style Guide is recommended?
A:: The [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript) is recommended.

Q:: (Cloze) For projects using {{c1::FlowType}}, it's recommended to use {{c2::Flow type style check rules}} for {{c3::ESLint}}.
A:: (Cloze) Flow introduces few syntaxes that also need to follow certain code style and be checked.

Q:: What is the purpose of using a `.eslintignore` file?
A:: The `.eslintignore` file is used to exclude files or folders from code style checks without polluting your code with `eslint-disable` comments.

Q:: What should be done with `eslint` disable comments before making a Pull Request?
A:: Remove any of your `eslint` disable comments before making a Pull Request.

Q:: How should small tasks be marked in the code?
A:: Use `//TODO:` comments for small tasks. For larger tasks, use `//TODO(#3456)` where the number is an open ticket.

Q:: (Cloze) Comments should be {{c1::kept relevant}} as code changes, and {{c2::commented blocks of code}} should be {{c3::removed}}.
A:: (Cloze) Your code should be as readable as possible, you should get rid of anything distracting. If you refactored a function, don't just comment out the old one, remove it.

Q:: Why should irrelevant or funny comments, logs, or naming be avoided?
A:: While your build process may (should) get rid of them, sometimes your source code may get handed over to another company/client and they may not share the same banter.

Q:: What guidelines are given for naming functions?
A:: For functions, use long, descriptive names. A function name should be a verb or a verb phrase, and it needs to communicate its intention.

Q:: How should functions be organized in a file?
A:: Organize your functions in a file according to the step-down rule. Higher level functions should be on top and lower levels below.

### 7.2 Enforcing code style standards

Q:: What is the purpose of using a .editorconfig file in a project?
A:: A .editorconfig file helps developers define and maintain consistent coding styles between different editors and IDEs on the project. The EditorConfig project consists of a file format for defining coding styles and a collection of text editor plugins that enable editors to read the file format and adhere to defined styles. EditorConfig files are easily readable and they work nicely with version control systems.

Q:: How can you make your editor notify you about code style errors?
A:: Use [eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier) and [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) with your existing ESLint configuration. [Read more...](https://github.com/prettier/eslint-config-prettier#installation)

Q:: Why should you consider using Git hooks?
A:: Git hooks greatly increase a developer's productivity. They allow you to make changes, commit and push to staging or production environments without the fear of breaking builds. [Read more...](http://githooks.com/)

Q:: What is the benefit of using Prettier with a precommit hook?
A:: While `prettier` itself can be very powerful, it's not very productive to run it simply as an npm task alone each time to format code. Using Prettier with a precommit hook, along with `lint-staged` and `husky`, can greatly enhance productivity. [Read more about configuring `lint-staged` here](https://github.com/okonet/lint-staged#configuration) and [configuring `husky` here](https://github.com/typicode/husky).

#### Chapter 8 - Logging

![Logging](/images/logging.png)

Q:: Why should you avoid client-side console logs in production?
A:: Even though your build process can (and should) get rid of them, it's important to ensure that your code style checker warns you about leftover console logs. This helps prevent unintended logging in production environments.

Q:: What is the recommended approach for production logging?
A:: It's recommended to use logging libraries for production mode, such as [winston](https://github.com/winstonjs/winston) or [node-bunyan](https://github.com/trentm/node-bunyan). These libraries help produce readable production logging.

Q:: What are the benefits of using logging libraries in production?
A:: Using logging libraries makes troubleshooting less unpleasant by providing features such as colorization, timestamps, logging to a file in addition to the console, or even logging to a file that rotates daily. [Read more...](https://blog.risingstack.com/node-js-logging-tutorial/)

#### Chapter 9 - API

<a name="api-design"></a>

![API](/images/api.png)

Q:: What are the three main factors in resource-oriented design for APIs?
A:: The three main factors in resource-oriented design are:
1. Resources (which have data, can be nested, and have methods that operate against them)
2. Collections (groups of resources)
3. URLs (which identify the online location of resources or collections)

Q:: Why is resource-oriented design beneficial for API development?
A:: Resource-oriented design is beneficial because:
1. It's well-known to developers (the main API consumers)
2. It offers readability and ease of use
3. It allows for writing generic libraries and connectors without knowing the specifics of the API

Q:: What case should be used for URLs and resource names in API design?
A:: Use kebab-case for URLs and plural kebab-case for resource names in URLs.

Q:: What case should be used for parameters in the query string or resource fields?
A:: Use camelCase for parameters in the query string or resource fields.

Q:: Why should plural nouns be used for naming URLs pointing to collections?
A:: Plural nouns should be used for naming URLs pointing to collections (e.g., `/users`) because it reads better and keeps URLs consistent. [Read more...](https://apigee.com/about/blog/technology/restful-api-design-plural-nouns-and-concrete-names)

Q:: How should plurals be handled in source code for variables and properties?
A:: In the source code, convert plurals to variables and properties with a List suffix. This is because plural is nice in the URL, but in the source code, it's too subtle and error-prone.

Q:: What is the recommended format for URLs pointing to a specific resource?
A:: Always use a singular concept that starts with a collection and ends with an identifier, for example:
```
/students/245743
/airports/kjfk
```

Avoid URLs like this:

```
GET /blogs/:blogId/posts/:postId/summary
```

_Why:_

> This is not pointing to a resource but to a property instead. You can pass the property as a parameter to trim your response.

Q:: (Cloze) In API design, it's recommended to keep {{c1::verbs}} out of your {{c2::resource URLs}} because using a verb for each resource operation can lead to {{c3::a huge list of URLs}} and {{c4::no consistent pattern}}.
A:: (Cloze) This makes it difficult for developers to learn the API. Verbs are used for something else in API design.

Q:: When is it appropriate to use verbs in API URLs?
A:: Use verbs for non-resources, when your API doesn't return any resources but instead executes an operation and returns the result. These are not CRUD operations. For example:
```
/translate?text=Hallo
```

_Why:_

> Because for CRUD we use HTTP methods on `resource` or `collection` URLs. The verbs we were talking about are actually `Controllers`. You usually don't develop many of these. [read more...](https://github.com/byrondover/api-guidelines/blob/master/Guidelines.md#controller)

Q:: What case should be used for JSON property names in request bodies or response types?
A:: Follow `camelCase` for `JSON` property names in request bodies or response types to maintain consistency. This is because these guidelines assume JavaScript is used for generating and parsing JSON.

Q:: Why should you avoid using table_name for a resource name and column_name for resource properties in API design?
A:: Because your intention is to expose Resources, not your database schema details. This abstraction helps maintain separation between your API design and database structure.

Q:: How should CRUD functionalities be explained using HTTP methods in API design?
A:: CRUD functionalities should be explained using HTTP methods as follows:
- GET: To retrieve a representation of a resource
- POST: To create new resources and sub-resources
- PUT: To update existing resources
- PATCH: To update existing resources, only updating the fields that were supplied
- DELETE: To delete existing resources

Q:: How should nested resources be represented in API URLs?
A:: For nested resources, use the relation between them in the URL. For example:

> `GET /schools/2/students ` , should get the list of all students from school 2.

> `GET /schools/2/students/31` , should get the details of student 31, which belongs to school 2.

> `DELETE /schools/2/students/31` , should delete student 31, which belongs to school 2.

> `PUT /schools/2/students/31` , should update info of student 31, Use PUT on resource-URL only, not collection.

> `POST /schools` , should create a new school and return the details of the new school created. Use POST on collection-URLs.

Q:: What is the recommended approach for versioning APIs in the URL?
A:: Use a simple ordinal number for a version with a `v` prefix (v1, v2). Move it all the way to the left in the URL so that it has the highest scope. For example:
```
http://api.domain.com/v1/schools/3/students
```
_Why:_

> When your APIs are public for other third parties, upgrading the APIs with some breaking change would also lead to breaking the existing products or services using your APIs. Using versions in your URL can prevent that from happening. [read more...](https://apigee.com/about/blog/technology/restful-api-design-tips-versioning)

Q:: (Cloze) A good error message response in an API should include a {{c1::code}}, a {{c2::message}}, and a {{c3::description}}. For validation errors, it should also include an {{c4::errors}} array with details for each error.
A:: (Cloze) This structure helps developers troubleshoot and resolve issues when using your APIs.

A good error message response might look something like this:

```json
{
  "code": 1234,
  "message": "Something bad happened",
  "description": "More details"
}
```

or for validation errors:

```json
{
  "code": 2314,
  "message": "Validation Failed",
  "errors": [
    {
      "code": 1233,
      "field": "email",
      "message": "Invalid email"
    },
    {
      "code": 1234,
      "field": "password",
      "message": "No password provided"
    }
  ]
}
```

Q:: What are some important HTTP status codes to use in API responses, and what do they indicate?
A:: Some important HTTP status codes include:
> `200 OK` response represents success for `GET`, `PUT` or `POST` requests.

> `201 Created` for when a new instance is created. Creating a new instance, using `POST` method returns `201` status code.

> `204 No Content` response represents success but there is no content to be sent in the response. Use it when `DELETE` operation succeeds.

> `304 Not Modified` response is to minimize information transfer when the recipient already has cached representations.

> `400 Bad Request` for when the request was not processed, as the server could not understand what the client is asking for.

> `401 Unauthorized` for when the request lacks valid credentials and it should re-request with the required credentials.

> `403 Forbidden` means the server understood the request but refuses to authorize it.

> `404 Not Found` indicates that the requested resource was not found.

> `500 Internal Server Error` indicates that the request is valid, but the server could not fulfill it due to some unexpected condition.

Q:: How can you limit the amount of data returned in an API response?
A:: Use a fields query parameter that takes a comma-separated list of fields to include. For example:
```
GET /students?fields=id,name,age,class
```

Q:: (Cloze) When designing APIs, it's recommended to provide {{c1::total numbers of resources}} in your response and accept {{c2::limit}} and {{c3::offset}} parameters for {{c4::pagination}}.
A:: (Cloze) Additionally, filtering and sorting don't need to be supported from the start for all resources, but should be documented for resources that offer these features.

Q:: Why is it important to use common HTTP status codes in API responses?
A:: Using common HTTP status codes is important because most developers don't have all 70+ HTTP status codes memorized. Using uncommon status codes might force developers to look up their meanings, disrupting their workflow. Most API providers use a small subset of HTTP status codes for clarity and ease of use. [read more...](https://apigee.com/about/blog/technology/restful-api-design-what-about-errors)

Q:: How should security exception messages be handled in API responses?
A:: Keep security exception messages as generic as possible. For instance, instead of saying 'incorrect password', reply with 'invalid username or password'. This prevents unknowingly informing the user that the username was correct and only the password was incorrect.

### 9.2 API security

Q:: Why should basic authentication not be used unless over a secure connection (HTTPS)?
A:: Basic authentication should not be used without HTTPS because the token, user ID, and password are transmitted over the network as clear text (base64 encoded, which is reversible). This makes the basic authentication scheme insecure. [Read more...](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication)

Q:: How should authentication tokens be transmitted in API requests?
A:: Authentication tokens must be transmitted using the Authorization header on every request. For example: `Authorization: Bearer xxxxxx, Extra yyyyy`. They should not be transmitted in the URL.

Q:: (Cloze) To enhance API security, {{c1::Authorization Code}} should be {{c2::short-lived}}, and any {{c3::non-TLS requests}} should be rejected by responding with {{c4::403 Forbidden}}.
A:: (Cloze) These measures help protect against unauthorized access and insecure data exchange.

Q:: Why is Rate Limiting important for API security?
A:: Rate Limiting is important to protect your APIs from bot threats that may call your API thousands of times per hour. It's recommended to implement rate limiting early on in your API development process.

Q:: What should an API do with received data to ensure security?
A:: An API should convert the received data to their canonical form or reject them. If there are any errors from bad or missing data, the API should return a 400 Bad Request status with details about the errors.

Q:: Why is it important to serialize JSON in API responses?
A:: Serializing JSON is crucial because a key concern with JSON encoders is preventing arbitrary JavaScript remote code execution within the browser or on the server (if using node.js). Using a proper JSON serializer to encode user-supplied data properly prevents the execution of user-supplied input on the browser.

Q:: (Cloze) When validating the content-type in API requests, it's recommended to mostly use {{c1::application/*json}}. Accepting other mime types like {{c2::application/x-www-form-urlencoded}} could allow attackers to {{c3::create a form and trigger a simple POST request}}.
A:: (Cloze) The server should never assume the Content-Type. A lack of Content-Type header or an unexpected Content-Type header should result in the server rejecting the content with a 4XX response.

Q:: What security measures can be implemented through HTTP headers?
A:: Setting HTTP headers appropriately can help to lock down and secure your web application. The Helmet project provides a set of security middleware for Express apps that can help set various HTTP headers. [Read more...](https://github.com/helmetjs/helmet)

Q:: How should an API handle data validation?
A:: All the data exchanged with the REST API must be validated by the API. This includes both incoming requests and outgoing responses to ensure data integrity and security.

Q:: What additional resource can be consulted for a comprehensive API security checklist?
A:: The API Security Checklist Project provides a comprehensive list of security best practices for API development. [Read more...](https://github.com/shieldfy/API-Security-Checklist)

### 9.3 API documentation

Q:: What should be included in the API Reference section of the README.md file?
A:: The API Reference section in the README.md file should include a comprehensive description of the API, including authentication methods, URL structure, request types, and details for each endpoint.

[README.md template](https://github.com/elsewhencode/project-guidelines/blob/master/README.sample.md)

Q:: How should API authentication methods be documented?
A:: API authentication methods should be described with a code sample to demonstrate their proper usage.

Q:: What information should be included when explaining the URL structure of an API?
A:: When explaining the URL structure of an API, include the path (without the root URL) and the request type (Method) for each endpoint.

Q:: How should URL parameters be documented in API documentation?
A:: URL parameters should be documented as follows:
- Specify if they are Required or Optional
- Provide the name and type of each parameter
For example:
```
Required: id=[integer]
Optional: photo_id=[alphanumeric]
```

Q:: (Cloze) For POST requests in API documentation, you should provide {{c1::working examples}} and separate the parameters into {{c2::Optional}} and {{c3::Required}} sections.
A:: (Cloze) This helps users understand how to properly structure their POST requests to the API.

Q:: What information should be included in the Success Response section of API documentation?
A:: The Success Response section should include:
- The expected status code
- Any return data
For example:
```
Code: 200
Content: { id : 12 }
```

Q:: How should Error Responses be documented in API documentation?
A:: Error Responses should be documented comprehensively, including:
- All possible ways an endpoint can fail (e.g., unauthorized access, wrong parameters)
- The error code, message, and description for each error case
For example:
```json
{
  "code": 401,
  "message": "Authentication failed",
  "description": "Invalid username or password"
}
```

Q:: Why is it important to document all possible error responses for an API endpoint?
A:: Documenting all possible error responses helps prevent assumptions from being made by API users. Even if it seems repetitive, it provides clear expectations for all potential failure scenarios.

Q:: (Cloze) Two popular open-source tools for API documentation are {{c1::API Blueprint}} and {{c2::Swagger}}.
A:: (Cloze) These tools can help create good, standardized documentation for your API.

- [API Blueprint](https://apiblueprint.org/)
- [Swagger](https://swagger.io/).

Q:: What are the key components that should be explained for each API endpoint in the documentation?
A:: For each API endpoint, the documentation should explain:
1. The URL structure (path only, no root URL)
2. The request type (Method)
3. URL parameters (if any), specifying if they are required or optional
4. Request body for POST requests, with examples
5. Success response (status code and return data)
6. Possible error responses (status codes, messages, and descriptions)

#### Chapter 10 - Accessibility ([a11y](https://www.a11yproject.com/))

![Accessibility](/images/accessibility.png)

### 10.1 Laying accessibility practices in place

Q:: Why is it important to consider accessibility at the start of a web project?
A:: Web content is accessible by default, but we often compromise this when building complex features. It's much easier to maintain accessibility by considering it from the start rather than re-implementing features later.

Q:: What tools are recommended for regular accessibility audits?
A:: Two recommended tools for regular accessibility audits are:
1. Lighthouse accessibility in Google Chrome DevTools
2. The axe DevTools extension

Q:: (Cloze) The scoring in accessibility audit tools like Lighthouse and axe is based on {{c1::axe user impact assessments}}.
A:: (Cloze) These assessments help determine the severity and impact of accessibility issues.

Q:: What important accessibility checks must be done manually?
A:: Some important accessibility checks that must be done manually include logical tab order. These are often listed as manual/guided tests alongside automated results in tools like Lighthouse and axe.

[Read more...](https://web.dev/lighthouse-accessibility/#additional-items-to-manually-check)

Q:: What are some recommended accessibility linters for different frameworks?
A:: Recommended accessibility linters for different frameworks include:
- React: [eslint-plugin-jsx-a11y](https://www.npmjs.com/package/eslint-plugin-jsx-a11y)
- Angular: [Angular Codelyzer](https://github.com/mgechev/codelyzer)
- Vue: [eslint-plugin-vuejs-accessibility](https://github.com/vue-a11y/eslint-plugin-vuejs-accessibility)

Q:: Why is it beneficial to use an accessibility linter in a project?
A:: An accessibility linter automatically checks that a basic level of accessibility is met by your project and is relatively easy to set up.

Q:: (Cloze) For accessibility testing, it's recommended to set up and use {{c1::[axe-core](https://www.youtube.com/watch?v=-n5Ul7WPc3Y&list=PLMlWGnpsViOMt24a-Y_dybv68H-kj6Un6&t=1649s)}} or similar tools. If using Storybook, you can implement {{c2::[accessibility testing with Storybook](https://storybook.js.org/blog/accessibility-testing-with-storybook/)}}.
A:: (Cloze) Including accessibility checks in your tests helps catch any changes that affect your project's accessibility and audit score.

Q:: What are some examples of accessible design systems?
A:: Two examples of accessible design systems are:
1. [React Spectrum](https://react-spectrum.adobe.com/react-spectrum/)
2. [Material Design](https://material.io/design)

Q:: Why is it beneficial to use an accessible design system?
A:: Accessible design systems provide components that are highly accessible out of the box, making it easier to maintain accessibility throughout your project.

Q:: What should be considered when agreeing on a minimum accessibility score for a project?
A:: When agreeing on a minimum accessibility score, consider your project's specific requirements. The score should be based on the results from tools like Lighthouse or axe, which use axe user impact assessments to determine the severity of accessibility issues.

### 10.2 Some basic accessibility rules to add to your project:

Q:: Why is it important to ensure link names are accessible?
A:: Inaccessible link elements pose barriers to accessibility. Using aria-label to describe links can help make them more accessible to users relying on assistive technologies.

Q:: How should lists be structured for accessibility?
A:: Lists must have both parent and child elements to be valid. This is important because screen readers inform users when they come to a list and how many items are in the list.

Q:: Why is the correct semantic structure of headings important for accessibility?
A:: Headers convey the structure of the page. When applied correctly, the page becomes easier to navigate, especially for users relying on screen readers or other assistive technologies.

Q:: (Cloze) Ensuring text elements have {{c1::sufficient contrast}} against the page background is important because some people with {{c2::low vision}} experience {{c3::low contrast}}, making it difficult to distinguish {{c4::outlines, borders, edges, and details}}.
A:: (Cloze) Text that is too close in luminance (brightness) to the background can be hard to read for these users.

Q:: Why is it necessary to provide alternative text for images?
A:: Screen readers have no way of translating an image into words that get read to the user, even if the image only consists of text. Therefore, it's necessary for images to have short, descriptive alt text so screen reader users can clearly understand the image's contents and purpose.

Q:: Where can more accessibility rules be found?
A:: More accessibility rules can be found at [Deque University's axe rules](https://dequeuniversity.com/rules/axe).

#### Chapter 11 - Licensing

![Licensing](/images/licensing.png)

Q:: (Cloze) When using resources in your project, it's important to ensure you have the {{c1::rights to use}} them. For libraries, look for licenses such as {{c2::MIT}}, {{c3::Apache}}, or {{c4::BSD}}.
A:: (Cloze) However, if you modify these libraries, you should review the license details carefully.

Q:: What potential legal issues should be considered when using images and videos in a project?
A:: Copyrighted images and videos may cause legal problems. It's important to ensure you have the right to use any visual content in your project.

---

DECK INFO

TARGET DECK: Javascript::Coding best practices::EPG - Project guidelines - elsewhen

FILE TAGS: #Javascript::#Coding-best-practices

Tags:

Reference:

Related:

```dataview
LIST
where file.name = this.file.name
````