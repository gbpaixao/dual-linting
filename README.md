# dual-linting
This is POC shows that it's possible to have only one code style on server-side and each developer could have their own code style simultaneously.

## How?
There are two eslint configuration files: (1) one on the root of the project - the server code style, (2) another one on ./src - each devs code style.

(1) By using Git Hooks (Husky and Lint-staged), before committing the code will always be linted using this eslint configuration.
(2) is on .gitignore, so that no dev overrides the others configurations.
