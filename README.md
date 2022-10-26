# ngx-boilerplate

*An [opinionated](OPINIONS.md) boilerplate for Angular applications.*

## Versioning

The version number of this project will always match the major version of the Angular used in it. The minor and build numbers may not match, and are incremented when I make other changes to the boilerplate.

## Installation

Out of the box, there are no Angular environment files. They are auto-generated by the `setenv.ts` script (see `package.json`) and should not be edited or committed to the repository.

### Environment files

Before running the application, you'll need to create a `projects/browser/src/environments/.env` file containing any properties that should appear in your `environmnet.ts` file. Keys in **MACRO_CASE** will be automatically converted to **camelCase**.

```shell
BASE_URL=http://localhost:4200
APP_TITLE=My Awesome App
```

Will become:

```typescript
export const environment = {
	"baseUrl": "http://localhost:4200",
	"appTitle": "My Awesome App"
};
```

Your `.env` file should not be committed to the repository, since it may contain API keys and other private information. Please keep the `.env.example` file up-to-date with all the keys that need to exist for the application to run.

The npm commands for building and compiling the application include the command to generate the environment files, but you can also create them manually with `npm run config:dev` and `npm run config:prod`.

### Dependencies

You can use either `npm ci` to install dependencies that are locked to the versions in `package-lock.json`, or `npm install` to install the latest compatible versions from `package.json` (which may update `package-lock.json`).

## Linting and fixing

To lint everything, run `npm run lint`. This covers your Angular project files, SCSS, and HTML.

To have Prettier fix formatting, run `npm run prettier`.

## Documentation

Documentation is created with CompoDoc using `npm run doc:browser:build`. You can run a dedicated documentation server with `npm run doc:serve` and visit <http://localhost:8080/> to view it.

## Development server

Run `npm run start` for a dev server. Navigate to <http://localhost:4200/>. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

The schematics will currently create TypeScript files with spaces for indentation instead of tabs, and without trailing commas. Please run Prettier before committing the new or modified files.

## Build

Run `npm run build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `npn run test` to execute the unit tests via [Karma](https://karma-runner.github.io). Run `npm run test:coverage` to create an updated coverage report that can be display in the generated documentation (you'll need to build the documentation in order to see the changes).

## Continuous integration

Since the environment can't be built without a `.env` file in the environment folder, the workflow simply copies `.env.example` to `projects/browser/src/environments/.env` to allow the build process to succeed. If your tests rely on specific environment values, you'll need to create repository secrets through GitHub that contains those values (which keeps things like API keys out of the repository itself), *or* put default values into the `.env.example` file, with the understanding that those values will become part of the repository once you commit that change.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
