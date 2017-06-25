# Angular Development Guidelines

*Proposed guidelines for developing Angular applications*

1. Study and apply the official [Angular Style Guide](https://angular.io/guide/styleguide).
2. Use the [Angular CLI](https://cli.angular.io/) to scaffold services, components, modules, etc.
    - See the [docs](https://cli.angular.io), as well as a third party [reference guide](https://www.sitepoint.com/ultimate-angular-cli-reference)
3. Use [TSLint](https://palantir.github.io/tslint) with the [VS Code extension](https://marketplace.visualstudio.com/items?itemName=eg2.tslint) or [SublimeText plugin](https://github.com/lavrton/SublimeLinter-contrib-tslint) to vet your TypeScript code in real-time
4. Use the [Angular Language Service](https://github.com/angular/angular/tree/master/packages/language-service) with the [VS Code extension](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template) or [SublimeText plugin](http://brianflove.com/2017/04/11/angular-language-service/) to check for template errors in real time
5. Avoid using `any` unless absolutely necessary, using [classes](https://www.typescriptlang.org/docs/handbook/classes.html) and [interfaces](https://www.typescriptlang.org/docs/handbook/interfaces.html) for greater compile-time type safety
6. Use the [object-oriented](http://rachelappel.com/write-object-oriented-javascript-with-typescript/) features of TypeScript / ES 2015+ in order to implement [design patterns](https://github.com/torokmark/design_patterns_in_typescript) in a type-safe manner
7. Place business logic in [domain classes](https://www.amazon.com/exec/obidos/ASIN/0321125215/domainlanguag-20), rather than in components or services.
8. Remove commented code (`//deadFunction()`) and console log statements (`console.log('Debugging code')`) before pushing a commit
9. Run `ng lint`, `ng test` and `ng e2e` prior to pushing a final commit to a pull request.
10. [Inject services](https://angular.io/guide/dependency-injection) into model classes and components.
11. Properly scope services to components, feature modules (shared folder in feature), or app-wide (core folder).
12. Avoid referencing components in services, using strategy pattern where user input is needed
13. Write [unit tests](https://angular.io/guide/testing) in [Jasmine](https://jasmine.github.io/) to validate business logic in model classes, mocking services with [spies](https://jasmine.github.io/2.0/introduction.html#section-Spies) to stub dependencies
14. Unit test *presentation logic* in components
15. Create [temporary local git branches](http://jaimeiniesta.github.io/learn.github.com/p/branching.html) for feature sub-tasks, then [rebase](https://www.atlassian.com/git/tutorials/merging-vs-rebasing) them into your local feature branch and delete the temporary branch.
16. Before creating a final commit to a pull request, make sure to [pull and rebase](http://gitready.com/advanced/2009/02/11/pull-with-rebase.html) commits from the working branch of the upstream repository, resolving any conflicts that may occur.\*
17. Create a final commit by [squashing](http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html) previous commits in a pull request by using interactive rebase.\*

\* For a description of git commands used for rebasing and squashing, see this [gist](https://gist.github.com/tonysneed/42263e6577c30063d093aef2fc488e7a).
