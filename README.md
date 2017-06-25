# Angular Development Guidelines

*Proposed guidelines for developing Angular applications*

1. Study and apply the official [Angular Style Guide](https://angular.io/guide/styleguide).
2. Use the [Angular CLI](https://cli.angular.io/) to scaffold services, components, modules, etc.
    - See the [docs](https://cli.angular.io) and third party [reference guide](https://www.sitepoint.com/ultimate-angular-cli-reference)
3. Use the [TSLint](https://palantir.github.io/tslint) [VS Code extension](https://marketplace.visualstudio.com/items?itemName=eg2.tslint) / [SublimeText plugin](https://github.com/lavrton/SublimeLinter-contrib-tslint) to vet your TypeScript code in real-time
4. Use the [Angular Language Service](https://github.com/angular/angular/tree/master/packages/language-service) [extension](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template) / [SublimeText plugin](http://brianflove.com/2017/04/11/angular-language-service/) for your code editor to check for template errors in real time
5. Avoid using `any` unless absolutely necessary, using classes and interfaces for greater compile-time type safety
6. Use object-oriented features of TypeScript / ES 2015+, in order to implement design patterns in a type-safe manner
7. Place logic in model classes, rather than in components or services.
8. Remove commented code and console log statements from code before pushing a commit
9. Run `ng lint`, `ng test` and `ng e2e` prior to pushing a final commit to a pull request.
10. Inject services into model classes
11. Properly scope services to components, feature modules (shared folder), or app-wide (shared folder)
12. Avoid referencing components in services, using strategy pattern where user input is needed
13. Unit test the business logic in model classes, mocking services
14. Unit test presentation logic in components
15. Create temporary local branches for feature sub-tasks, then rebase them into your local feature branch and delete the temporary branch.
16. Before creating a final commit to a pull request, make sure to pull and rebase upstream commits from develop/staging, resolving any conflicts that may occur.\*
17. Create a final commit by squashing previous commits in a pull request by using interactive rebase.\*

\* For a description of git commands used for rebasing and squashing, see this [gist](https://gist.github.com/tonysneed/42263e6577c30063d093aef2fc488e7a).
