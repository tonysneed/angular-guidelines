# Angular Development Guidelines

*Suggested guidelines for developing Angular applications*

## A. General Guidelines

1. Study and apply the official [Angular Style Guide](https://angular.io/guide/styleguide).

2. Use the [Angular CLI](https://cli.angular.io/) to scaffold services, components, modules, etc.
    - See the [docs](https://cli.angular.io), as well as a third party [reference guide](https://www.sitepoint.com/ultimate-angular-cli-reference).
    -  Run `npm` sripts from package.json, rather than executing global `ng` commands.
        + `npm` scripts with `ng` commands use the _local_ stable version of @angular/cli
    - Pass parameters to `npm` by preceeding args with `--`.

    ```
    npm start
    npm start -- -o
    npm run lint
    npm run build
    npm run test
    ```

## B. Tooling

1. Use [TSLint](https://palantir.github.io/tslint) with the [VS Code extension](https://marketplace.visualstudio.com/items?itemName=eg2.tslint) or [SublimeText plugin](https://github.com/lavrton/SublimeLinter-contrib-tslint) to vet your TypeScript code in real-time.

2. Use the [Angular Language Service](https://github.com/angular/angular/tree/master/packages/language-service) with the [VS Code extension](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template) or [SublimeText plugin](http://brianflove.com/2017/04/11/angular-language-service/) to check for template errors in real time.

3. If using VS Code install helpful extensions, tasks and shortcuts.

    - **TS Hero** extendion for managing imports.
    - **Debugger for Chome** so you can debug the app and tests in the editor.
    - **Tasks, Launch Files, Shortcuts** for Angular Development from this [repo](https://github.com/tonysneed/vscode-ng).

## C. TypeScript

1. Avoid using `any` unless absolutely necessary, using [classes](https://www.typescriptlang.org/docs/handbook/classes.html) and [interfaces](https://www.typescriptlang.org/docs/handbook/interfaces.html) for greater compile-time type safety.

2. Remove commented code (`//deadFunction()`) and console log statements (`console.log('Debugging code')`) before pushing a commit.

## D. Patterns

1. Use the [object-oriented](http://rachelappel.com/write-object-oriented-javascript-with-typescript/) features of TypeScript / ES 2015+ in order to implement [design patterns](https://github.com/torokmark/design_patterns_in_typescript) in a type-safe manner.

2. Place business logic in [domain classes](https://www.amazon.com/exec/obidos/ASIN/0321125215/domainlanguag-20), rather than in components or services.

3. Inject [services](https://angular.io/guide/dependency-injection) into model classes and components.
11. Properly **scope** services to _components_, _feature modules_ (shared folder in feature), or _app-wide_ (core folder).

4. Avoid referencing components in services, using strategy pattern where user input is needed.

## E. Testing

1. Write [unit tests](https://angular.io/guide/testing) in [Jasmine](https://jasmine.github.io/) to validate _business logic_ in model classes, mocking services with [spies](https://jasmine.github.io/2.0/introduction.html#section-Spies) to stub dependencies.

2. Unit test *presentation logic* in components.

## F. Git

1. Run linting and test commands prior to pushing a final commit to a pull request.

    ```
    npm run lint
    npm run test
    npm run e2e
    ```

2. Create [temporary local git branches](http://jaimeiniesta.github.io/learn.github.com/p/branching.html) for feature sub-tasks, then [rebase](https://www.atlassian.com/git/tutorials/merging-vs-rebasing) them into your local feature branch and delete the temporary branch.

    ```
    git checkout feature/branch-name
    git rebase temporary-branch
    git branch -d temporary-branch
    ```

3. Before creating a final commit to a pull request, make sure to [pull and rebase](http://gitready.com/advanced/2009/02/11/pull-with-rebase.html) commits from the working branch of the upstream repository.

    ```
    git checkout feature/branch-name
    git pull --rebase origin develop
    ```
  
    - Resolve any conflicts that may occur.
        + If using VS Code, conflicts will have a purple C in the Git pane.
        + Click links to accept current, incoming or both sets of changes.
        + Stage files with resolved conflicts by clicking the plus sign.

    - Continue rebase process until all conflicts are resolved.

    ```
    git rebase --continue
    ```

4. Create a final commit by [squashing](http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html) previous commits in a pull request using interactive rebase.

    ```
    git rebase -i <commit_id>
    ```
  
    - Specify commit id BEFORE the oldest commit to include
    - In editor change all picks to s, except first one
    - Consoliate commit messages 

5. Force push feature branch to remote

    ```
    git push --force
    ```
  
6. After the PR is merged, **delete** local feature branch and **pull** latest from origin
