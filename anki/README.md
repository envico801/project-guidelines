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

- Have a `test` mode environment if needed.

  _Why:_

  > While sometimes end to end testing in `production` mode might seem enough, there are some exceptions: One example is you may not want to enable analytical information on a 'production' mode and pollute someone's dashboard with test data. The other example is that your API may have rate limits in `production` and blocks your test calls after a certain amount of requests.

- Place your test files next to the tested modules using `*.test.js` or `*.spec.js` naming convention, like `moduleName.spec.js`.

  _Why:_

  > You don't want to dig through a folder structure to find a unit test. [read more...](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc)

- Put your additional test files into a separate test folder to avoid confusion.

  _Why:_

  > Some test files don't particularly relate to any specific implementation file. You have to put it in a folder that is most likely to be found by other developers: `__test__` folder. This name: `__test__` is also standard now and gets picked up by most JavaScript testing frameworks.

- Write testable code, avoid side effects, extract side effects, write pure functions

  _Why:_

  > You want to test a business logic as separate units. You have to "minimize the impact of randomness and nondeterministic processes on the reliability of your code". [read more...](https://medium.com/javascript-scene/tdd-the-rite-way-53c9b46f45e3)

  > A pure function is a function that always returns the same output for the same input. Conversely, an impure function is one that may have side effects or depends on conditions from the outside to produce a value. That makes it less predictable. [read more...](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc)

- Use a static type checker

  _Why:_

  > Sometimes you may need a Static type checker. It brings a certain level of reliability to your code. [read more...](https://medium.freecodecamp.org/why-use-static-types-in-javascript-part-1-8382da1e0adb)

- Run tests locally before making any pull requests to `develop`.

  _Why:_

  > You don't want to be the one who caused production-ready branch build to fail. Run your tests after your `rebase` and before pushing your feature-branch to a remote repository.

- Document your tests including instructions in the relevant section of your `README.md` file.

  _Why:_

  > It's a handy note you leave behind for other developers or DevOps experts or QA or anyone who gets lucky enough to work on your code.

<a name="structure-and-naming"></a>

#### Chapter 6 - Structure and Naming

![Structure and Naming](/images/folder-tree.png)

- Organize your files around product features / pages / components, not roles. Also, place your test files next to their implementation.

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

  _Why:_

  > Instead of a long list of files, you will create small modules that encapsulate one responsibility including its test and so on. It gets much easier to navigate through and things can be found at a glance.

- Put your additional test files to a separate test folder to avoid confusion.

  _Why:_

  > It is a time saver for other developers or DevOps experts in your team.

- Use a `./config` folder and don't make different config files for different environments.

  _Why:_

  > When you break down a config file for different purposes (database, API and so on); putting them in a folder with a very recognizable name such as `config` makes sense. Just remember not to make different config files for different environments. It doesn't scale cleanly, as more deploys of the app are created, new environment names are necessary.
  > Values to be used in config files should be provided by environment variables. [read more...](https://medium.com/@fedorHK/no-config-b3f1171eecd5)

- Put your scripts in a `./scripts` folder. This includes `bash` and `node` scripts.

  _Why:_

  > It's very likely you may end up with more than one script, production build, development build, database feeders, database synchronization and so on.

- Place your build output in a `./build` folder. Add `build/` to `.gitignore`.

  _Why:_

  > Name it what you like, `dist` is also cool. But make sure that keep it consistent with your team. What gets in there is most likely generated (bundled, compiled, transpiled) or moved there. What you can generate, your teammates should be able to generate too, so there is no point committing them into your remote repository. Unless you specifically want to.

<a name="code-style"></a>

#### Chapter 7 - Code style

![Code style](/images/code-style.png)

<a name="code-style-check"></a>

### 7.1 Some code style guidelines

- Use stage-2 and higher JavaScript (modern) syntax for new projects. For old project stay consistent with existing syntax unless you intend to modernise the project.

  _Why:_

  > This is all up to you. We use transpilers to use advantages of new syntax. stage-2 is more likely to eventually become part of the spec with only minor revisions.

- Include code style check in your build process.

  _Why:_

  > Breaking your build is one way of enforcing code style to your code. It prevents you from taking it less seriously. Do it for both client and server-side code. [read more...](https://www.robinwieruch.de/react-eslint-webpack-babel/)

- Use [ESLint - Pluggable JavaScript linter](http://eslint.org/) to enforce code style.

  _Why:_

  > We simply prefer `eslint`, you don't have to. It has more rules supported, the ability to configure the rules, and ability to add custom rules.

- We use [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript) for JavaScript, [Read more](https://www.gitbook.com/book/duk/airbnb-javascript-guidelines/details). Use the javascript style guide required by the project or your team.

- We use [Flow type style check rules for ESLint](https://github.com/gajus/eslint-plugin-flowtype) when using [FlowType](https://flow.org/).

  _Why:_

  > Flow introduces few syntaxes that also need to follow certain code style and be checked.

- Use `.eslintignore` to exclude files or folders from code style checks.

  _Why:_

  > You don't have to pollute your code with `eslint-disable` comments whenever you need to exclude a couple of files from style checking.

- Remove any of your `eslint` disable comments before making a Pull Request.

  _Why:_

  > It's normal to disable style check while working on a code block to focus more on the logic. Just remember to remove those `eslint-disable` comments and follow the rules.

- Depending on the size of the task use `//TODO:` comments or open a ticket.

  _Why:_

  > So then you can remind yourself and others about a small task (like refactoring a function or updating a comment). For larger tasks use `//TODO(#3456)` which is enforced by a lint rule and the number is an open ticket.

- Always comment and keep them relevant as code changes. Remove commented blocks of code.

  _Why:_

  > Your code should be as readable as possible, you should get rid of anything distracting. If you refactored a function, don't just comment out the old one, remove it.

- Avoid irrelevant or funny comments, logs or naming.

  _Why:_

  > While your build process may(should) get rid of them, sometimes your source code may get handed over to another company/client and they may not share the same banter.

- Make your names search-able with meaningful distinctions avoid shortened names. For functions use long, descriptive names. A function name should be a verb or a verb phrase, and it needs to communicate its intention.

  _Why:_

  > It makes it more natural to read the source code.

- Organize your functions in a file according to the step-down rule. Higher level functions should be on top and lower levels below.

  _Why:_

  > It makes it more natural to read the source code.

<a name="enforcing-code-style-standards"></a>

### 7.2 Enforcing code style standards

- Use a [.editorconfig](http://editorconfig.org/) file which helps developers define and maintain consistent coding styles between different editors and IDEs on the project.

  _Why:_

  > The EditorConfig project consists of a file format for defining coding styles and a collection of text editor plugins that enable editors to read the file format and adhere to defined styles. EditorConfig files are easily readable and they work nicely with version control systems.

- Have your editor notify you about code style errors. Use [eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier) and [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) with your existing ESLint configuration. [read more...](https://github.com/prettier/eslint-config-prettier#installation)

- Consider using Git hooks.

  _Why:_

  > Git hooks greatly increase a developer's productivity. Make changes, commit and push to staging or production environments without the fear of breaking builds. [read more...](http://githooks.com/)

- Use Prettier with a precommit hook.

  _Why:_

  > While `prettier` itself can be very powerful, it's not very productive to run it simply as an npm task alone each time to format code. This is where `lint-staged` (and `husky`) come into play. Read more on configuring `lint-staged` [here](https://github.com/okonet/lint-staged#configuration) and on configuring `husky` [here](https://github.com/typicode/husky).

<a name="logging"></a>

#### Chapter 8 - Logging

![Logging](/images/logging.png)

- Avoid client-side console logs in production

  _Why:_

  > Even though your build process can (should) get rid of them, make sure that your code style checker warns you about leftover console logs.

- Produce readable production logging. Ideally use logging libraries to be used in production mode (such as [winston](https://github.com/winstonjs/winston) or
  [node-bunyan](https://github.com/trentm/node-bunyan)).

      _Why:_
      > It makes your troubleshooting less unpleasant with colorization, timestamps, log to a file in addition to the console or even logging to a file that rotates daily. [read more...](https://blog.risingstack.com/node-js-logging-tutorial/)

<a name="api"></a>

#### Chapter 9 - API

<a name="api-design"></a>

![API](/images/api.png)

### 9.1 API design

_Why:_

> Because we try to enforce development of sanely constructed RESTful interfaces, which team members and clients can consume simply and consistently.

_Why:_

> Lack of consistency and simplicity can massively increase integration and maintenance costs. Which is why `API design` is included in this document.

- We mostly follow resource-oriented design. It has three main factors: resources, collection, and URLs.

  - A resource has data, gets nested, and there are methods that operate against it.
  - A group of resources is called a collection.
  - URL identifies the online location of resource or collection.

  _Why:_

  > This is a very well-known design to developers (your main API consumers). Apart from readability and ease of use, it allows us to write generic libraries and connectors without even knowing what the API is about.

- use kebab-case for URLs.
- use camelCase for parameters in the query string or resource fields.
- use plural kebab-case for resource names in URLs.

- Always use a plural nouns for naming a url pointing to a collection: `/users`.

  _Why:_

  > Basically, it reads better and keeps URLs consistent. [read more...](https://apigee.com/about/blog/technology/restful-api-design-plural-nouns-and-concrete-names)

- In the source code convert plurals to variables and properties with a List suffix.

  _Why_:

  > Plural is nice in the URL but in the source code, it’s just too subtle and error-prone.

- Always use a singular concept that starts with a collection and ends to an identifier:

  ```
  /students/245743
  /airports/kjfk
  ```

- Avoid URLs like this:

  ```
  GET /blogs/:blogId/posts/:postId/summary
  ```

  _Why:_

  > This is not pointing to a resource but to a property instead. You can pass the property as a parameter to trim your response.

- Keep verbs out of your resource URLs.

  _Why:_

  > Because if you use a verb for each resource operation you soon will have a huge list of URLs and no consistent pattern which makes it difficult for developers to learn. Plus we use verbs for something else.

- Use verbs for non-resources. In this case, your API doesn't return any resources. Instead, you execute an operation and return the result. These **are not** CRUD (create, retrieve, update, and delete) operations:

  ```
  /translate?text=Hallo
  ```

  _Why:_

  > Because for CRUD we use HTTP methods on `resource` or `collection` URLs. The verbs we were talking about are actually `Controllers`. You usually don't develop many of these. [read more...](https://github.com/byrondover/api-guidelines/blob/master/Guidelines.md#controller)

- The request body or response type is JSON then please follow `camelCase` for `JSON` property names to maintain the consistency.

  _Why:_

  > This is a JavaScript project guideline, where the programming language for generating and parsing JSON is assumed to be JavaScript.

- Even though a resource is a singular concept that is similar to an object instance or database record, you should not use your `table_name` for a resource name and `column_name` resource property.

  _Why:_

  > Because your intention is to expose Resources, not your database schema details.

- Again, only use nouns in your URL when naming your resources and don’t try to explain their functionality.

  _Why:_

  > Only use nouns in your resource URLs, avoid endpoints like `/addNewUser` or `/updateUser` . Also avoid sending resource operations as a parameter.

- Explain the CRUD functionalities using HTTP methods:

  _How:_

  > `GET`: To retrieve a representation of a resource.

  > `POST`: To create new resources and sub-resources.

  > `PUT`: To update existing resources.

  > `PATCH`: To update existing resources. It only updates the fields that were supplied, leaving the others alone.

  > `DELETE`: To delete existing resources.

- For nested resources, use the relation between them in the URL. For instance, using `id` to relate an employee to a company.

  _Why:_

  > This is a natural way to make resources explorable.

  _How:_

  > `GET /schools/2/students ` , should get the list of all students from school 2.

  > `GET /schools/2/students/31` , should get the details of student 31, which belongs to school 2.

  > `DELETE /schools/2/students/31` , should delete student 31, which belongs to school 2.

  > `PUT /schools/2/students/31` , should update info of student 31, Use PUT on resource-URL only, not collection.

  > `POST /schools` , should create a new school and return the details of the new school created. Use POST on collection-URLs.

- Use a simple ordinal number for a version with a `v` prefix (v1, v2). Move it all the way to the left in the URL so that it has the highest scope:

  ```
  http://api.domain.com/v1/schools/3/students
  ```

  _Why:_

  > When your APIs are public for other third parties, upgrading the APIs with some breaking change would also lead to breaking the existing products or services using your APIs. Using versions in your URL can prevent that from happening. [read more...](https://apigee.com/about/blog/technology/restful-api-design-tips-versioning)

- Response messages must be self-descriptive. A good error message response might look something like this:

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

  _Why:_

  > developers depend on well-designed errors at the critical times when they are troubleshooting and resolving issues after the applications they've built using your APIs are in the hands of their users.

  _Note: Keep security exception messages as generic as possible. For instance, Instead of saying ‘incorrect password’, you can reply back saying ‘invalid username or password’ so that we don’t unknowingly inform user that username was indeed correct and only the password was incorrect._

- Use these status codes to send with your response to describe whether **everything worked**,
  The **client app did something wrong** or The **API did something wrong**.

      _Which ones:_
      > `200 OK` response represents success for `GET`, `PUT` or `POST` requests.

      > `201 Created` for when a new instance is created. Creating a new instance, using `POST` method returns `201` status code.

      > `204 No Content` response represents success but there is no content to be sent in the response. Use it when `DELETE` operation succeeds.

      > `304 Not Modified` response is to minimize information transfer when the recipient already has cached representations.

      > `400 Bad Request` for when the request was not processed, as the server could not understand what the client is asking for.

      > `401 Unauthorized` for when the request lacks valid credentials and it should re-request with the required credentials.

      > `403 Forbidden` means the server understood the request but refuses to authorize it.

      > `404 Not Found` indicates that the requested resource was not found.

      > `500 Internal Server Error` indicates that the request is valid, but the server could not fulfill it due to some unexpected condition.

      _Why:_
      > Most API providers use a small subset HTTP status codes. For example, the Google GData API uses only 10 status codes, Netflix uses 9, and Digg, only 8. Of course, these responses contain a body with additional information. There are over 70 HTTP status codes. However, most developers don't have all 70 memorized. So if you choose status codes that are not very common you will force application developers away from building their apps and over to wikipedia to figure out what you're trying to tell them. [read more...](https://apigee.com/about/blog/technology/restful-api-design-what-about-errors)

- Provide total numbers of resources in your response.
- Accept `limit` and `offset` parameters.

- The amount of data the resource exposes should also be taken into account. The API consumer doesn't always need the full representation of a resource. Use a fields query parameter that takes a comma separated list of fields to include:
  ```
  GET /students?fields=id,name,age,class
  ```
- Pagination, filtering, and sorting don’t need to be supported from start for all resources. Document those resources that offer filtering and sorting.

<a name="api-security"></a>

### 9.2 API security

These are some basic security best practices:

- Don't use basic authentication unless over a secure connection (HTTPS). Authentication tokens must not be transmitted in the URL: `GET /users/123?token=asdf....`

  _Why:_

  > Because Token, or user ID and password are passed over the network as clear text (it is base64 encoded, but base64 is a reversible encoding), the basic authentication scheme is not secure. [read more...](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication)

- Tokens must be transmitted using the Authorization header on every request: `Authorization: Bearer xxxxxx, Extra yyyyy`.

- Authorization Code should be short-lived.

- Reject any non-TLS requests by not responding to any HTTP request to avoid any insecure data exchange. Respond to HTTP requests by `403 Forbidden`.

- Consider using Rate Limiting.

  _Why:_

  > To protect your APIs from bot threats that call your API thousands of times per hour. You should consider implementing rate limit early on.

- Setting HTTP headers appropriately can help to lock down and secure your web application. [read more...](https://github.com/helmetjs/helmet)

- Your API should convert the received data to their canonical form or reject them. Return 400 Bad Request with details about any errors from bad or missing data.

- All the data exchanged with the REST API must be validated by the API.

- Serialize your JSON.

  _Why:_

  > A key concern with JSON encoders is preventing arbitrary JavaScript remote code execution within the browser... or, if you're using node.js, on the server. It's vital that you use a proper JSON serializer to encode user-supplied data properly to prevent the execution of user-supplied input on the browser.

- Validate the content-type and mostly use `application/*json` (Content-Type header).

  _Why:_

  > For instance, accepting the `application/x-www-form-urlencoded` mime type allows the attacker to create a form and trigger a simple POST request. The server should never assume the Content-Type. A lack of Content-Type header or an unexpected Content-Type header should result in the server rejecting the content with a `4XX` response.

- Check the API Security Checklist Project. [read more...](https://github.com/shieldfy/API-Security-Checklist)

<a name="api-documentation"></a>

### 9.3 API documentation

- Fill the `API Reference` section in [README.md template](./README.sample.md) for API.
- Describe API authentication methods with a code sample.
- Explaining The URL Structure (path only, no root URL) including The request type (Method).

For each endpoint explain:

- URL Params If URL Params exist, specify them in accordance with name mentioned in URL section:

  ```
  Required: id=[integer]
  Optional: photo_id=[alphanumeric]
  ```

- If the request type is POST, provide working examples. URL Params rules apply here too. Separate the section into Optional and Required.

- Success Response, What should be the status code and is there any return data? This is useful when people need to know what their callbacks should expect:

  ```
  Code: 200
  Content: { id : 12 }
  ```

- Error Response, Most endpoints have many ways to fail. From unauthorized access to wrongful parameters etc. All of those should be listed here. It might seem repetitive, but it helps prevent assumptions from being made. For example

  ```json
  {
    "code": 401,
    "message": "Authentication failed",
    "description": "Invalid username or password"
  }
  ```

- Use API design tools, There are lots of open source tools for good documentation such as [API Blueprint](https://apiblueprint.org/) and [Swagger](https://swagger.io/).

<a name="a11y"></a>

#### Chapter 10 - Accessibility ([a11y](https://www.a11yproject.com/))

![Accessibility](/images/accessibility.png)

### 10.1 Laying accessibility practices in place

Take the following steps **at the start of your project** to ensure an intentional level of accessibility is sustained:

_Why:_

> Web content is [accessible by default](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/HTML). We compromise this when we build complex features. It's much easier to reduce this impact by considering accessibility from the start rather than re-implement these features later.

- Arrange to do regular audits using [lighthouse](https://developers.google.com/web/tools/lighthouse#devtools) [accessibility](https://web.dev/lighthouse-accessibility/) or the [axe DevTools extension](https://chrome.google.com/webstore/detail/axe-devtools-web-accessib/lhdoppojpmngadmnindnejefpokejbdd?hl=en-US). Agree on a minimum score based on your projects requirements. The scoring in both tools is based on [axe user impact assessments](https://github.com/dequelabs/axe-core/blob/develop/doc/rule-descriptions.md#wcag-21-level-a--aa-rules).

  > **Note:** [some important checks](https://web.dev/lighthouse-accessibility/#additional-items-to-manually-check) must be done manually, e.g. logical tab order. The above tools list these as manual/guided tests alongside the automated results. With axe you have to save your automated results to view these.

- Install an a11y linter:

  - React: [eslint-plugin-jsx-a11y](https://www.npmjs.com/package/eslint-plugin-jsx-a11y)
  - Angular: [Angular Codelyzer](https://github.com/mgechev/codelyzer)
  - Vue: [eslint-plugin-vuejs-accessibility](https://github.com/vue-a11y/eslint-plugin-vuejs-accessibility)

  _Why:_

  > A linter will automatically check that a basic level of accessibility is met by your project and is relatively easy to set up.

- Set up and use a11y testing using [axe-core](https://www.youtube.com/watch?v=-n5Ul7WPc3Y&list=PLMlWGnpsViOMt24a-Y_dybv68H-kj6Un6&t=1649s) or similar.

- If you're using storybook, do [this](https://storybook.js.org/blog/accessibility-testing-with-storybook/).

  _Why:_

  > Including a11y checks in your tests will help you to catch any changes that affect your projects accessibility and your audit score.

- Consider using an accessible design system such as [React Spectrum](https://react-spectrum.adobe.com/react-spectrum/) or [Material Design](https://material.io/design).

  _Why:_

  > These components are highly accessible out of the box.

### 10.2 Some basic accessibility rules to add to your project:

- Ensure link names are accessible. Use aria-label to describe links

  _Why:_

  > Inaccessible link elements pose barriers to accessibility.

- Ensure lists are structured correctly and list elements are used semantically.

  _Why:_

  > Lists must have both parent and child elements for it to be valid. Screen readers inform users when they come to a list and how many items are in a list.

- Ensure the heading order is semantically correct.

  _Why:_

  > Headers convey the structure of the page. When applied correctly the page becomes easier to navigate.

- Ensure text elements have sufficient contrast against page background.

  _Why:_

  > Some people with low vision experience low contrast, meaning that there aren't very many bright or dark areas. Everything tends to appear about the same brightness, which makes it hard to distinguish outlines, borders, edges, and details. Text that is too close in luminance (brightness) to the background can be hard to read.

- Provide alternative text for images.

  _Why:_

  > Screen readers have no way of translating an image into words that gets read to the user, even if the image only consists of text. As a result, it's necessary for images to have short, descriptive alt text so screen reader users clearly understand the image's contents and purpose.

More accessibility rules can be found [here](https://dequeuniversity.com/rules/axe).

<a name="licensing"></a>

#### Chapter 11 - Licensing

![Licensing](/images/licensing.png)

Make sure you use resources that you have the rights to use. If you use libraries, remember to look for MIT, Apache or BSD but if you modify them, then take a look at the license details. Copyrighted images and videos may cause legal problems.

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