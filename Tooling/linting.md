# Linting and formatting

1. Eslint: https://khalilstemmler.com/blogs/typescript/eslint-for-typescript/
Eslint is the typical linter used to catch any code styling issues before they
make it into the code base.
- Configured by a eslint config file with various naming conventions
- The file specifies what rules you to use for linting, typically a dev team
will just use an existing companies established linting config based on 
preferences. Eg. shopify
- Typically, most modern editors will pick this file up and automatically show
errors and warnings within the editor in realtime as developers code
- Typical workflow, in `package.json`, a script for linting `eslint .` and for
fixing errors `eslint . --fix`. Fix is able to automatically fix some linting
errors in some cases.
- This would also automatically run in the CI when PR's are created
- And could even be configured to run in a precommit hook (maybe using husky).
This would mean dev's automatically lint before commiting.

## Custom rules:
https://eslint.org/docs/latest/extend/custom-rule-tutorial#why-create-a-custom-rule
It is possible and sometimes can be beneficial to be able to write your own custom
linting rules. As the tutorial here says, you should try to find an existing plugin
that already does what you need before by searching online as many plugins already 
exist.

## Extra resources
https://github.com/dustinspecker/awesome-eslint

2. Prettier: https://khalilstemmler.com/blogs/tooling/prettier/
Prettier is a formatter. This is for formatting code rather than linting which
shows errors/warnings but also can be fixed. The formatter can also be configured
to use the eslint config.
- it enforces rules like max line width and spacing
- advantage is that it can be configured to run on save in editors. eg. vscode
extension or similar plugin in neovim
