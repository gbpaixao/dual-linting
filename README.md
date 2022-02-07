# dual-linting
This is POC shows that it's possible to have only one code style on server-side and each developer could have their own code style simultaneously.

## How?
There are two eslint configuration files: 
  
  1. One on the root of the project - the server code style;
  2. Another one on ./src - each devs code style.

While coding, each developer can override the second configuration file, so it be the way they want during development. But when the developer wants to commit their changes, the server code style should be applied instead of their own. This is possible by using ESLint's scripts.

    eslint ./src --ext .js --ext .ts --fix -c ./.eslintrc.json --no-eslintrc

Where .src is the path you want to lint, --ext is the extensions you want to lint, -c is the configuration file you want to use, and --no-eslintrc says no other configuration file should be used.

> **_Note:_** The dev configuration file should be on .gitignore, so that it doesn't override the others configurations.


## Husky and lint-staged

By using Git Hooks with the lib Husky, you can call a script on package.json. So before committing the changes, the code will always be linted using the server's configuration file.

Lint-staged is reponsible for re-adding the files which were changed by the linting process.